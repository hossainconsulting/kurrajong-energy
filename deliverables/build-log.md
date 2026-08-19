# Build log — Kurrajong Energy Engagement

Every change, with the reason and the requirement it traces to. This is the
artefact that survives the project and the one an auditor or a successor reads.

| Date | Component | Type | Change | Why / requirement |
|---|---|---|---|---|
| 19/08/2026 | Org: `kurrajong` | Provisioning | Developer Edition created, named Kurrajong Energy (`00DgL00000b5i4kUAA`), authenticated to the CLI as alias `kurrajong` | Dedicated org for the Service Cloud Consultant track, kept separate from `01-agentforce-meridian` which also covers Service Cloud + Agentforce |
| 19/08/2026 | Org: `kurrajong` | Correction | Country → Australia, `DefaultLocaleSidKey` → `en_AU` via the API | Org provisioned as `Country: United States`, `en_US`, despite Australia being selected at signup. Third occurrence — this is systematic with these DE signups, not a signup error. Fixed before any data was loaded |
| 19/08/2026 | Org: `kurrajong` | Audit | Field Service entitlements confirmed: Standard (10), Dispatcher (2), Mobile (2), Scheduling (2). Also `Service User` (2), `Agentforce (Default)`, `Agentforce Service Agent Builder` (10,000), `Slack Service User` | Field Service basics are in the Service-Con-201 syllabus; confirms they can be exercised in this org without further licensing |
| 19/08/2026 | Org: `kurrajong` | Finding | Currency locale still USD. `DefaultCurrencyIsoCode` is not a field on `Organization` in a single-currency org, so it cannot be set through the API | Must be changed in Setup before seeding data with amounts |
| 19/08/2026 | Org: `kurrajong` | Finding | Stock Salesforce sample data present — 13 Accounts | Purge before seeding, or case volumes and account figures blend Kurrajong with Salesforce's demo data |
