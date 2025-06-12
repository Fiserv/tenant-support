# Governance Model for Contributing Teams

## Context
In addition to the core development activities carried out by the Developer Studio Team, this document outlines the process governance model for other teams involved in feature development, enhancements, fixes, and support for 'Workspaces'. It serves as a comprehensive guide to ensure that all contributors adhere to the established onboarding and operational procedures, facilitating a smooth integration and collaboration across teams.

## Overall Process
The overall software development process in Developer Studio is described here: [SDLC and Development Process](https://enterprise-confluence.onefiserv.net/display/TOS/SDLC+and+Development+Process)

## SDLC Methodology
The software development lifecycle and methodology that’s used is Agile development.
The main development follows Scrum with 2-week sprints, with the respective setup in JIRA.
Certain specialized work streams follow Kanban, either by using Kanban board in JIRA, or Kanban within the Scrum sprints with some more flexibility.

In case of multiple development teams, in general they follow Scaled Agile Framework / SAFe, even in its simplest implementation, using the same sprint schedule for all teams within the project.

Related resources:

[Definition of Ready (DoR)](https://enterprise-confluence.onefiserv.net/pages/viewpage.action?pageId=463011104)

[Definition of Done (DoD)](https://enterprise-confluence.onefiserv.net/pages/viewpage.action?pageId=463011017)

## Coordination at Certain Milestones

This section outlines key coordination points throughout the development process. While many of these are also mentioned in the meetings section, they generally include:

- **Feature Kick-off**: 
  - Engage with Tenant Advocate - Tania- tania.sarkar@fiserv.com to set initial context.
  - Discuss overall feasibility, approach, high-level scope (larger enhancement vs smaller enhancement), intended timeline, etc.

- **PRD Reviews**:  
  - **Larger Enhancements**: 
    - Create the Product Requirements Document (PRD) using the [Sample PRD Template](https://fiservcorp.sharepoint.com/:w:/r/sites/tos-launchpoint/_layouts/15/Doc.aspx?sourcedoc=%7BD1CBDD32-0D38-451E-9310-C93360CD1B9F%7D&file=PRD-template-tenants.docx&action=default&mobileredirect=true) for the feature within your designated [Product folder](https://fiservcorp.sharepoint.com/sites/tos-launchpoint/Shared%20Documents/Forms/AllItems.aspx?id=%2Fsites%2Ftos%2Dlaunchpoint%2FShared%20Documents%2FProjects%2FDeveloper%20Studio%20%2D%20Business%20Requirements&viewid=c1d95fea%2D1d1a%2D4aa5%2D975e%2D369a2c0b247f&ovuser=11873a1f%2D4c8d%2D450d%2D8dfb%2De37a2e2557f8%2Ctania%2Esarkar%40Fiserv%2Ecom&OR=Teams%2DHL&CT=1746203110997&clickparams=eyJBcHNOYW1lIjoiVGVhbXMtRGVza3RvcCIsIkFwcFZlcnNpb24iOiI1MC8yNTAzMTMyMTAxOCIsIkhhc0ZlZGVyYXRlZFVzZXIiOmZhbHNlfQ%3D%3D). 
    - If you cannot find a folder for your product, feel free to create a new folder or reach out to the Tenant Advocate for assistance. 
    - Notify the Tenant Advocate once a PRD has been added or updated.
    - The PRD finally needs to get reviewed by the official stakeholders (as listed in the PRD)

  - **Smaller Enhancements**: 
    - Open a [GitHub Issue ticket](https://github.com/Fiserv/Support/issues) as illustrated below:

    ![GitHub Issue ticket](assets/images/github/github_issue_ticket.png "GitHub Issue ticket")

    - If you do not have access, please create a GitHub user account using your Fiserv email address and share the details with the Tenant Advocate.
    - If required, the Tenant Advocate or a member of the Developer Studio Team will reach out for further clarification, either through GitHub comments or by scheduling a one-on-one call.

- **ADR Reviews**: 
  - For any feature release on Developer Studio, it is mandatory to create [Architectural Decision Record(ADR)](https://enterprise-confluence.onefiserv.net/display/TOS/ADR-AAAAA-NN%3A+Dev+Studio+ADR+Template) which would be reviewed by the designated Architect of the Developer Studio Team. 
  - Add your new ADR in [Draft ADRs Backlog](https://enterprise-confluence.onefiserv.net/display/TOS/ADRs%3A+Draft) section.
  - The Tenant Advocate & the Developer Studio Architect will reach out for further clarification & review, by scheduling a one-on-one call.
  - If you do not have access to Confluence, please reach out to Supriya - supriya.nirmale@Fiserv.com 

- **UX Design Reviews**: 
  - Depending on the nature of the requirement, there may or may not be a UX design change.
  - If any design changes are identified during the review process, the Developer Studio team will involve the UX team for further engagement.
  - See the info in the meetings section, and plan accordingly ahead of time, as that team is shared across multiple applications.

- **Test Plan Review**: 
  - Consult the [QA Hand Off](https://enterprise-confluence.onefiserv.net/display/TOS/QA+Hand+Off) document and review the information in the meetings section.

- **Development and QA Touch-points**: 
  - Coordinate as needed, depending on the complexity of the feature and whether discussions are required on specific topics.

- **Code Reviews**: 
  - Submit Merge Requests (MRs) and coordinate with the Developer Studio team for merging.
  - Refer [Code Review Process](https://enterprise-confluence.onefiserv.net/display/TOS/Code+Review+Process)
  - Refer [Developer Studio Point of Contacts](https://enterprise-confluence.onefiserv.net/display/TOS/Developer+Studio+-+Point-of-Contact+for+Contributing+Teams)

- **Testing on Different Environments**: 
  - As features progress through environments (Dev → QA → Stage → Prod), ensure thorough testing.
  - Utilize test automation where applicable.

- **Bug Fixes for Developed Features**: 
  - Address any issues with introduced changes and follow the standard code review and QA processes.

- **Hotfixes**: 
  - Would require a mandatory approval from Developer Studio's product owner for any HotFixes.
  - Submit merge requests to the **previous branch** for hotfixes, tracked in sub-pages of [Production Releases](https://enterprise-confluence.onefiserv.net/display/TOS/Production+Releases).
  - Ensure hotfixes are also merged into the **develop branch**, with respective testing in the Dev environment.
  - Check for **other branches** to merge into, preventing overwriting of hotfixes by subsequent sprint code. Let's say **sprint S15 hotfixes** that are overwritten by **sprint S16** code that's missing those hotfixes.
  - The DevOps team will handle deployments to the respective environments for hotfixes.
  - Code reviews and testing apply similarly for hotfixes.
  
- Fixes to production are typically scheduled for the next sprints in the develop branch, or if needed sooner in one of the upcoming releases of recent sprints that are already in the QA or Stage environment.
   - **Prod hotfixes off-release** outside of scheduled release deployments are avoided, only in case of high severity or impact, **after confirming with the Developer Studio team**.

- **Support**: 
  - Coordinate with the Developer Studio team for support coverage.
  - Troubleshoot incidents related to owned features and provide support for tenant requests.

## Common Meetings to Attend

There is no need to attend Developer Studio daily scrums, as teams usually have their separate scrum calls. Given that, the meetings to attend are minimized and generally include the following:

- **(Preferred)**: Kick-off meetings with tenant advocate per feature to set initial context and discuss overall feasibility, approach, high-level scope, intended timeline, etc.
- **(Required)**: PRD Reviews (Product Requirements Document): The Tenant Advocate will schedule meetings as needed. A heads-up regarding higher priority issues, such as critical client impact, would be greatly appreciated, as it will help us manage the Tenant roadmap more effectively.
- **(Required)**: ADR Reviews (Architecture Decision Record): The Tenant Advocate along with a designated architect will schedule a meeting to review/discuss the ADR for your feature as needed.
- **(Conditional)**: UX Design Handover and Review: In case of UI changes, once the overall approach is confirmed with PRD and ADR, there is a handover for the UX Design team, generally with a **3-sprint delivery time** for UX design / Figma mockups.        
   - *Please plan the timeline in advance accordingly, as this is a shared team across multiple applications*.
- **(Optional)**: Development touch-points: Schedule only if needed, if there are any implementation details to discuss and review. Submit merge requests (MRs) with code changes for review to Developer Studio repository owners.
- **(Optional)**: QA touch-points: Schedule only if needed, if there are any testing details to discuss and review. Join the QA Team meeting (weekly) if you need a test plan review by the team. Submit merge requests (MRs) with test automation code changes for review to Developer Studio QA repository owners. Reach out to Parth - parth.patel@fiserv.com  to get a meeeting invite.
- **(Required)**: Sprint technical showcases: Present the developed stories at the sprint end demos. Reach out to Parth - parth.patel@fiserv.com  to get a meeeting invite.
- **(Required)**: Prod Go/No-Go, Prod Deployment: When certain features with more impact are slated for release. 
   - Refer this [Sprint schedule](https://fiservcorp-my.sharepoint.com/:x:/r/personal/alvin_cho_fiserv_com/_layouts/15/doc2.aspx?sourcedoc=%7B6e5308ee-83fa-43f5-a940-b30ee962c144%7D&action=edit&wdenableroaming=1&wdodb=1&wdlcid=en-US&wdorigin=Other&wdredirectionreason=Force_SingleStepBoot&wdinitialsession=dc5e3479-4a87-b170-7345-c22bb186decf&wdrldsc=2&wdrldc=1&wdrldr=RefreshingExpiredAccessToken&ovuser=11873a1f-4c8d-450d-8dfb-e37a2e2557f8%2Ctania.sarkar%40Fiserv.com&clickparams=eyJBcHBOYW1lIjoiVGVhbXMtRGVza3RvcCIsIkFwcFZlcnNpb24iOiI1MC8yNTA1MTgwMDIxNCIsIkhhc0ZlZGVyYXRlZFVzZXIiOmZhbHNlfQ%3D%3D) and reach out to Parth - parth.patel@fiserv.com to get a meeeting invite.
- **(Required)**: When an issue is reported regarding a developed feature, the Development Team is expected to provide [on-call support](https://enterprise-confluence.onefiserv.net/pages/viewpage.action?pageId=463011106).


Refer:
  - [Tenant Onboarding Model](?path=docs/tenant-info/tenant-onboarding-model.md)
