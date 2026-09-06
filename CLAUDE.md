# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working in this project.

## What this is

Engagement workspace for the **Kurrajong Energy engagement** — ten sprints against the
**Service Cloud Consultant (Service-Con-201)** track. Hemayet plays the consultant at a
fictional Australian energy retailer with 340,000 residential customers: complaints
arrive by phone, by email, and through a web form that lands in a shared inbox; there is
no knowledge base; ombudsman escalations are tracked in a spreadsheet; and regulated
response deadlines are being missed.

Kurrajong Energy Pty Ltd is fictional; no real customer data is in here.

**Current state: scaffold.** `force-app/`, `seed/` and `evidence/` hold only
`.gitkeep`. Nothing has been built yet.

## The regulated deadlines are the point

Entitlements and milestones in this engagement are not a dashboard nicety — **missing
one has an external consequence.** That is what makes the SLA design decisions real
rather than academic, and it is the lens for every review here:

- A milestone design that cannot evidence *when the clock started and stopped* is not
  finished, however good the routing is.
- Business hours, pause conditions and recalculation on reassignment are where regulated
  SLA designs actually fail. Decide them explicitly and write down why.
- Ombudsman escalation is a distinct path with its own clock, not a case priority.

## Why this is a separate engagement from Meridian

`agentforce-meridian-care` is also Service Cloud and Agentforce, for a warranty service
administrator. This track is deliberately kept apart: **Meridian is about deflecting
phone volume with an agent; Kurrajong is about regulated case handling** — statutory
response windows, ombudsman escalation, multi-channel intake and knowledge. The overlap
is the platform, not the problem. Do not carry a Meridian design decision across without
re-deriving it here.

## The org

Target org alias **`kurrajong`** — Developer Edition, org ID `00DgL00000b5i4kUAA`.

```bash
sf org display --target-org kurrajong
```

Confirmed present: Field Service entitlements — Standard (10), Dispatcher (2), Mobile
(2), Scheduling (2); Agentforce and Service User licences active. Locale already
corrected to Australian (`Country: Australia`, `DefaultLocaleSidKey: en_AU`).

Two items were outstanding as of the last README update:

1. **Currency locale is still USD.** Not settable through the API in a single-currency
   org. Setup → Company Information → Edit → Currency Locale → English (Australia) AUD.
2. **Stock Salesforce sample data is still present** (13 Accounts). Purge before seeding.
   The pattern is `seed/00-purge-sample-data.apex` in the **sunrise-solar-internship**
   repo. (The README points at `03-admin-sunrise/seed/...`, a path from before these
   engagements were split into separate repositories — that path does not exist.)

## Known repo gap

There is **no `sfdx-project.json`** in this repo, so `sf project deploy` and
`sf project retrieve` will not work against `force-app/` until one is added. The other
Salesforce repos in this program use `packageDirectories: [{path: "force-app", default:
true}]` with `sourceApiVersion: "67.0"`.

## The division of labour on this engagement

**Hemayet builds all Setup configuration by hand** — case lifecycle, Omni-Channel
routing and presence, entitlement processes and milestones, Knowledge data categories,
channels and CTI, the Agentforce agent, reports. The certification tests Setup
navigation and so does the job. Do not build config via the Metadata API on his behalf
unless he asks explicitly.

**Claude does:** seed data (Apex anonymous in `seed/`), including the deliberate defects
the engagement depends on; verification queries; evidence extraction; code review;
deployment mechanics; ERD and documentation drafting; and playing stakeholders in
character for the discovery interviews.

## Seeded data must contain the mess

Cases with no channel recorded, complaints duplicated across the shared inbox and the
web form, escalations whose spreadsheet row disagrees with the case record, and a
handful that already breached. A clean case backlog cannot demonstrate a routing or SLA
problem, and the breach cases are what make the milestone reporting worth building.

## Documentation standards

`deliverables/` is the substance and the interview evidence. The configuration proves
the clicks happened; the documents prove the thinking did.

- **Every change goes in `deliverables/build-log.md`** with its date, the component, the
  change, and the requirement it traces to. Corrections are appended as new rows, never
  edited over.
- **Claim only what was verified** — a query or a screenshot backs every "verified".
- **Accepted risks are recorded, not hidden.**
- **Dates are Australian** — `dd/mm/yyyy`.
- `evidence/` holds before/after extracts and screenshots per sprint.

## Never commit

Auth files and sfdx auth URLs — an auth URL is a full credential. `.gitignore` covers
`**/*authFile*.json`, `**/*sfdxAuthUrl*`, `.env*`, `.sf/` and `.sfdx/`. A credential
that reaches git history has to be *rotated*, not deleted.

## Agent workflow

Superpowers is expected to be installed as a **user-level plugin**
(`/plugin install superpowers@claude-plugins-official`), not vendored into this repo.
There is no test runner here and most work is Setup configuration, so the red/green TDD
skills have little to bite on; the planning, verification and code-review skills apply
to the seed scripts and the written deliverables.
