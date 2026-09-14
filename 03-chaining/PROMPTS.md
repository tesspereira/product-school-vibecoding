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

- _____
- _____

## What broke (and the fix)

_Where a single mega-prompt failed and chaining fixed it._

_____
