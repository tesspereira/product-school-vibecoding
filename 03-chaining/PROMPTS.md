# PROMPTS.md: Living Prompt Pack

> Module 3 · Prompt Chaining. Re-architect the build with prompt chains; capture the reusable ones here.

## How to use this pack

_Each prompt is a reusable step. Chain them: the output of one becomes the input to the next._

## Prompt chain: Make this better chain

### Step 1: Expand, build new screens in a strict sequence
```
Build the next phase of this app in a strict sequence:
1. Add a screen "Access Request Intake". Match the layout and spacing of the attached tool-detail-view screenshot — same card structure, same field order (justification → client-work flag → submit).
2. Add a screen "Help Desk Confirmation". Match the data density of the attached confirmation-notice screenshot (ticket reference, expected response time, link back to catalog).
3. Navigation: write the logic so "Access Request Intake" links to "Help Desk Confirmation" on submit.

Build these in order so "Access Request Intake" is the anchor for "Help Desk Confirmation".
```

### Step 2: Behavior, hard-code the states
```
Apply the following logic constraints to the comparison-tray flow:
- Use skeleton screens for the tool-card list loading state.
- If no data is present, show the empty state: "No tools match your filters — reset filters or browse by use case."
- On fetch failure, trigger the error state: "We couldn't submit your request. Try again, or contact Help Desk directly."

Maintain the same design language throughout and tether all behavior strictly to these rules.
```

### Step 3: Refine, one surgical polish
```
The tool-card approval-status badge needs a professional accessibility polish.
1. Start by listing the 3 biggest gaps in scannability and spacing compared to the approved prototype's badge treatment.
2. Once you've identified those, resize the badge and update the icon+label pairing so status is never color-only.

Don't change anything else in the project or touch the underlying logic.
```

## Reusable techniques learned

- - Separating expansion from behavior (Step 1 vs Step 2) keeps each prompt focused — screens get built without logic bleeding in, and logic gets applied without triggering unplanned screen changes.
- _____

## What broke (and the fix)

_Where a single mega-prompt failed and chaining fixed it._

A single mega-prompt for this app produced a build with no clear kill switch — the search-loop pivot wasn't observable, so there was no signal telling us the catalog-first approach wasn't working. It also left the "Unapproved" tool path as a dead end: an employee could see a tool was unapproved but had nowhere to go from there (no alternative, no explanation, no next action). Chaining fixed both — Step 1 forced the pivot screens (search-loop state, alternative paths) to be built explicitly as their own step rather than getting lost inside a broader "add the catalog" prompt, and Step 2 forced every terminal state, including "Unapproved," to resolve to a defined next action instead of silently stopping.
