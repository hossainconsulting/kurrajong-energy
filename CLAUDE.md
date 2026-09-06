# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working in this project.

## What this is

Engagement workspace for **Kurrajong Energy** — a ten-sprint Service Cloud
Consultant simulation at a fictional Australian energy retailer with 340,000
residential customers. Complaints arrive by phone, by email, and through a web
form that lands in a shared inbox. There is no knowledge base. Ombudsman
escalations are tracked in a spreadsheet, and regulated response deadlines are
being missed.

Sprint scope: discovery, case lifecycle, Omni-Channel routing, entitlements and
regulated milestones, Knowledge, CTI and channels, Agentforce for Service, field
service basics, reporting, adoption and handover.

## The thing that makes this engagement real

**The deadlines are statutory, not internal.** Missing a milestone here has an
external consequence — an ombudsman escalation, a regulatory breach — not a red
cell on a dashboard. Every SLA design decision should be justified against that,
and an entitlement process that cannot evidence compliance after the fact has not
done its job.

Follow-on rule: reporting is not the last sprint's problem. If a milestone cannot
be reported on, it cannot be proven, and the design is incomplete regardless of
how it behaves at runtime.

## Not to be confused with the Meridian engagement

`agentforce-meridian-care` is also Service Cloud plus Agentforce. The two are
deliberately separate:

- **Meridian** — deflecting phone volume with an agent, at a warranty administrator.
- **Kurrajong** — regulated case handling: statutory response windows, ombudsman
  escalation, multi-channel intake, Knowledge.

The overlap is the platform, not the problem. Do not carry a Meridian design
decision over here on the grounds that both are Service Cloud.

## The org

Target org alias **`kurrajong`**, org ID `00DgL00000b5i4kUAA`.

```bash
sf org display --target-org kurrajong
sf data query --target-org kurrajong --query "SELECT COUNT() FROM Case"
```

Confirmed present: Field Service entitlements — Standard (10), Dispatcher (2),
Mobile (2), Scheduling (2) — plus Service User (2), Agentforce (Default),
Agentforce Service Agent Builder (10,000), Slack Service User. Field Service
basics are in the syllabus and can be exercised without further licensing.

**Two org items still outstanding** (both recorded in the build log):

1. **Currency locale is still USD.** `DefaultCurrencyIsoCode` is not a field on
   `Organization` in a single-currency org, so this cannot be set through the API.
   Setup → Company Information → Edit → Currency Locale → English (Australia) AUD.
   Do it before seeding anything with amounts.
2. **13 stock Salesforce sample Accounts are still present.** Purge before seeding,
   or case volumes blend Kurrajong with Salesforce's demo data.

Country and `DefaultLocaleSidKey` were already corrected to Australian via the API.

## The division of labour

**Hemayet builds all Setup configuration by hand** — case fields, record types,
queues, assignment rules, Omni-Channel routing, entitlement processes and
milestones, Knowledge data categories, Lightning pages, the agent itself.
Service-Con-201 tests Setup navigation and so does the job. Do not build config via
the Metadata API on his behalf unless he asks explicitly.

**Claude does:** seed data (Apex anonymous in `seed/`), verification queries, code
review, deployment mechanics, ERD and documentation drafting, build-log entries,
and playing stakeholders in character for discovery exercises.

## Repository conventions

| Folder | Contents |
|---|---|
| `force-app/` | Metadata **retrieved from** the org, not authored here |
| `seed/` | Apex anonymous scripts that build starting data, including its deliberate defects |
| `deliverables/` | Design docs, SOPs, analyses, runbooks — the substance |
| `evidence/` | Before/after screenshots and test results, per sprint |

`deliverables/build-log.md` carries five entries covering org provisioning and the
opening audit. Every subsequent change gets a row.

## Known stale reference

The README points at `03-admin-sunrise/seed/00-purge-sample-data.apex` for the
purge pattern. That path is from an earlier monorepo layout; the file now lives in
the separate `sunrise-solar-internship` repository at
`seed/00-purge-sample-data.apex`.

## Rules worth enforcing in review

- Deliberate defects in seed data are the exercise. Do not quietly fix them.
- No `sfdx-project.json` exists here yet — this repo cannot be deployed from or
  retrieved into until one is added.
- Never commit an sfdx auth URL. It is a full credential. See `.gitignore`.
