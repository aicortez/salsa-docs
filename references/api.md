# API Reference — Salsa as a Service v2.0

Use this file when answering questions about the API, webhooks, or SDK usage.

## Base URL
```
https://api.salsaasaservice.com/v2
```
v1.0 API is deprecated and will be shut down December 31, 2025.

## Authentication
All requests require a Bearer token:
```
Authorization: Bearer YOUR_API_KEY
```
Enterprise customers can also use OAuth 2.0 and SAML 2.0.

---

## Key Endpoints

### Get demand forecast (REST)
```bash
curl -X GET https://api.salsaasaservice.com/v2/forecast \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json"
```

### Create a production batch (REST)
```bash
curl -X POST https://api.salsaasaservice.com/v2/production/batches \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{"recipe_id": "rec_456", "quantity": 5.0}'
```

### Get AI inventory predictions (JS SDK)
```javascript
const predictions = await salsa.ai.inventory.predict({
  location: "kitchen_1",
  horizon_days: 7
});
console.log(`Predicted reorder date: ${predictions.reorder_date}`);
```

### Enable auto-ordering (JS SDK)
```javascript
const autoOrder = await salsa.ai.inventory.enableAutoOrder({
  location: "kitchen_1",
  max_order_value: 5000,
  approval_required_over: 1000,
  preferred_suppliers: ["sysco", "us_foods"]
});
```

### Get AI quality prediction (JS SDK)
```javascript
const prediction = await salsa.ai.quality.predict({
  batch_id: "BATCH-2024-001",
  current_stage: "mixing"
});
console.log(`Predicted quality: ${prediction.score}/10`);
console.log(`Confidence: ${prediction.confidence}%`);
```

### Configure quality monitoring (JS SDK)
```javascript
const qualityConfig = {
  enabled: true,
  monitoring_interval: "5m",
  thresholds: {
    temperature: { min: 35, max: 40, unit: "F" },
    freshness_score: { min: 8.0, max: 10.0 },
    consistency: { min: 7.5 }
  },
  alert_channels: ["email", "sms", "push", "slack"],
  auto_action: {
    low_quality_detected: "pause_production",
    temperature_violation: "notify_manager"
  }
};
```

### Query IoT sensor data (JS SDK)
```javascript
const sensors = await salsa.iot.getSensors({ location: "kitchen_1" });
sensors.forEach(sensor => {
  const reading = sensor.getLatestReading();
  console.log(`${sensor.name}: ${reading.value} ${reading.unit}`);
  if (reading.isAnomaly()) {
    console.log(`Alert: ${reading.anomalyDetails}`);
  }
});
```

---

## GraphQL API

### Demand forecast query
```graphql
query GetProductionForecast {
  forecast(location: "loc_123", days: 7) {
    date
    recipes {
      id
      name
      predictedDemand {
        quantity
        unit
        confidence
      }
    }
  }
}
```

### Real-time quality alert subscription
```graphql
subscription OnQualityAlert {
  qualityAlert(location: "loc_123") {
    id
    severity
    sensorId
    message
    timestamp
  }
}
```

### Paginated production history
```graphql
query GetProductionHistory($first: Int = 50, $after: String) {
  productionBatches(first: $first, after: $after) {
    edges {
      node { id recipeId quantity }
      cursor
    }
    pageInfo {
      hasNextPage
      endCursor
    }
  }
}
```

---

## Webhooks v2

### Sample quality alert payload
```json
{
  "event": "quality.alert.created",
  "timestamp": "2024-01-15T10:30:00Z",
  "data": {
    "alert_id": "alert_789",
    "location_id": "loc_123",
    "severity": "high",
    "message": "Temperature out of range",
    "sensor_id": "temp_001",
    "reading": {
      "value": 45.3,
      "threshold": 40.0
    }
  },
  "signature": "sha256=abc123..."
}
```

Webhooks include SHA-256 signature verification. Features: guaranteed delivery, retry logic, event filtering, payload transformation, delivery status tracking.

---

## ERP Integration (JS SDK)
```javascript
import { SalsaClient } from 'salsa_sdk';
const client = new SalsaClient({ apiKey: 'your_api_key' });

const erpConnection = await client.integrations.connectErp({
  system: 'sap',
  credentials: {
    host: 'erp.yourcompany.com',
    client: '100',
    username: 'SALSA_INT',
    auth_type: 'oauth'
  },
  sync_options: {
    inventory: true,
    procurement: true,
    cost_accounting: true,
    frequency: 'real-time'
  }
});
```

---

## Performance Tips
- Use field-level caching with `@cache(ttl: 300)` on GraphQL queries
- Paginate large datasets using cursor-based pagination
- Use the SDK's built-in caching for repeated queries
- Prefer GraphQL subscriptions over polling for real-time data
