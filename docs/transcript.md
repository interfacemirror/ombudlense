# Full End-to-End Demo Transcript

This document provides the complete, literal, step-by-step transcript of the use case. Each step maps directly to system behaviour defined in the [Solution Design](solution-design.md).

---

## Phase 1: Phone Call — AI Voice Channel

| Step | Actor | Statement / Action |
|---|---|---|
| 1 | Citizen | Dials the council contact number. |
| 2 | AI Voice Bot | "Welcome to Council Services. How can I help you today?" |
| 3 | Citizen | "I want to build a granny flat." |
| 4 | System | AI detects **INT‑01** (Development Approval Enquiry). |
| 5 | AI Voice Bot | Asks follow-up questions: property address, suburb, and property type. |
| 6 | Citizen | Provides property details. |
| 7 | System | **Flow‑01** (CreateCitizenCase) is triggered. |
| 8 | System | Creates or matches Citizen (Contact) record. |
| 9 | System | Creates a new Case and generates an AI summary. |
| 10 | AI Voice Bot | "I've created a case for you. Your reference number is ABC‑12345." |

---

## Phase 2: Voice Escalation — Copilot-Assisted Agent

| Step | Actor | Statement / Action |
|---|---|---|
| 11 | Citizen | "Can I fast-track this approval?" |
| 12 | System | AI detects **INT‑02** (Fast‑Track / Escalation). |
| 13 | System | Sentiment and intent confidence are evaluated. |
| 14 | System | **Flow‑02** (EscalateToPlanningAgent) is triggered. |
| 15 | System | Case is routed to the Planning Officer queue. |
| 16 | System | Copilot prepares an agent briefing with case summary and policy guidance. |
| 17 | Agent | Answers the call and sees Copilot context instantly. |
| 18 | Agent | "I can see your case and property details. Let me explain your fast-track options." |

---

## Phase 3: Chat Channel — Same Case Continuation

| Step | Actor | Statement / Action |
|---|---|---|
| 19 | Citizen | Opens the council website and starts a web chat. |
| 20 | Citizen | "What documents do I need?" |
| 21 | System | AI detects **INT‑03** (Document Checklist Request). |
| 22 | System | **Flow‑03** (CorrelateOmnichannelInteraction) matches the chat to Case ABC‑12345. |
| 23 | System | Interaction record is created and added to the Case timeline. |
| 24 | System | **Flow‑04** (SendDocumentChecklist) retrieves the required checklist. |
| 25 | AI Chat Bot | Responds in chat with the document list and next steps. |

---

## Phase 4: Email Channel — Licensing Follow‑Up

| Step | Actor | Statement / Action |
|---|---|---|
| 26 | Citizen | Replies to the follow-up email sent by the council. |
| 27 | Citizen | "Can this approval be used for a rental licence later?" |
| 28 | System | AI detects **INT‑05** (Licence / Permit Follow‑up). |
| 29 | System | **Flow‑06** (PrepareLicencePathway) is triggered. |
| 30 | System | Validates licence eligibility rules. |
| 31 | System | A draft Licence / Permit record is created and linked to the Case. |
| 32 | System | AI updates the case summary with the future licensing pathway. |
| 33 | System | AI drafts an email response explaining the licensing steps. |

---

## Phase 5: Case Closure & Measurement

| Step | Actor | Statement / Action |
|---|---|---|
| 34 | Council Staff | Updates the Approval Application status. |
| 35 | System | **Flow‑05** (NotifyApprovalStatus) updates the Case and notifies the citizen. |
| 36 | System | Case metrics are captured for reporting (AHT, CSAT, AI deflection). |
| 37 | System | Case is closed or moved to the next lifecycle stage. |
