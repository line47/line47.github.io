---
layout: project
title: CMS Design System 
who: Centers for Medicare & Medicaid Services 
link: https://design.cms.gov/
role: Design System Lead 
summary: Improve scalability, consistency, accessibility, and adoption of three interconnected systems spanning CMS.gov, Healthcare.gov, and Medicare.gov.
call-to-action: Interested in improving your design system? Let’s connect!
call-to-action-link:
responsibilities:
  - user experience 
  - design system guidance
  - front-end design
  - user research
  - systems thinking
  - design tokens
image: /assets/images/projects/project-cmsds.png
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
scope: Enterprise Design System leadership & evolution
featured: true
impacts:
- Scaled the core system powering Healthcare.gov, Medicare.gov, and CMS.gov. Expanded the team from 1 to 8 cross-functional members, consolidated 14+ fragmented resources into a single source of truth (design.cms.gov), and built a multi-brand token system for component scaling.
takeaway: A design system is fundamentally about trust and communication. By treating the system as a product, simplifying dependencies, and supporting cross-functional teams through open governance, complex government platforms can scale sustainably.
---

## Context and the challenge
Evolving beyond siloed codebases and maintenance friction
{: .lead}

### Background
Built on the heels of the U.S. Web Design System (USWDS) in 2017, the CMS Design System (CMSDS) was established so teams building Healthcare.gov, Medicare.gov, and CMS.gov could deliver consistent, responsive, and accessible digital healthcare experiences. While sharing visual principles with USWDS, CMSDS was engineered as a standalone ecosystem of production-ready React and HTML components delivered directly via NPM and CDN.

### Challenge
Early implementations relied on separate "site packages" (later renamed "child design systems") for Healthcare.gov and Medicare.gov. Over time, this grew into a fragmented "landscape of 14+ bespoke resources"—spanning separate GitHub repos, InVision DSM kits, PDF style guides, and multiple documentation sites.

- **Duplicated maintenance:** Teams solved the exact same bugs and built the exact same components three times.
- **UI inconsistencies:** Foundational components like buttons diverged across sites in both visual appearance and CSS naming standards.
- **High cognitive overhead:** Product teams ran into friction whenever they needed to report a bug, propose new features, or locate canonical usage guidance.


### Stakeholder alignment
As {{page.role}} starting in 2019, I pitched CMS leadership on treating the design system as a true product rather than an administrative side project. I advocated for increasing team capacity—scaling our team from a single designer/developer to an 8-person cross-functional pod (designers, engineers, product owners, scrum master, and technical lead). This allowed us to shift from siloed child systems to a unified multi-brand token architecture.


## Research and discovery
Understanding product team needs and mapping workflow friction
{: .lead}

### Auditing the system landscape
Mapped out every touchpoint where designers and developers interacted with the design system, identifying gaps across documentation, design assets, and codebases.

### Stakeholder and contractor engagement

Conducted qualitative discovery sessions with CMS leadership and external contractor product teams.

### Community building and observational audits

- **Office hours and syncs:** Hosted regular open office hours and biweekly syncs with designers, developers, and accessibility specialists to build community and gather direct feedback.
- **Tooling audits:** Observed designers using Sketch and Figma kits to identify where workflow handoffs to engineering were breaking down.
- **Quantitative surveys:** Distributed user surveys across CMS product teams to benchmark system satisfaction, component gaps, and adoption blockers.

### Key insights
Product teams wanted to adopt the system, but the overhead of navigating multiple codebases and learning complex contribution processes prevented them from giving back. The system needed to meet teams where they were with a trusted, single source of truth.

## Design and execution
Architecting a scalable, multi-brand component engine
{: .lead}

### Multi-brand design tokens and systematized foundations
Re-architected core elements—including color ramps, spacing units, and typography scales—into design tokens. This allowed Medicare.gov and Healthcare.gov to inherit core component structure while injecting site-specific branding without duplicating code.

### Simplifying technical dependencies
Streamlined complex package dependencies from 4 down to 1 core NPM package. This eliminated version-matching headaches for product developers and made system upgrades predictable.

### Component maturity model
Introduced a clear Component Maturity Model framework directly within the documentation site. This gave product teams instant visibility into each component’s level of code maturity, integration status, and Section 508 / WCAG accessibility compliance.

### Standardized tooling and dual output
Built shared developer scripts across codebases for linting, testing, and automated site building. Maintained both HTML snippets and production-ready React components, ensuring both legacy web apps and modern React applications across CMS benefited from system updates.

## Leadership and process
Scaling team capabilities and establishing unified governance
{: .lead}

### Team building and capacity advocacy
Successfully grew the design system discipline across four distinct phases—expanding from 1 designer/developer to 2, then 4, then 6, and ultimately an 8-person team.

### Consolidating governance and tooling
Deprecated fragmented tools (such as legacy style guides) and established design.cms.gov alongside GitHub and Storybook as the central source of truth.

### Mentorship and systems thinking
Coached product designers and engineers on applying systems thinking. Mentored team members on accessibility best practices, component review workflows, and documentation writing.

## Outcomes

### Unified digital footprint
Replaced 14+ scattered resources with one consolidated, well-governed ecosystem powering Healthcare.gov, Medicare.gov, and CMS.gov.

### Eliminated triplicated work
Streamlined engineering efficiency by removing the need to solve bugs or write component code three separate times across child systems.

### Accelerated product delivery
Reduced developer setup friction and version-matching issues, enabling contractor teams to focus sprint time on complex healthcare applications rather than basic UI building blocks.