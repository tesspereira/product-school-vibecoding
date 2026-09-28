# FakeCompany Tool Catalog

_Product School · Vibe Coding Certification · Final Project Showcase_

**Live product:** https://fake-company-tool-catalog.replit.app

## The Problem & Hypothesis

**Problem.** FakeCompany employees struggle to identify which workplace tools are available, approved, and appropriate for client work.

**Hypothesis.** We believe **providing certain information about tools up front in a simple manner** will cause **employees to understand what's available to them and more easily decide if it's appropriate for their needs** for **FakeCompany employees**. We'll know we're right when **the time it takes to find the right tool is less than 5 minutes on average**.

## The Evidence

- **Hypothesis (above):**  The hypothesis is: Showing approval status, intended use, restrictions, owner, and access information up front helps employees identify an appropriate tool more quickly and confidently.

Metrics that matter:
Time to a confident tool decision
Search friction
Request-flow completion
My Requests comprehension
Request resolution

## Data Signal → The One Fix

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

## The Recommendation

**Verdict: ITERATE, keep refining.**

Based on the user data showing that 1 of 3 testers were confused when clicking "My Requests" led to an unexplained login screen, and that no one could tell how to request access to a tool, update the "My Requests" page and each tool's detail view to support a complete request flow. Specifically: (1) replace the login wall on My Requests with a page showing 2–3 example requests with statuses (Submitted, In review, Approved) and a short line explaining "This is where you track access requests you've submitted"; (2) add a "Request access" button to each tool that opens a short form with the tool name pre-filled, its approval status shown, a dropdown for "Will you use this for client work? Yes/No", and a text field for "What do you need it for?"; (3) after submitting, show a confirmation with next steps and expected turnaround, and add the new request to My Requests. Keep all existing functionality working.

## My Story, Friction · Learning · Aha

I started vibecoding the Tool Catalog as a way to help employees find approved tools, then learned that a useful catalog also needs a clear path to request access and track what happens next. The biggest break wasn’t just technical: testers hit an unexplained login screen on My Requests, and none could tell how to request a tool; I also had to make submissions reliable when tickets or connections failed. I learned to test the whole employee journey, not just whether each screen or API worked on its own. My biggest aha was that showing approval information only helps if people can turn it into a confident decision and an obvious next step.

---
_Built across six modules with an AI build tool, then iterated from live product data. Hosted on GitHub Pages._
