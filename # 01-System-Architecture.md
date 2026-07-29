# 01-System-Architecture.md

# Enterprise AI Intelligent Document Processing Platform

Version: 1.0

Status: Production Blueprint

Author: Samiul Islam

Architecture Type:
Enterprise Intelligent Document Processing Platform (IDP)

Target Platform

- n8n
- Airtable
- OpenAI
- Gmail
- Telegram
- Google Vision OCR (Optional)

------

# CRITICAL IMPLEMENTATION CONTRACT

This document is the official Enterprise Architecture Contract for the Intelligent Document Processing Platform.

Every AI, developer, automation engineer, or workflow designer must strictly follow this architecture exactly as documented.

This document is the Single Source of Truth (SSOT) for the entire project.

No workflow, database schema, processing sequence, AI logic, business rule, validation rule, routing strategy, or monitoring mechanism may be modified without explicit user approval.

The architecture defined in this document is LOCKED.

---

# Mandatory Processing Contract

The complete processing sequence must always follow this order.

```
Gmail Intake
        ↓
Attachment Processing
        ↓
Document Content Extraction
        ↓
Document Normalization
        ↓
Rule-Based Classification
        ↓
Duplicate Detection (Airtable Document Registry)
        ↓
Duplicate Decision
        ↓
Confidence Evaluation
        ↓
AI Fallback (Only when confidence is below threshold)
        ↓
Business Rules Engine
        ↓
Validation Engine
        ↓
Human Review (Only when validation or AI fails)
        ↓
Document Routing
        ↓
Business Processing
        ↓
Airtable Database Update
        ↓
Audit Logging
        ↓
Monitoring
        ↓
Notifications
        ↓
Analytics Dashboard
```

---

# Mandatory Classification Policy

Document classification MUST use document content only.

Allowed sources

- Extracted PDF Text
- OCR Output
- Vision OCR Output

Never use

- File Name
- Attachment Name
- Gmail Subject
- Email Body Subject
- Folder Name
- MIME Type
- File Extension

---

# Mandatory Rule Engine Policy

The Rule-Based Engine is the primary decision engine.

AI is NOT the primary classifier.

Processing priority is always

1. Rule-Based Engine
2. Duplicate Detection
3. Confidence Evaluation
4. AI Fallback
5. Human Review

AI must never execute before the Rule-Based Engine or Duplicate Detection.

---

# Mandatory Duplicate Detection Policy

Duplicate Detection MUST always be performed using Airtable Document Registry before any AI execution.

Duplicate Detection must use

- Composite Business Key
- File Hash (SHA-256)
- Document Type
- Business Metadata

Duplicate Detection must never rely on file names or email subjects.

---

# Mandatory Human Review Policy

Human Review is the final safety layer.

A document must be sent to Human Review if

- Rule Engine cannot classify
- AI confidence is below threshold
- Validation fails
- Required fields are missing
- Business rules fail
- Duplicate status is ambiguous

---

# Architecture Lock

The AI must NEVER

- Change the workflow sequence
- Skip a processing layer
- Merge unrelated layers
- Replace Rule Engine with AI
- Execute AI before Duplicate Detection
- Change Airtable schemas
- Rename production tables
- Remove metadata
- Change business rules
- Change the architecture without explicit user approval

This architecture is permanently locked unless the project owner explicitly authorizes a revision.

---

# 1. Project Vision

The goal of this project is to build a fully automated Enterprise Intelligent Document Processing Platform capable of processing business documents at production scale.

The platform must automatically receive documents from Gmail, identify document types using document content (never file names), detect duplicates, classify documents, extract structured data, validate business rules, update Airtable databases, maintain complete audit trails, and support AI fallback with human review.

The system must be modular, scalable, auditable, and enterprise-ready.

---

# 2. Core Principles

The following principles are mandatory.

## Principle 1

Document classification MUST use document content.

Never use:

- File Name
- Attachment Name
- Gmail Subject
- File Extension

Only use:

- Extracted PDF Text
- OCR Result
- Vision OCR Result

---

## Principle 2

Rule-Based Engine must always execute first.

---

## Principle 3

Duplicate Detection must execute before AI.

---

## Principle 4

AI is only a fallback engine.

---

## Principle 5

Human Review is the final fallback.

---

## Principle 6

Every document must have an audit trail.

---

## Principle 7

Every workflow execution must be traceable.

---

## Principle 8

All metadata must be preserved.

---

## Principle 9

Business tables cannot be updated before validation succeeds.

---

# 3. Enterprise Processing Sequence

WF-01 Gmail Intake

↓

WF-02 Attachment Processor

↓

WF-03 Text Extraction

↓

WF-04 Unified Text Processing

↓

WF-05 Rule-Based Classification

↓

WF-06 Duplicate Detection

↓

WF-07 Airtable Registry Search

↓

WF-08 Duplicate Decision

