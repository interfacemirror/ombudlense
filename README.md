# OmbudLens

AI‑Powered Council Approvals & Licensing Concierge — ABS Got Talent 2025 submission by Team OmbudLens.

## Overview

OmbudLens is a solution built on **Dynamics 365 Contact Center** with AI Voice, Copilot, Copilot Studio, and Power Automate. It delivers an AI‑first Council Approvals & Licensing Concierge that supports omnichannel citizen engagement, intelligent triage, case creation, agent assist, and full lifecycle continuity.

A citizen contacting an Australian local council (e.g. to enquire about building a granny flat) never repeats information across channels, and the council manages the entire journey through a single case.

## Repository Structure

```
ombudlense/
├── docs/
│   ├── solution-design.md       # End-to-end authoritative solution design
│   ├── architecture.md          # Solution architecture layers
│   ├── data-model.md            # Dataverse table-level field definitions
│   ├── transcript.md            # Full end-to-end demo transcript
│   ├── dashboards.md            # KPI dashboard definitions
│   └── implementation-plan.md  # Implementation plan and team ownership
└── src/
    ├── dataverse/
    │   └── tables/              # Dataverse table schema definitions (JSON)
    ├── flows/                   # Power Automate flow definitions (JSON)
    └── copilot/
        └── intents/             # Copilot Studio intent definitions (JSON)
```

## Key Artefacts

| Area | Document / File |
|---|---|
| Solution Design | [docs/solution-design.md](docs/solution-design.md) |
| Architecture | [docs/architecture.md](docs/architecture.md) |
| Data Model | [docs/data-model.md](docs/data-model.md) |
| Demo Transcript | [docs/transcript.md](docs/transcript.md) |
| Dashboards & KPIs | [docs/dashboards.md](docs/dashboards.md) |
| Implementation Plan | [docs/implementation-plan.md](docs/implementation-plan.md) |
| Dataverse Tables | [src/dataverse/tables/](src/dataverse/tables/) |
| Power Automate Flows | [src/flows/](src/flows/) |
| Copilot Studio Intents | [src/copilot/intents/](src/copilot/intents/) |

## Quick Links — Scenario Flows

| Flow | Name | Trigger |
|---|---|---|
| Flow‑01 | CreateCitizenCase | INT‑01 from AI Voice or Chat |
| Flow‑02 | EscalateToPlanningAgent | INT‑02 or low sentiment score |
| Flow‑03 | CorrelateOmnichannelInteraction | Incoming chat or email |
| Flow‑04 | SendDocumentChecklist | INT‑03 |
| Flow‑05 | NotifyApprovalStatus | Approval status update |
| Flow‑06 | PrepareLicencePathway | INT‑05 |

## Quick Links — Copilot Studio Intents

| Intent | Name | Triggers |
|---|---|---|
| INT‑01 | Development Approval Enquiry | build, extension, granny flat queries |
| INT‑02 | Fast‑Track / Escalation | urgency or officer request |
| INT‑03 | Document Checklist Request | document/form queries |
| INT‑04 | Case Status Enquiry | progress/timeline questions |
| INT‑05 | Licence / Permit Follow‑up | post‑approval queries |

## 3‑Minute Demo Script

| Time | Scene |
|---|---|
| 0:00–0:20 | Council challenges and citizen pain points |
| 0:20–1:10 | AI Voice handles enquiry and creates a case |
| 1:10–1:50 | Copilot‑assisted escalation to planning officer |
| 1:50–2:30 | Chat and email continuation on the same case |
| 2:30–3:00 | Metrics, outcomes, and scalability |
