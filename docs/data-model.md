# Dataverse Data Model

All entities are stored in **Microsoft Dataverse** as part of the Dynamics 365 Contact Center solution. Table schema JSON definitions are located in [`src/dataverse/tables/`](../src/dataverse/tables/).

---

## Entity Relationship Overview

```
Citizen (Contact)
    └── Case
            ├── Property
            ├── Interaction (many)
            ├── Approval Application
            │       └── Licence / Permit
            └── (AI Summary, Sentiment Score)
```

---

## Table Definitions

### Citizen (Contact)

Extends the standard Dynamics 365 **Contact** table with council-specific fields.

| Field | Type | Description |
|---|---|---|
| Citizen ID | GUID (PK) | Unique identifier |
| First Name | Text | Given name |
| Last Name | Text | Family name |
| Primary Phone | Phone | Primary contact number |
| Primary Email | Email | Primary email address |
| Address | Text | Street address |
| Suburb | Text | Suburb |
| State | Text (Choice) | Australian state or territory |
| Postcode | Text | Postcode |
| Preferred Channel | Choice | Phone / Chat / Email |
| Consent Flag | Boolean | Consent to data collection |
| Language Preference | Choice | Preferred language |

---

### Case

Extends the standard Dynamics 365 **Case (Incident)** table.

| Field | Type | Description |
|---|---|---|
| Case Number | Auto-number (PK) | Unique case reference (e.g. ABC‑12345) |
| Case Type | Choice | Development / Licensing / Enquiry |
| Category | Choice | Granny Flat / Extension / Permit / Other |
| Status | Choice | Open / In Progress / Pending / Closed |
| Sub‑Status | Choice | Awaiting Documents / Awaiting Assessment / etc. |
| Priority | Choice | Low / Normal / High / Critical |
| Origin Channel | Choice | Phone / Chat / Email |
| Created On | DateTime | Timestamp of case creation |
| Assigned Queue | Lookup (Queue) | Current service queue |
| Assigned Agent | Lookup (User) | Currently assigned agent |
| AI Summary | Multiline Text | AI-generated case summary |
| Sentiment Score | Decimal | Sentiment score (−1.0 to +1.0) |
| SLA Due Date | DateTime | SLA target date/time |

---

### Property

| Field | Type | Description |
|---|---|---|
| Property ID | GUID (PK) | Unique identifier |
| Address | Text | Full property address |
| Lot / Plan Number | Text | Lot and plan number |
| Property Type | Choice | Residential / Commercial / Rural |
| Council Zone | Text | Council planning zone code |
| Risk Category | Choice | Low / Medium / High |
| Heritage Flag | Boolean | Heritage-listed indicator |

---

### Approval Application

| Field | Type | Description |
|---|---|---|
| Application ID | GUID (PK) | Unique identifier |
| Application Type | Choice | Development Approval / Building Permit / Other |
| Linked Case | Lookup (Case) | Related case |
| Submission Date | Date | Date application was submitted |
| Assessment Status | Choice | Submitted / Under Assessment / Approved / Rejected |
| Decision Outcome | Choice | Approved / Conditional Approval / Rejected |
| Decision Date | Date | Date of final decision |
| SLA Target | DateTime | SLA target for assessment completion |

---

### Licence / Permit

| Field | Type | Description |
|---|---|---|
| Licence ID | GUID (PK) | Unique identifier |
| Licence Type | Choice | Building / Rental / Development / Other |
| Linked Approval | Lookup (Approval Application) | Related approval |
| Issue Date | Date | Date licence was issued |
| Expiry Date | Date | Licence expiry date |
| Status | Choice | Draft / Active / Expired / Revoked |
| Renewal Eligible | Boolean | Whether renewal is eligible |

---

### Interaction

| Field | Type | Description |
|---|---|---|
| Interaction ID | GUID (PK) | Unique identifier |
| Case | Lookup (Case) | Related case |
| Channel | Choice | Phone / Chat / Email |
| Start Time | DateTime | Interaction start timestamp |
| End Time | DateTime | Interaction end timestamp |
| Transcript | Multiline Text | Full interaction transcript |
| Interaction Summary | Multiline Text | AI-generated summary |
| Handled by AI Flag | Boolean | Whether AI handled without agent |
