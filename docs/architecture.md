# Solution Architecture

## Architecture Layers

### Experience Layer

| Channel | Technology |
|---|---|
| Phone | AI Voice (Dynamics 365 Contact Center) |
| Web Chat | Dynamics 365 Omnichannel Web Chat |
| Email | Dynamics 365 Omnichannel Email |

### Platform Layer

| Component | Role |
|---|---|
| Dynamics 365 Contact Center | Core service desk and case management platform |
| Omnichannel for Customer Service | Unified routing and channel management |
| Copilot for Service | Agent‑facing AI assistance and briefing |

### AI Layer

| Component | Role |
|---|---|
| Copilot Studio | Intent recognition, topic management, agentic orchestration |
| Azure OpenAI | Large language model for AI summaries, sentiment, and drafting |
| Agentic Decision Logic | Rules-based escalation and pathway selection |

### Data Layer

| Component | Role |
|---|---|
| Dataverse | Primary data store for all entities |
| Council Planning System | External system integration for zoning and DA rules |
| Council Licensing System | External system integration for licence eligibility and throughput |

---

## Architecture Diagram (Text Representation)

```
┌───────────────────────────────────────────────────────┐
│                   EXPERIENCE LAYER                    │
│   [ Phone / AI Voice ]  [ Web Chat ]  [ Email ]       │
└────────────────────┬──────────────────────────────────┘
                     │
┌────────────────────▼──────────────────────────────────┐
│                   PLATFORM LAYER                      │
│  Dynamics 365 Contact Center  │  Omnichannel          │
│  Copilot for Service (Agent Assist)                   │
└────────────────────┬──────────────────────────────────┘
                     │
┌────────────────────▼──────────────────────────────────┐
│                     AI LAYER                          │
│  Copilot Studio  │  Azure OpenAI  │  Agentic Logic    │
└────────────────────┬──────────────────────────────────┘
                     │
┌────────────────────▼──────────────────────────────────┐
│                    DATA LAYER                         │
│  Dataverse  │  Council Planning  │  Council Licensing │
└───────────────────────────────────────────────────────┘
```

---

## Channel Flow

1. Citizen initiates contact via **Phone**, **Chat**, or **Email**.
2. **Copilot Studio** identifies the intent and initiates the appropriate **Power Automate flow**.
3. The flow creates or matches a **Contact** record and creates or updates a **Case** in **Dataverse**.
4. If escalation is required, the case is routed to the **Planning Officer queue** with **Copilot for Service** context pre-loaded.
5. Subsequent interactions across any channel are correlated to the same **Case** via **Flow‑03**.
6. Council staff update the **Approval Application** status, triggering **Flow‑05** to notify the citizen.
7. If a licence pathway is requested, **Flow‑06** creates a draft **Licence / Permit** record and updates the case summary.

---

## Integration Points

| Integration | Direction | Method |
|---|---|---|
| Council Planning System | Read | REST API / Dataverse Virtual Table |
| Council Licensing System | Read/Write | REST API / Power Automate connector |
| Azure OpenAI | Read | Azure OpenAI REST API via Copilot Studio |
| Citizen Notification (Email/SMS) | Write | Power Automate + Dynamics 365 Email / Twilio |
