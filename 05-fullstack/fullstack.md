# Full-Stack: Data, Access Rules, Edge Cases, Deploy

> Module 5 · Full-Stack. Add data schemas, access rules, and edge cases; stress-test and deploy.

## Deployed link

_The working, shareable link that survives real users._

https://fake-company-tool-catalog.replit.app

## Data schema

| Entity | Key fields | Notes |
|---|---|---|
| profiles | profiles | _____ |
| request_events | request_events | _____ |

## Access rules

_Who can see / do what? Where are the auth boundaries?_

Who	Can see	Can do
Visitor (not signed in): Can see Active catalog tools and their status, including tools marked “Not approved”. Can Browse and search. Cannot submit or view requests.
Signed-in user: Can see Catalog, their own profile and role information, and their own requests, tickets, and request events. Can Submit an access request for an eligible tool and retry ticket creation for their own request.
Reviewer or admin: Can see Everything a signed-in user can see, plus all requests, tickets, and request events at the database-policy level. Can Move requests through legal review statuses, with a required reason. Permission is checked again when each change is made, so revoking the role takes effect immediately.
Backend service / scheduled worker: Can see Private outbox data and operational records. Can Manage catalog and roles, create tickets, process the outbox, and perform other service-only writes.

## Edge cases hardened

| Case | Before | After |
|---|---|---|
| Empty / first-run state | Whitespace-only | Empty or whitespace-only justification |
| Bad / malicious input | Employee assigning themselves admin | No Employee assigning themselves admin |
| Failure / offline | Submission while offline | No submission while offline |

## Stress test results

_What you threw at it, and what held / broke._

Two simultaneous submissions with the same idempotency key: one durable request was created; the other response was a replay of that request.
Rapid double-click: the browser sent one submission request.
Ticket recovery: a pending request gained a ticket reference, and the reference remained after reload. Rollback-only database checks also passed for retry backoff and idempotent ticket creation.
Failure recovery: a stalled fetch timed out instead of loading indefinitely; a subsequent retry succeeded.
