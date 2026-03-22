# AI‑Powered Council Approvals & Licensing Concierge — Solution Design

## Executive Summary

This document is the single, authoritative solution design for the ABS Got Talent 2025 submission by Team OmbudLens. It consolidates the full use case, citizen transcript, architecture, data model, AI intent design, Power Automate flows, KPIs, dashboards, and execution plan into one end‑to‑end, build‑ready artefact. No supporting or addendum documents are required.

---

## Use Case Overview

A citizen contacts an Australian local council to enquire about building a granny flat. The enquiry begins on phone, continues via chat and email, and later expands into licensing and permits. The citizen never repeats information, and the council manages the entire journey through a single case.

---

## Problem Statement

Councils experience high enquiry volumes, fragmented channels, and manual triage. Citizens face long wait times, inconsistent answers, and duplicated effort. Council officers spend excessive time responding to basic enquiries instead of assessing applications.

---

## Solution Overview

The solution uses Dynamics 365 Contact Center with AI Voice, Copilot, Copilot Studio, and Power Automate to deliver an AI‑first Council Approvals & Licensing Concierge. The platform supports omnichannel engagement, intelligent triage, case creation, agent assist, and lifecycle continuity.

---

## Transcript‑to‑Design Correlation

| Citizen Statement | Intent | Flow | Outcome |
|---|---|---|---|
| "I want to build a granny flat" | INT‑01 | Flow‑01 | Case created and Case Number returned |
| "Can I fast‑track this?" | INT‑02 | Flow‑02 | Escalation to Planning Agent |
| Citizen switches to chat/email | — | Flow‑03 | Same Case continued |
| "What documents do I need?" | INT‑03 | Flow‑04 | Checklist delivered |
| "Can this become a licence later?" | INT‑05 | Flow‑06 | Licence pathway created |

---

## Copilot Studio — Intent Design

| Intent ID | Name | Trigger Phrases |
|---|---|---|
| INT‑01 | Development Approval Enquiry | build, extension, granny flat, development application |
| INT‑02 | Fast‑Track / Escalation | fast-track, urgent, escalate, speak to officer |
| INT‑03 | Document Checklist Request | what documents, what forms, checklist, what do I need |
| INT‑04 | Case Status Enquiry | status, progress, update, timeline, how long |
| INT‑05 | Licence / Permit Follow‑up | licence, permit, rental, post-approval |

---

## Scenario Orchestration — Flow‑Level Design

### Flow‑01: CreateCitizenCase

- **Trigger:** INT‑01 from AI Voice or Chat
- **Input:** Citizen details, property details
- **Action:** Create/Match Contact → Create Case → Generate AI Summary
- **Output:** Case Number

### Flow‑02: EscalateToPlanningAgent

- **Trigger:** INT‑02 or low sentiment score
- **Input:** Case ID, sentiment score
- **Action:** Route to Planning queue → Prepare Copilot context
- **Output:** Assigned Agent

### Flow‑03: CorrelateOmnichannelInteraction

- **Trigger:** Incoming chat or email
- **Input:** Citizen identifier, message
- **Action:** Match Case → Create Interaction record
- **Output:** Updated Case Timeline

### Flow‑04: SendDocumentChecklist

- **Trigger:** INT‑03
- **Input:** Case ID
- **Action:** Retrieve checklist → Send via preferred channel
- **Output:** Checklist sent

### Flow‑05: NotifyApprovalStatus

- **Trigger:** Approval status update
- **Input:** Application ID, status
- **Action:** Update Case → Notify citizen
- **Output:** Notification sent

### Flow‑06: PrepareLicencePathway

- **Trigger:** INT‑05
- **Input:** Case ID, approval outcome
- **Action:** Create draft Licence → Update AI summary
- **Output:** Licence pathway recorded
