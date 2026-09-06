# Kurrajong Energy Engagement

> **This is a simulation, not client work.** Kurrajong Energy Pty Ltd is a fictional company.
> This repository documents a self-directed Salesforce project built to develop
> and evidence implementation skills. No real customer data appears anywhere in it.

**Certification track:** Service Cloud Consultant (Service-Con-201)
**Salesforce org:** Developer Edition (CLI alias `kurrajong`)
**Scope:** 10 sprints | discovery, case lifecycle, Omni-Channel routing, entitlements and regulated milestones, Knowledge, CTI and channels, Agentforce for Service, field service basics, reporting, adoption and handover

## The brief

An Australian energy retailer with 340,000 residential customers. Complaints
arrive by phone, by email, and through a web form that lands in a shared inbox.
There is no knowledge base. Ombudsman escalations are tracked in a spreadsheet,
and regulated response deadlines are being missed.

The regulated deadlines are the point. Entitlements and milestones in this
engagement are not a dashboard nicety — missing one has an external consequence,
which is what makes the SLA design decisions real rather than academic.

## Why this is a separate engagement from Meridian

`01-agentforce-meridian` is also Service Cloud and Agentforce, for a warranty
service administrator. This track is deliberately kept apart: Meridian is about
deflecting phone volume with an agent, Kurrajong is about **regulated case
handling** — statutory response windows, ombudsman escalation, multi-channel
intake and knowledge. The overlap is the platform, not the problem.

## What's in here

| Folder | Contents |
|---|---|
| `force-app/` | Salesforce metadata retrieved from the org — the configuration itself |
| `seed/` | Apex scripts that build the starting data, including its deliberate defects |
| `deliverables/` | The written work: design docs, SOPs, analyses, runbooks |
| `evidence/` | Before/after screenshots and test results per phase |

`deliverables/` is the substance. The configuration proves the clicks happened;
the documents prove the thinking did.

## Progress

Build log lives in `deliverables/build-log.md` — every change with its date,
reason, and the requirement it traces to.

## Org state

- [x] Org created and authenticated (`kurrajong`, `00DgL00000b5i4kUAA`)
- [x] Locale corrected to Australian — provisioned as US despite the signup form,
      as with every other org in this program. `Country: Australia`,
      `DefaultLocaleSidKey: en_AU`
- [x] Field Service entitlements confirmed present: Standard (10), Dispatcher (2),
      Mobile (2), Scheduling (2). Agentforce and Service User licences also active
- [ ] **Currency locale still USD.** Setup → Company Information → Edit →
      **Currency Locale** → English (Australia) AUD. Not settable through the API
      in a single-currency org
- [ ] Stock Salesforce sample data still present (13 Accounts). Purge before
      seeding — see `03-admin-sunrise/seed/00-purge-sample-data.apex`

## For recruiters and agencies

**What this repository evidences:** Service Cloud Consultant discipline for regulated case
handling — entitlements and milestones with an external consequence, business hours and
pause conditions decided explicitly, and ombudsman escalation as its own path with its own
clock.

**State as at 06/09/2026:** Scoped; org provisioned, Field Service and Agentforce
entitlements confirmed. No sprint has been built yet, and this README will say so until
one has.

**Read these first:**

1. [`deliverables/build-log.md`](deliverables/build-log.md) — the record so far, including the org audit
2. [`CLAUDE.md`](CLAUDE.md) — the engagement rules and why this is kept apart from the Meridian engagement

**How to verify:** every change is in the build log with its date and the requirement it
traces to; corrections are appended, never edited over. The
[skill-to-evidence map](https://portfolio.hossainconsulting.com/#evidence) on the portfolio shows where each certification is
applied, and the [hiring page](https://portfolio.hossainconsulting.com/#hire) says what I am open to.

---

Built by [Hemayet Hossain](https://github.com/hossainconsulting) · Sydney, Australia
Portfolio: [portfolio.hossainconsulting.com](https://portfolio.hossainconsulting.com)

---

## Connect

Built by **Hemayet Hossain**, Salesforce administrator and implementation
consultant, Sydney, Australia. This is one of eight projects
published in full; the complete record and the certification track are on the
portfolio.

[Portfolio](https://portfolio.hossainconsulting.com/?utm_source=github&utm_medium=readme&utm_campaign=kurrajong-energy) ·
[All links](https://portfolio.hossainconsulting.com/links) ·
[GitHub](https://github.com/hossainconsulting) ·
[LinkedIn](https://www.linkedin.com/company/hossain-consulting) ·
[Instagram](https://www.instagram.com/hossainconsulting/)
