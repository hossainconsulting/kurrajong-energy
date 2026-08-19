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

---

Built by [Hemayet Hossain](https://github.com/hossainconsulting) · Sydney, Australia
Portfolio: [portfolio.hossainconsulting.com](https://portfolio.hossainconsulting.com)