↓

WF-09 Confidence Decision

↓

WF-10 AI Fallback

↓

WF-11 Human Review

↓

WF-12 Business Rules Engine

↓

WF-13 Validation Engine

↓

WF-14 Document Router

↓

WF-15 Database Update

↓

WF-16 Audit Logging

↓

WF-17 Monitoring

↓

WF-18 Error Handling

↓

WF-19 Notifications

↓

WF-20 Dashboard Analytics

---

# 4. Enterprise Workflow Blueprint

====================================================================

📧 LAYER 1 : INGESTION

====================================================================

Gmail Trigger

↓

Get Email

↓

Download Attachments

↓

Attachment Metadata Extractor

Store:

- Gmail Message ID
- Sender
- Subject
- Attachment Name
- MIME Type
- File Size
- Timestamp

↓

Next Layer

====================================================================

LAYER 2 : FILE PROCESSING

====================================================================

IF File Type

├── Digital PDF

├── Scanned PDF

└── Image

↓

Digital PDF

↓

Extract From File

↓

Scanned PDF

↓

OCR

↓

Image

↓

Vision OCR

↓

Merge

↓

Unified Text

====================================================================

LAYER 3 : DOCUMENT NORMALIZATION

====================================================================

Normalize

- Dates

- Currency

- Amounts

- Spaces

- Supplier

- Customer

↓

Output

Normalized Document Object

====================================================================

LAYER 4 : RULE-BASED ENGINE

====================================================================

Detect

Invoice

Purchase Order

Payment Receipt

↓

Extract

↓

Confidence Score

↓

Detected Elements

↓

Output

Classification Result

====================================================================

LAYER 5 : DUPLICATE DETECTION

====================================================================

Generate Business Key

↓

Generate File Hash

↓

Search Airtable Registry

↓

IF Duplicate

YES

↓

Update Registry

↓

Stop Workflow

NO

↓

Continue

====================================================================

LAYER 6 : CONFIDENCE DECISION

====================================================================

Confidence >= Threshold

YES

↓

Continue

NO

↓

AI Fallback

====================================================================

LAYER 7 : AI FALLBACK

====================================================================

AI Classification

↓

AI Extraction

↓

AI Validation

↓

AI Confidence

↓

IF Success

↓

Continue

IF Fail

↓

Human Review

====================================================================

LAYER 8 : BUSINESS RULES

====================================================================

Business Validation

↓

Amount Validation

↓

Vendor Validation

↓

Customer Validation

↓

Required Fields

↓

Continue

====================================================================

LAYER 9 : VALIDATION ENGINE

====================================================================

Validate

Schema

Field Types

Required Fields

Currency

Dates

↓

IF Pass

↓

Router

IF Fail

↓

Human Review

====================================================================

LAYER 10 : DOCUMENT ROUTER

====================================================================

Invoice

↓

Purchase Order

↓

Payment Receipt

====================================================================

LAYER 11 : DATABASE UPDATE

====================================================================

Invoice Summary

Invoice Items

Purchase Order Summary

Purchase Order Items

Document Registry

====================================================================

LAYER 12 : AUDIT

====================================================================

Execution Log

↓

Workflow Log

↓

Audit Trail

↓

Metadata Store

====================================================================

LAYER 13 : ERROR HANDLING

====================================================================

Retry Queue

↓

Error Log

↓

Dead Letter Queue

====================================================================

LAYER 14 : NOTIFICATION

====================================================================

Telegram

↓

Email

↓

Admin Alert

====================================================================

LAYER 15 : ANALYTICS

====================================================================

Dashboard

↓

Statistics

↓

Processing Metrics

↓

Vendor Reports

↓

AI Accuracy

---

# 5. Architecture Lock Policy

This architecture is immutable.

The AI must never:

- Change the workflow order.
- Skip any layer.
- Merge unrelated layers.
- Remove duplicate detection.
- Move AI before Rule Engine.
- Use file names for classification.
- Update business tables before validation.
- Bypass Human Review.
- Modify the architecture without explicit user approval.

---

# 6. Locked Processing Order

The following execution order is mandatory:

Rule-Based Engine

↓

Duplicate Detection

↓

Airtable Registry Search

↓

Duplicate Decision

↓

Confidence Decision

↓

AI Fallback

↓

Human Review

↓

Business Rules

↓

Validation

↓

Database Update

↓

Audit

↓

Notification

↓

Dashboard

This order cannot be changed.

---

# 7. Locked Airtable Policy

The following Airtable tables already exist and are production-approved.

These tables are LOCKED.

The AI must never:

- Rename them
- Delete them
- Modify field names
- Modify field types
- Recreate them

Locked Tables

1. Invoice Summary

2. Invoice Items

3. Purchase Order Summary

4. Purchase Order Items

5. Document Registry

Any new Airtable table requires explicit user approval before implementation.

---

End of Section 1
