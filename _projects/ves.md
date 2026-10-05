---
layout: project
title: Veterans Health Administration Enrollment System
who: U.S. Department of Veterans Affairs 
link:
role: Manager of Design
image: /assets/images/projects/project-ves.png
summary: Modernize the VHA Enrollment system, a staff-facing application used to manage Veteran enrollment in and determining the eligibility for health care benefits. 
responsibilities:
  - user experience design 
  - design strategy
  - user journeys 
  - persona creation 
  - research strategy 
  - sprint planning 
  - delivery alignment 
startYear: 2023
endYear: 2025
scope: Enterprise System Modernization
impacts: 
  - Modernized the primary healthcare system for over 9 Million Veterans. Replaced a non-linear 1990s legacy system with guided registration workflows, automated external data checks to prevent duplicate records, and established reusable design patterns.
featured: true
builtWith: 
- Figma
- Mural 
- Confluence 
- Jira
takeaway: In large-scale civic tech, solving UI problems requires equal parts system mapping, technical coordination, and stakeholder trust. By combining deep user research with structured cross-vendor collaboration, complex federal systems can be modernized without disrupting critical public services.
---

## Context & the challenge 
Bringing clarity to complexity
{: .lead}

### Background 
The VHA Enrollment System supports over 9 million Veterans across the largest integrated healthcare system in the United States. The underlying system relied on legacy software architecture dating back to the 1990s.

### Challenge
Enrolling in VA benefits involves interconnected rules across eligibility, service history, income limits, and priority group calculations. The legacy platform offered no guided workflows or task-based structure. VA staff were confronted with "walls of text" and dense forms. VA processors had to navigate across multiple screens based on memory or internal training docs to complete a single registration, resulting in manual data entry errors, accidental creation of duplicate records, and high administrative burden.

### Stakeholder alignment
As {{ page.role }}, I established the UI/UX roadmap and product strategy in close coordination with VA business stakeholders, technical SMEs, and product owners. I structured alignment sessions to balance federal eligibility policies, legacy services and systems, and VA needs.

## Research & discovery
Grounding the team in VA staff realities
{: .lead}

### In-person contextual inquiry
Led in-person observational site visits to VA facilities. Watched staff process enrollment applications live, uncovering workaround behaviors like opening saved emails or toggling between external tabs to complete routine tasks.

#### Key findings

- **Search & duplication:** Staff searched for Veterans using limited parameters; if a record wasn't found immediately, they created a new one, leading to duplicate records.
- **Lack of system guidance:** Staff had to mentally calculate priority group eligibility based on disparate factors rather than the system guiding the evaluation.
- **Manual data processing:** Information like income verification was manually cross-checked with external systems like VFMP (Veteran and Family Member Program).

### Centralized research
Established a centralized research repository to document findings, insights, and decision histories. This provided a single source of truth that bridged knowledge gaps between design, PMs, and engineering teams.


## Design & execution
Architecting guided workflows with modern system design
{: .lead}

### Complex workflow and system diagramming
Mapped multi-layered decision trees to visualize how priority groups were calculated based on military experience, income, and service-connected status. Visualized high-level user flows for searching, record creation, and final registration.

### Guided registration experience
Redesigned the registration interface into a linear, step-by-step guided workflow. Replaced fragmented legacy screens with clear hierarchy, distinct page sections, and persistent global application chrome (including a top record bar and intuitive side navigation).

### Preventing errors at the UI layer
Introduced proactive record cross-checking into the search flow. If a Veteran isn't found immediately, the system runs automated backend verification before allowing new record creation, preventing duplicate entry errors at the source.

### Design and engineering collaboration
Built interactive, clickable Figma prototypes to align front-end/back-end engineers and business stakeholders on complex interaction states. Documented reusable UI design patterns to ensure consistency across micro interactions and streamline development sprints.

## Leadership & Process
Bridging subcontractor, prime, and federal stakeholders
{: .lead}

### Multi-tier team leadership
Managed the UI/UX discipline across designers, researchers, and business analysts working within a multi-vendor structure. Our team was the subcontractor design team operating alongside a prime front-end engineering team and VA business/technical leads.

### Design quality 
Established design critique sessions and peer review processes to maintain high  quality across all workflows, while mentoring junior designers and researchers.

### Cross-functional collaboration
Served as the primary bridge between UI/UX and engineering teams, translating user research and accessibility requirements into technical user stories. Led stakeholder presentations to demo progress and align priorities with leadership.

## Outcomes

### Streamlined record creation
Transformed a fragmented legacy experience into an intuitive, guided workflow that speeds up processing time and reduces staff cognitive load. Created a record creation workflow that limited duplicate record creation. 

### Automated system integrations
Directly integrated income verification and external system data flows (e.g., VFMP), eliminating manual cross-checking and human error in eligibility determinations.

### System agility & scalability
Partnered with engineering to align UI patterns with a modern microservices architecture, laying a foundation for future feature releases and system integrations.