# Iteration: Analytics, Sprint, Final Recommendation

> Module 6 · Evals & Iteration. Read the analytics, run an iteration sprint, present with evidence.

## What the evidence says

_What real usage showed: numbers if your tool has analytics, counted behaviour if it does not. Put the signal that matters on screen._

- **Primary signal:** The UI is clear, easy to navigate
- **What moved:** The request flow is now in place; its effect on completion hasn't been measured yet.
- **What didn't:** Some features are not turned on

_Analytics snapshot: visitors 5; page views _____; views per visit _____; duration <499 ms; bounce _____._

_Observed behaviour: reach 3; core action 3; stall point Unclear why a login screen appeared when someone clicked on "My Requests"; explained away _____; own first run _____._

## Iteration sprint

| Change | Hypothesis | Result |
|---|---|---|
| Based on the user data showing that 1 of 3 testers were confused when clicking "My Requests" led to an unexplained login screen, and that no one could tell how to request access to a tool, update the "My Requests" page and each tool's detail view to support a complete request flow. Specifically: (1) replace the login wall on My Requests with a page showing 2–3 example requests with statuses (Submitted, In review, Approved) and a short line explaining "This is where you track access requests you've submitted"; (2) add a "Request access" button to each tool that opens a short form with the tool name pre-filled, its approval status shown, a dropdown for "Will you use this for client work? Yes/No", and a text field for "What do you need it for?"; (3) after submitting, show a confirmation with next steps and expected turnaround, and add the new request to My Requests. Keep all existing functionality working. | If employees can see each tool’s approval status, intended use, restrictions, owner, and access instructions up front, they will be able to identify an appropriate tool more quickly and confidently. | _____ |

## Peer feedback

"Hi Tess, I liked the "Compare" feature based on selection of two apps.  There are many features (e.g. at the top of the screen) which are not yet implemented."

"I like how it already feels like a real, functional website because of its overall structure. I understand that some of the main navigation buttons are not enabled yet, which makes sense at this stage.

One suggestion: when using the search bar, an “Ask Help Desk” option appears. It could be helpful to add a small notes field when selecting this option, so users can briefly explain what they need help with before submitting the request to the service team.

Overall, I really like the design. The UI feels clean, simple, and easy to navigate."

"I like how the list of AI tools is sorted from approved to approved with guardrails to pilot to not approved. This will help employees navigate ambiguity as they consider what tools they want to use. My Requests took me to a log in screen and I wasn’t sure what the request meant."

## The recommendation

**Decision:** ☐ Go  ☑ Iterate  ☐ Kill

_The evidence that justifies the call:_

"The only stall point in testing was at 'My Requests': a tester hit an unexplained login screen and 'wasn't sure what the request meant'. That matters because requesting access is the step behind the problem we're solving, where 80% of Help Desk tickets concern tool approval."

## Final showcase

- **Demo link:** https://fake-company-tool-catalog.replit.app
- **The one-sentence story:** A catalog of company-approved and available software that employees can request and use to do their work.
- **Where it landed on the Confidence Line (M2 → now):** Still iterating
