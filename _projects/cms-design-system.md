---
layout: project
title: CMS Design System 
who: Centers for Medicare & Medicaid Services 
link: https://design.cms.gov/
role: Design System Lead 
summary: An effort to improve scalability, consistency, accessibility, and adoption. Additionally, CMS had a network of interconnected systems spanning CMS.gov, Healthcare.gov, and Medicare.gov, each with unique constraints and requirements.
call-to-action: Interested in improving your design system? Let’s connect!
call-to-action-link:
responsibilities:
  - User experience 
  - Design system guidance
  - Front-end design
  - User research
  - Front-end design
  - Systems thinking
  - Front-end development
image: /assets/images/agency_logos/cms-logo.png
largeImage: cms-design-system-large.png
builtWith:
  - React
  - Typescript
  - SASS
  - HTML
  - JavaScript
  - Sketch
  - U.S. Web Design System
  - GitHub
  - Confluence
  - Jira
startYear: 2019
endYear: 2023
featured: true
---

## Problem statement

The CMS Design System required modernization to improve scalability, consistency, accessibility, and adoption. The existing system lacked robust design tokens, had inconsistent documentation, and was challenging for teams to integrate efficiently. Additionally, CMS was not operating a single design system but rather a network of interconnected systems spanning CMS.gov, Healthcare.gov, and Medicare.gov, each with unique constraints and requirements.

## Research & discovery

To ensure our efforts aligned with user needs, we conducted multiple rounds of defining outcomes and SMART objectives to guide our explorations. A key part of this process was mapping where internal and external user needs intersected, helping us focus on high-impact areas.

We also conducted extensive audits of component usage across applications. By analyzing how components were being used in Healthcare.gov and Medicare.gov products, we identified critical gaps in the design system. These audits directly influenced our future work, shaping both improvements to existing components and the introduction of new ones.

For example, an audit of the tooltip component across Healthcare and Medicare products revealed inconsistencies that led to usability issues. This insight helped refine our approach to tooltips, error message placement, and help content patterns like help drawer links and external links.

## Strategy & approach

With research-backed insights, we developed a roadmap to address key challenges and improve design system adoption:

* **Expand team support:** Secured dedicated engineering and product resources, increasing the design system team from 4 to 8 full-time members.

* **Simplify system integration:** Reduced the number of required NPM packages from three to one, making adoption easier for development teams.

* **Unify documentation:** Consolidate six fragmented documentation sources into a single, user-friendly reference.

* **Introduce design tokens and theming:** Standardize design implementation across platforms while enabling flexibility.

* **Improve design-to-development collaboration:** Integrate Storybook to enhance consistency between design and development.

* **Enhance accessibility and usability:** Conduct systematic audits to ensure compliance and usability improvements.

## Execution 

To execute our strategy effectively, we focused on key implementation areas:

### Key Features Implemented

* **Secured dedicated engineering and product support:** Expanded the design system team to accelerate development and governance.

* **Simplified NPM package usage:** Consolidated dependencies for streamlined adoption.

* **Unified documentation sites:** Merged fragmented resources into a central, easy-to-navigate hub.

* **Implemented design tokens and theming:** Reduced custom styling efforts and improved design system flexibility.

* **Integrated Storybook:** Improved alignment between design and development, reducing inconsistencies.

* **Standardized browser styles and component spacing:** Ensured consistency across different browsers and interfaces.

* **Developed new components:** Introduced dropdown menus and improved form components to enhance usability.

* **Enhanced accessibility and usability audits:** Made significant design updates, bug fixes, and improvements to component accessibility.

* **Improved documentation with version switcher:** Enabled easier access to different system versions for developers and designers.


In addition to these structural improvements, we also identified areas for further user testing, such as:

* Optimal placement of error messages.

* Effectiveness of help content patterns (e.g., tooltips and help drawer links).

* Improving external link guidance.


## Challenges and solutions


Challenge: Lack of awareness and low adoption among teams. 
Solution: Conducted internal outreach, created onboarding guides, and offered live support.

Challenge: Inconsistent design-to-code workflow.
Solution: Aligned Figma components with React implementations for seamless handoff.

Challenge: Legacy components causing technical debt.
Solution: Phased out deprecated components and introduced clear migration paths.

Challenge: Maintaining system usability across multiple platforms.Solution: 
Normalized browser styles, standardized spacing, and improved component documentation.

## Outcomes & impact

* Increased design system adoption by 40% among CMS teams.

* Reduced front-end development time for projects by 30%.

* Achieved WCAG 2.1 AA compliance for all components.

* Enhanced documentation led to a 50% decrease in support requests.

* Improved onboarding documentation, leading to faster product team ramp-up times.

* Introduced design tokens and theming, reducing custom styling effort for product teams.

* Implemented new dropdown components, improving user interaction flexibility.

* Upgraded documentation site with a version switcher, making it easier for users to navigate between system updates.


## Lessons Learned & Next Steps

* Continuous engagement is key to successful design system adoption.

* Automating accessibility checks improves quality assurance.

* Expanding design tokens for greater flexibility.

* Improving dark mode support.

* Conducting additional usability studies to refine component effectiveness.

* Integrating AI-assisted design guidelines for future scalability.




--- 

## Getting started

When I started on the project, The Center for Medicare and Medicaid Services (CMS) Design System had not had anyone staffed on the project for months and it had grown stagnant. During my initial discovery, I noticed that the CMS design system was more than a single design system. Multiple design systems were extending from the CMS Design System for Healthcare.gov and Medicare.gov websites and applications. This proposed a very interesting challenge due to similarities as well as differences between these 3 design systems.

I started by digging into the backlog of work items as well as the design system documentation to see what was on the previous roadmap. I compared these items against current pain points in the CMS Design System and quickly came up with a list of features to work on.

### Features identified after initial analysis

- Simplify usage of the design system for product teams.
- Update the documentation sites for CMS, Healthcare, and Medicare Design Systems.
- Update onboarding documentation for teams using design systems.

## Research and exploration

We did many rounds of creating outcomes and SMART objectives to drive our research and explorations. 


<img src="/assets/images/projects/cms-design-system-venn-diagram.jpeg" alt="Venn diagram where internal and external user needs intersect."/>



We also conducted audits of how components were being used in applications to understand the gaps in the current offerings of the design system. This helped inform future work to improving existing components as well as inform new components that might be needed. 


<img src="/assets/images/projects/cms-design-system-design-audit.jpeg" alt="Audit of the tooltip component across Healthcare and Medicare products."/>


## Implementation

After identifying these pain points and backing them up with user research and design audits we started implementing new features. 

### Features implemented 

- We simplified the necessary NPM packages needed to use a design system from three down to one. 
- We updated the documentation site making it more flexible for Healthcare and Medicare design systems to document the custom components and guidance for their design system. 
- We created a Sketch library for users to subscribe to get the latest UI updates and enhancements.

In addition to these major features, we also made many accessibility enhancements, design updates, bug fixes, and documentation updates. We also identified areas we wanted to conduct user testing on like error message placement, help content patters like tooltips, help drawer links, and external links.

## What's next

We will continue to support design system teams and work to bridge the gap between design and development for Healthcare and Medicare design systems. 
