# Living PRD

> Module 4 · Production Specs. Refactor for readability; extract a living PRD that stays true as the build evolves.

## Problem

_What user problem does this solve? Tie to the validated hypothesis._

FakeCompany employees struggle to identify which workplace tools are available, approved, and appropriate for client work.

## Users & jobs

- **Primary user:** A FakeCompany employee who needs a software tool for design, writing, research, strategy, internal work, or client delivery.
- **Job to be done:** When I need a tool for internal or client work, help me quickly understand what is available, whether I am allowed to use it, what restrictions apply, and how to get access so I can make a confident decision without opening an unnecessary Help Desk ticket.

## Scope

- **In:** In

Catalog of available and known tools
Search by tool, task, description, category, or status
Browsing by use case:
All tools
Create and design
Write and edit
Research and strategy
Filtering by approval status:
Approved
Approved with guardrails
Pilot
Not approved
Tool cards with:
Name
Category
Approval status
Intended use
Primary caveat
Decision signal
Detailed tool view with:
Approval status
Client-work guidance
Intended use
Restrictions
Owner
Status rationale
Next action
Selection and comparison of two tools
Research context explaining why the catalog exists
Success target of reaching the right tool in under five minutes
Search-loop detection after repeated unproductive attempts
Alternative paths to describe a need or contact Help Desk
Loading, empty, and confirmation states demonstrated in the broader application flow
- **Out (explicitly):** Out

Real authentication, authorization, or employee identity
Live integration with procurement, security, or access-management systems
Real access provisioning
Real Help Desk ticket creation
Persistent request storage
Administrator interfaces for managing catalog content
Approval workflows for Security, Legal, or tool owners
Live status synchronization from external systems
Personalized recommendations
Usage reporting or experimentation dashboards
Notifications by email, Slack, or another company channel
Production analytics proving the five-minute success target
Formal accessibility testing or compliance certification

## Requirements

| # | Requirement | Priority | Acceptance criteria |
|---|---|---|---|
| 1 | Display a catalog of tools | Must | The catalog presents every configured tool with its name, category, approval status, intended use, primary caveat, and decision signal. |
| 2 | Keep comparison selection visible | Should | When at least one tool is selected, a comparison tray identifies the selected tools, shows selection progress, and allows removal. |

## Data & events

_What gets stored, what gets tracked._

Data & events
Prototype data

The prototype uses a static in-code catalog. Each tool includes:

Name
Initials or visual mark
Category
Supported use cases
Approval status
Best-use description
Restriction or caveat
Owning team
Access action label
Explanation for the status
General description
Decision signal
Visual accent
The demonstrated catalog contains:

Figma
ChatGPT Enterprise
Notion AI
Google Gemini
Grammarly
Midjourney
This data is mocked. It is not loaded from a catalog service, database, governance system, or administrative interface.

## Open questions

Open questions
What exact interaction counts as finding the “right tool” for the five-minute success metric?
Has the solution hypothesis been tested with employees, or has only the underlying problem been validated?
What baseline decision time should the new experience be compared against?
Which system is the source of truth for tools, approval statuses, restrictions, owners, and access instructions?
Who is authorized to create and update catalog entries?
How frequently must approval information be reviewed?
Should expired or unreviewed statuses be hidden, flagged, or automatically downgraded?
Which actions can be completed automatically, and which require Help Desk, Security, Legal, Procurement, or owner review?
Should “Approved” mean approved for all client work, or can approval vary by client, geography, data type, or contract?
What information is safe to collect in the access-request justification?
Should free-form search terms be recorded for analytics, given that employees may enter client or sensitive information?
What is the real Help Desk integration, ticket-reference format, and expected response-time policy?
Should the search-loop threshold remain three attempts, or should testing determine the threshold?
Should comparison remain limited to two tools?
How should employees request a tool that is not yet represented in the catalog?
Are access requests and ticket status expected to persist in the catalog?
Are employee identity, team, role, geography, and existing licenses needed to determine eligibility?
What accessibility standard and browser/device support must the production application meet?
Who owns the five-minute success metric and how often will it be reviewed?
What outcome would cause FakeCompany to stop investing in catalog-first discovery and prioritize guided intake or direct support instead?
