# Mintlify Technical Support Specialist Take-Home Assessment

Welcome to the Technical Support Specialist take-home assessment! This exercise simulates real-world scenarios you'll encounter when helping customers optimize their documentation structure and user experience.

## Scenario

You're working with a developer tools company that has grown rapidly. They started with a basic documentation site but now need to evolve their structure to better serve their expanding user base. The company has:

- **Created a v2 of their API** with new advanced features
- **Expanded internationally** and needs French language support

Your task is to redesign the documentation navigation structure to create an intuitive, scalable user experience.

---

## Task 1: Navigation Structure & Information Architecture

**Primary Goal**: Refactor the navigation structure in `docs.json` to provide the best possible user experience while ensuring all content remains accessible.

**What you're working with**:
- `v1/` - Original English documentation
- `v2/` - Updated English documentation with new features
- `fr/` - French translations of both v1 and v2 content

**Requirements**:
1. All English and French v1 and v2 pages must be available through the navigation.
2. Navigation must be intuitive for different users.
3. Structure should be scalable for future growth. 

### What We're Looking For

**Product Thinking**:
- How do you organize information for different user journeys?
- What navigation patterns make sense for technical documentation?
- How do you handle version differences and language switching?

**Technical Implementation**:
- Proper use of Mintlify's navigation features
- Clean, maintainable JSON structure
- Understanding of internationalization best practices

**Problem-Solving Approach**:
- How do you research and apply Mintlify's documentation?
- What trade-offs do you consider when making UX decisions?
- How do you communicate your reasoning?

### Task 1 Deliverables

1. **Updated `docs.json`** with your new navigation structure
2. **Brief explanation** (in a separate MDX file added to the sidebar) of:
   - Your decision-making process
   - Key user experience improvements
   - Any trade-offs you considered
   - How your structure scales for future growth

---

## Task 2: Component Enhancement & Content Formatting

Now that you've mastered the navigation structure, it's time to enhance the content itself!

**The Challenge**: The current documentation uses basic vanilla MDX, but Mintlify offers a rich component library that can dramatically improve user experience and content presentation.

**Your Mission**: Refactor the **v2 files** (both English and French) to showcase effective use of Mintlify's component ecosystem.

### Requirements

1. Focus on **v2 files only** (mainly English version)
2. Use at least **3-4 different Mintlify components** appropriately
3. Maintain content meaning while improving presentation
4. Show understanding of when and why to use specific components

### Component Categories to Explore

**Content Organization**:
- Tabs, Accordions, Card Groups
- Code Groups for multi-language examples
- Callouts and Info boxes

**Visual Enhancement**:
- Custom styling with HTML/CSS
- Icons and visual hierarchy
- Responsive layouts

### Creative Freedom

- **Use HTML/CSS** if you want to create custom styling
- **Mix and match** components to create unique layouts

### What We're Evaluating

**Component Selection**:
- Do you choose components that enhance the content's purpose?
- Are components used appropriately for their intended function?

**User Experience Thinking**:
- Does the enhanced formatting improve readability and navigation?
- Do you consider different users and their needs?

**Technical Execution**:
- Proper component syntax and implementation
- Clean, maintainable code structure
- Effective use of component features

**Product Knowledge**:
- Understanding of Mintlify's component ecosystem
- Creative application of available tools
- Knowledge of best practices

### Examples of Great Component Usage

- **Code Groups** for showing API calls in multiple programming languages
- **Callouts** to highlight important warnings or tips
- **Tabs** to organize related but distinct information
- **Cards** to create scannable feature overviews
- **Custom HTML/CSS** to create unique branded experiences

### Task 2 Deliverables

1. **Enhanced v2 MDX files** with improved component usage
2. **Brief explanation** of your component choices:
   - Why you chose specific components for specific content
   - How your enhancements improve the user experience
   - Any custom styling decisions and their rationale

---

## Task 3: Deployment & Documentation Hosting

**The Final Step**: Deploy your enhanced documentation to production so it's accessible to the world!

**Your Mission**: Set up a Git repository, connect it to Mintlify, and deploy your completed documentation site.

### Requirements

1. Create a Git repository for this project (if not already done)
2. Create a Mintlify account (if you don't already have one)
3. Link your repository to a Mintlify deployment
4. Verify that your deployed site works correctly with all navigation and components
5. Return the deployed URL to us

### Task 3 Deliverables

**Deployed documentation URL** - Share the live link to your deployed Mintlify site

---

## Resources

- [Mintlify Documentation](https://mintlify.com/docs) - Your primary resource; everything you need to succeed will be within these docs
- [Mintlify Components Catalog](https://www.mintlify.com/docs/components/accordions) - Explore available components

## Getting Started

1. **Explore the current structure** - Run `mintlify dev` to see the existing site
2. **Read through the content** - Understand what each page contains
3. **Research Mintlify features** - Check the docs for navigation options
4. **Plan your approach** - Sketch out your ideal user experience
5. **Implement your solution** - Update `docs.json` with your new structure
6. **Enhance content** - Add Mintlify components to v2 files
7. **Test thoroughly** - Ensure all pages are accessible and navigation flows well
8. **Deploy** - Push to Git, connect to Mintlify, and share your live URL

## Tips for Success

- **There's no single "right" answer** - we want to see your thought process
- **User experience first** - think about different end users using the docs
- **Be creative** - explore Mintlify's features to find elegant solutions
- **Document your thinking** - help us understand your approach
- **Test your navigation** - make sure it actually works well in practice
- **Quality over quantity** - thoughtful component usage beats using everything available

## Time Expectation

Plan for **2-3 hours** of focused work. Quality over speed - we'd rather see thoughtful decisions than a rushed implementation.

---

**Good luck!** We're excited to see how you approach this challenge and learn about your problem-solving process.