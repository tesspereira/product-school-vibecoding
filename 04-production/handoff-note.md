# Engineering Handoff Note

> Module 4 · Production Specs. Open the black box, make the build legible to an engineer.

## What this is

_One paragraph an engineer can read in 60 seconds._

60-second summary
The selected FakeCompany Tool Catalog is a frontend-only React prototype designed to test whether showing approval status, intended use, restrictions, ownership, and next steps up front helps employees choose the right tool in under five minutes. It supports catalog browsing, search, status filtering, tool details, two-tool comparison, research context, and a search-loop escape path. The code is organized by PRD feature, with static tool data and TypeScript models separated from screen and shared display components. There is no backend, persistence, authentication, real Help Desk integration, or analytics in this prototype: actions produce local confirmation notices, and all state resets when the page reloads.

## Architecture (plain language)

- **Frontend:** Frontend The prototype lives in:  artifacts/mockup-sandbox/src/components/mockups/tool-catalog/  ToolCatalogPrototype.tsx is the stable canvas entry point. It renders ToolCatalogScreen, which owns the temporary interaction state and switches between the catalog, detail, and comparison experiences.  The code is grouped by feature:  tool-catalog/ ├── ToolCatalogPrototype.tsx ├── model/ │   ├── tools.ts │   └── types.ts ├── shared/ │   ├── CompareTray.tsx │   ├── DetailBlock.tsx │   ├── Quote.tsx │   ├── StatusPill.tsx │   ├── ToolCard.tsx │   └── ToolMark.tsx └── features/     ├── tool-catalog/     │   └── ToolCatalogScreen.tsx     ├── tool-detail/     │   └── ToolDetailScreen.tsx     ├── tool-comparison/     │   └── ToolComparisonScreen.tsx     ├── search-loop/     │   └── SearchLoopScreen.tsx     └── research-context/         └── ResearchContextScreen.tsx  The UI uses:  React and TypeScript Local React state Tailwind utility classes Lucide icons The mockup sandbox’s Vite preview environment There is no route for each screen. Detail and comparison screens are conditional views inside the same prototype component.
- **Backend / data:** Backend/data There is no backend attached to the selected prototype.  Tool records are hardcoded in model/tools.ts. Each record includes:  Name and initials Category and use cases Approval status Best use Restriction or caveat Owner Access-action label Status rationale Description Decision signal Visual accent Domain types are defined in model/types.ts.  Search, filters, comparison selections, search attempts, selected tool, notices, and modal visibility exist only in component memory. They are lost on refresh and are not shared between users.  The workspace contains a separate API server, but this prototype does not call it.
- **Key flows:** Key flows
Browse and search

The employee opens the catalog.
They browse by use case, enter a search, or filter by approval status.
The catalog filters the static tool array in the browser.
A no-results state appears when no tools match.
Review a tool

The employee selects a tool card.
ToolDetailScreen replaces the catalog content.
The screen shows approval, intended use, restrictions, owner, rationale, and next action.
Selecting the primary action produces a local confirmation notice; it does not open or provision a real service.
Compare tools

The employee adds up to two tools to the comparison tray.
The comparison action becomes available after two selections.
ToolComparisonScreen displays approval, best use, caveat, owner, and next action side by side.
Selecting a tool returns to its detail screen.
Search-loop recovery

Submitted searches and approval-filter changes increment an attempt counter.
After three attempts without opening a tool, SearchLoopScreen appears.
It offers “Tell us what you need,” “Ask Help Desk,” and reset actions.
The support actions currently produce local notices only.
Research context

ResearchContextScreen is presented as a modal containing the research evidence, complaints, solution hypothesis, and under-five-minute success target.

## What's solid vs. what's duct tape

| Area | State | Notes |
|---|---|---|
| Solid Feature names and component boundaries now match the Living PRD. Static data, domain types, screens, and shared display components are separated. The original canvas entry point remains stable. Search, status filtering, use-case browsing, details, and comparison work as a coherent local flow. Comparison is limited to two tools in a predictable way. Search-loop detection is explicit and observable. Approval status combines text, iconography, and color rather than relying on color alone. The layout responds across desktop and narrower widths. The mockup-sandbox TypeScript check passes. The component preview workflow starts cleanly. | solid | _____ |
| Duct tape The catalog is a fixed in-code array rather than managed data. “Loading” is not tied to a real network request in the prototype. Access and Help Desk actions only set confirmation text. There is no request persistence or ticket creation. Search-attempt state is a simple counter; it does not distinguish useful refinement from genuine user frustration. The three-attempt search-loop threshold is an unvalidated product assumption. The “under five minutes” target is displayed but not measured. There is no authentication, authorization, employee context, or entitlement check. Approval status is not synchronized with Security, Legal, Procurement, or tool owners. No automated interaction tests protect the main flows. Screen changes are conditional component state rather than URL-addressable navigation. Refreshing the iframe returns the user to the initial catalog state. | rough | _____ |

## Risks & assumptions for the team

Risks and assumptions
Stale governance information: Static approval data can become inaccurate without an owner and review process.
Meaning of “approved”: The prototype assumes one global status per tool. Real approval may vary by client, region, contract, data classification, or use case.
False confidence: Employees may treat prototype status labels as authoritative even though they are mocked.
Success measurement: The product has not defined exactly which action means the employee found the right tool.
Search privacy: A production search box may receive client names, confidential work descriptions, or personal information. Logging raw searches would require a privacy decision.
Search-loop accuracy: Three interactions may be normal comparison behavior rather than evidence that the employee is stuck.
Access ownership: The prototype assumes each tool has one owning team and one next action.
Request workflow: It assumes Help Desk is the correct escalation point for every unresolved question.
Persistence: Current local state is appropriate for a prototype but not an operational catalog.
Accessibility: Semantic controls and visible labels are present, but the prototype has not received formal keyboard, screen-reader, zoom, contrast, or accessibility-compliance testing.
Canvas dependency: The selected component runs inside the mockup sandbox and is not itself a separately deployed application.
Scope assumption: Access Request Intake and Help Desk Confirmation exist in the separate publishable Tool Catalog app, not in this selected canvas prototype.

## How to run it

```
How to run it
From the workspace root, start the mockup sandbox:

pnpm --filter @workspace/mockup-sandbox run dev

The managed workflow is:

artifacts/mockup-sandbox: Component Preview Server

Run the TypeScript check:

pnpm --filter @workspace/mockup-sandbox run typecheck

Run a production build of the mockup sandbox:

pnpm --filter @workspace/mockup-sandbox run build

The component entry point expected by the canvas is:

artifacts/mockup-sandbox/src/components/mockups/tool-catalog/ToolCatalogPrototype.tsx

Keep the ToolCatalogPrototype named export at that path unless the canvas iframe registration is updated at the same time.
```
