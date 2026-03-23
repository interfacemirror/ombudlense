# Implementation Plan & Ownership

## Team Structure

| Person | Role | Responsibilities |
|---|---|---|
| Person 1 | Architect & ALM Lead | Architecture, environments, ALM, governance |
| Person 2 | Channel & Routing Lead | Voice, chat, email, routing and queues |
| Person 3 | AI & Copilot Lead | AI Voice, Copilot, intents, agentic logic |
| Person 4 | Data & Integration Lead | Dataverse, integrations, deployment, reporting |

---

## Implementation Phases

### Phase 0 — Preparation (Week 1)

| Task | Owner | Status |
|---|---|---|
| Provision Dynamics 365 Contact Center environments (Dev/Test/Prod) | Person 1 | — |
| Configure ALM pipeline (Dev → Test → Prod) | Person 1 | — |
| Define governance model and solution naming conventions | Person 1 | — |
| Provision Azure OpenAI instance and keys | Person 3 | — |

### Phase 1 — Data Model & Dataverse (Week 2)

| Task | Owner | Status |
|---|---|---|
| Create Citizen (Contact) extensions | Person 4 | — |
| Create Case extensions | Person 4 | — |
| Create Property table | Person 4 | — |
| Create Approval Application table | Person 4 | — |
| Create Licence / Permit table | Person 4 | — |
| Create Interaction table | Person 4 | — |
| Configure relationships and views | Person 4 | — |

### Phase 2 — Channel & Routing (Week 2–3)

| Task | Owner | Status |
|---|---|---|
| Configure AI Voice channel | Person 2 | — |
| Configure Web Chat channel | Person 2 | — |
| Configure Email channel | Person 2 | — |
| Configure unified routing and queues (Planning queue) | Person 2 | — |
| Configure SLA rules | Person 2 | — |

### Phase 3 — AI & Copilot Studio (Week 3–4)

| Task | Owner | Status |
|---|---|---|
| Create Copilot Studio bot and connect to channels | Person 3 | — |
| Build INT‑01: Development Approval Enquiry topic | Person 3 | — |
| Build INT‑02: Fast‑Track / Escalation topic | Person 3 | — |
| Build INT‑03: Document Checklist Request topic | Person 3 | — |
| Build INT‑04: Case Status Enquiry topic | Person 3 | — |
| Build INT‑05: Licence / Permit Follow‑up topic | Person 3 | — |
| Configure Azure OpenAI plugin for AI summaries | Person 3 | — |
| Configure agentic decision logic for escalation | Person 3 | — |

### Phase 4 — Power Automate Flows (Week 3–4)

| Task | Owner | Status |
|---|---|---|
| Build Flow‑01: CreateCitizenCase | Person 4 | — |
| Build Flow‑02: EscalateToPlanningAgent | Person 4 | — |
| Build Flow‑03: CorrelateOmnichannelInteraction | Person 4 | — |
| Build Flow‑04: SendDocumentChecklist | Person 4 | — |
| Build Flow‑05: NotifyApprovalStatus | Person 4 | — |
| Build Flow‑06: PrepareLicencePathway | Person 4 | — |

### Phase 5 — Integration (Week 4)

| Task | Owner | Status |
|---|---|---|
| Integrate Council Planning System (zoning/DA rules) | Person 4 | — |
| Integrate Council Licensing System (eligibility) | Person 4 | — |
| End-to-end testing of all flows | All | — |

### Phase 6 — Dashboards & Reporting (Week 5)

| Task | Owner | Status |
|---|---|---|
| Build Executive Dashboard | Person 4 | — |
| Build Citizen Experience Dashboard | Person 4 | — |
| Build AI Effectiveness Dashboard | Person 4 | — |
| Build Agent Performance Dashboard | Person 4 | — |
| Build Approvals & Licensing Dashboard | Person 4 | — |

### Phase 7 — Demo Preparation & Submission (Week 5–6)

| Task | Owner | Status |
|---|---|---|
| Record 3‑minute demo video | All | — |
| Prepare submission artefacts | Person 1 | — |
| Final review and sign-off | All | — |
| Submit to ABS Got Talent 2025 | Person 1 | — |
