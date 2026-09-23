# Full-Stack: Data, Access Rules, Edge Cases, Deploy

> Module 5 · Full-Stack. Add data schemas, access rules, and edge cases; stress-test and deploy.

## Deployed link

_The working, shareable link that survives real users._

_____

## Data schema

| Entity | Key fields | Notes |
|---|---|---|
| profiles | profiles | _____ |
| request_events | request_events | _____ |

## Access rules

_Who can see / do what? Where are the auth boundaries?_

Implemented Supabase Auth and the complete authenticated access-request flow using the existing project and schema.

Authentication
Added Supabase email/password sign-in and sign-out.
Restores sessions after refresh.
Verifies bearer tokens server-side through Supabase Auth.
Handles expired, invalid, and revoked sessions.
Added a current-user provider with profile and role lookup.
Automatically creates profiles for new Auth users.
Users cannot create or assign their own roles.
Clears authenticated React Query data on logout, expiry, or account switching to prevent cross-user cache leakage.
Public catalog browsing remains available without signing in.
No service-role credential is used or exposed.
Access requests
Added generated, authenticated API contracts for:

GET /api/me
POST /api/access-requests
GET /api/access-requests
GET /api/access-requests/{id}

## Edge cases hardened

| Case | Before | After |
|---|---|---|
| Empty / first-run state | Whitespace-only | Empty or whitespace-only justification |
| Bad / malicious input | Employee assigning themselves admin | No Employee assigning themselves admin |
| Failure / offline | Submission while offline | No submission while offline |

## Stress test results

_What you threw at it, and what held / broke._

_____
