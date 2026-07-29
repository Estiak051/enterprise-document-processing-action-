# 26-Workflow-Implementation-Targets.md

# Enterprise Workflow Implementation Targets

Version: 2.0

Status: LOCKED

Priority: CRITICAL

Architecture: Immutable

---

# PURPOSE

This document defines the official implementation contract for the Enterprise Intelligent Document Processing Platform.

Documents 01–25 define:

• WHAT must be built

This document defines:

• HOW implementation must be performed

• WHERE implementation begins

• WHEN implementation may continue

• WHAT the AI is allowed to modify

• WHAT the AI is forbidden to modify

This document overrides every default coding behavior of the AI.

The repository itself is the ONLY source of truth.

---

# IMPLEMENTATION CONTRACT

The AI is NOT allowed to redesign this project.

The AI is NOT allowed to simplify this project.

The AI is NOT allowed to optimize this project.

The AI is NOT allowed to replace technologies.

The AI is NOT allowed to introduce new architecture.

The AI is NOT allowed to remove workflow layers.

The AI is NOT allowed to merge workflows.

The AI is an IMPLEMENTATION ENGINE only.

---

# IMPLEMENTATION TARGET POLICY

IMPORTANT

This repository intentionally DOES NOT contain n8n workflow JSON files.

The workflow JSON files must be CREATED by the AI.

The AI must NEVER ask:

"Where should I implement?"

"Which workflow file should I modify?"

"Please upload workflow JSON."

Those questions are prohibited.

Instead,

the AI must CREATE the workflow JSON from scratch according to this repository.

Each generated workflow becomes the official implementation.

---

# WORKFLOW GENERATION POLICY

Each workflow must be generated independently.

Each workflow must become one independent n8n workflow.

Never merge workflows.

Never generate multiple workflows together.

Never create helper workflows.

Never create temporary workflows.

Never create experimental workflows.

---

# IMPLEMENTATION ORDER (LOCKED)

The following order is mandatory.

WF-01 Gmail Intake

↓

WF-02 Attachment Processor

↓

WF-03 OCR Processing

↓

WF-04 Rule-Based Classification

↓

WF-05 Duplicate Detection

↓

WF-06 AI Classification

↓

WF-07 Data Extraction

↓

WF-08 Line Item Extraction

↓

WF-09 Business Rules Engine

↓

WF-10 Validation Engine

↓

WF-11 Human Review

↓

WF-12 Database Update

↓

WF-13 Monitoring & Logging

↓

WF-14 Error Handling & Retry

↓

WF-15 Notifications

↓

WF-16 Analytics Dashboard

This order is LOCKED.

It cannot be changed.

---

# IMPLEMENTATION MODE

The AI must implement

ONE workflow only.

Never implement two workflows together.

After finishing ONE workflow,

STOP.

Wait for user approval.

Only after approval

may the AI begin the next workflow.

---

# OUTPUT REQUIREMENTS

For every workflow implementation the AI must produce

• Workflow JSON

• Node List

• Node Configuration

• Expressions

• Credentials Required

• Airtable Mapping

• Error Handling

• Testing Instructions

After that

STOP.

---

# IMPLEMENTATION BOUNDARIES

The AI may

✔ Create workflow JSON

✔ Configure nodes

✔ Configure expressions

✔ Configure routing

✔ Configure mappings

✔ Configure credentials placeholders

✔ Configure Airtable nodes

✔ Configure AI Agent nodes

✔ Configure validation

✔ Configure retry logic

✔ Configure monitoring

The AI may NOT

✘ Change architecture

✘ Rename workflows

✘ Rename Airtable tables

✘ Rename Airtable fields

✘ Change business rules

✘ Change metadata

✘ Change duplicate strategy

✘ Change AI fallback

✘ Change processing sequence

✘ Create additional tables

✘ Delete tables

✘ Skip workflow layers

---

# WORKFLOW TARGETS

====================================================

WF-01

====================================================

Workflow Name

WF-01 Gmail Intake

Purpose

Receive incoming Gmail messages.

Download attachments.

Extract email metadata.

Package attachments for downstream workflows.

Output

Attachment Package

Implementation

Create a NEW workflow JSON named

WF-01-Gmail-Intake.json

This file does not exist initially.

The AI must create it.

After completion,

STOP.

Wait for approval.

---

WF-02

Workflow Name

WF-02 Attachment Processor

Purpose

Identify

Digital PDF

Scanned PDF

Image

Implementation

Create

WF-02-Attachment-Processor.json

After completion,

STOP.

---

WF-03

Workflow Name

WF-03 OCR Processing

Purpose

OCR

Vision OCR

PDF Text Extraction

Unified Text

Implementation

Create

WF-03-OCR-Processing.json

STOP after completion.

---

WF-04

Workflow Name

WF-04 Rule-Based Classification

Purpose

Rule Engine

Document Classification

Confidence Score

Detected Elements

Implementation

Create

WF-04-Rule-Based-Classification.json

STOP after completion.

---

WF-05

Workflow Name

WF-05 Duplicate Detection

Purpose

Composite Business Key

SHA256

Registry Search

Duplicate Decision

Implementation

Create

WF-05-Duplicate-Detection.json

STOP after completion.

====================================================

WF-06

====================================================

Workflow Name

WF-06 AI Classification


Purpose

AI Fallback Engine

This workflow is ONLY executed when:

Rule-Based Engine confidence is below threshold

OR

Rule-Based Engine fails


AI Responsibilities:

- Document Classification
- Field Extraction
- Confidence Evaluation
- Missing Field Detection


AI Input:

Unified Document Text

OCR Result

Metadata Object


AI Output:

Structured Classification Object


Implementation

Create a NEW workflow JSON named:

WF-06-AI-Classification.json


After completion:

STOP.

Wait for approval.


---

====================================================

WF-07

====================================================

Workflow Name

WF-07 Data Extraction


Purpose

Extract structured business information.


Supported Documents:

Invoice

Purchase Order

Payment Receipt


Extraction Requirements:

Invoice:

- Invoice Number
- Vendor
- Customer
- Invoice Date
- Due Date
- Currency
- Amount
- Payment Status


Purchase Order:

- PO Number
- Supplier
- Buyer
- PO Date
- Delivery Date
- Amount


Payment Receipt:

- Receipt Number
- Customer
- Payment Date
- Amount
- Payment Method


Implementation

Create:

WF-07-Data-Extraction.json


After completion:

STOP.

Wait for approval.


---

====================================================

WF-08

====================================================

Workflow Name

WF-08 Line Item Extraction


Purpose

Extract document line items.


Invoice Items:

- Description
- SKU
- Category
- Quantity
- Unit Price
- Tax
- Line Total


Purchase Order Items:

- Item Description
- Product Code
- Quantity
- Unit
- Unit Price
- Line Total


Implementation

Create:

WF-08-Line-Item-Extraction.json


After completion:

STOP.

Wait for approval.


---

====================================================

WF-09

====================================================

Workflow Name

WF-09 Business Rules Engine


Purpose

Apply business validation rules.


Rules:

- Required document fields
- Vendor rules
- Customer rules
- Amount rules
- Duplicate business rules
- Document consistency rules


Output:

Business Validation Result


Implementation

Create:

WF-09-Business-Rules.json


After completion:

STOP.


---

====================================================

WF-10

====================================================

Workflow Name

WF-10 Validation Engine


Purpose

Technical and data validation.


Validate:

- Schema
- Field Type
- Required Fields
- Currency Format
- Date Format
- Amount Format


Decision:

PASS

or

FAIL


FAIL:

Send to Human Review


Implementation

Create:

WF-10-Validation-Engine.json


After completion:

STOP.


---

====================================================

WF-11

====================================================

Workflow Name

WF-11 Human Review


Purpose

Manual approval and correction process.


Human Review Required When:

- AI confidence is low
- Required fields missing
- Validation failed
- AI extraction failed
- Business rule failed


Human Review Actions:

- Approve
- Reject
- Correct Data


Store:

- Reviewer ID
- Review Time
- Review Status
- Correction Notes


Implementation

Create:

WF-11-Human-Review.json


After completion:

STOP.


---

====================================================

WF-12

====================================================

Workflow Name

WF-12 Database Update


Purpose

Update Airtable production tables.


Locked Tables:

1. Invoice Summary

2. Invoice Items

3. Purchase Order Summary

4. Purchase Order Items

5. Document Registry


Rules:

No database update before:

- Validation PASS
- Business Rules PASS
- Human Review PASS (if required)


Implementation

Create:

WF-12-Database-Update.json


After completion:

STOP.


---

====================================================

WF-13

====================================================

Workflow Name

WF-13 Monitoring & Logging


Purpose

Enterprise monitoring.


Track:

- Workflow Execution ID
- Processing Time
- Success Rate
- Failure Rate
- AI Usage
- Human Review Count
- Document Volume


Implementation

Create:

WF-13-Monitoring-Logging.json


After completion:

STOP.


---

====================================================

WF-14

====================================================

Workflow Name

WF-14 Error Handling & Retry


Purpose

Enterprise error recovery.


Features:

- Retry Queue
- Failed Document Queue
- Error Log
- Dead Letter Queue


Every error must store:

- Error Message
- Node Name
- Execution ID
- Timestamp
- Retry Count


Implementation

Create:

WF-14-Error-Handling-Retry.json


After completion:

STOP.


---

====================================================

WF-15

====================================================

Workflow Name

WF-15 Notifications


Purpose

Send system alerts.


Channels:

- Telegram
- Email


Notifications:

Success

Failure

Human Review Required

Duplicate Found

System Error


Implementation

Create:

WF-15-Notifications.json


After completion:

STOP.


---

====================================================

WF-16

====================================================

Workflow Name

WF-16 Analytics Dashboard


Purpose

Enterprise reporting.


Metrics:

Document Count

Processing Time

Success Rate

Failure Rate

Duplicate Rate

AI Usage Rate

Human Review Rate

Vendor Statistics

Document Type Statistics


Implementation

Create:

WF-16-Analytics-Dashboard.json


After completion:

STOP.


####################################################################
AI IMPLEMENTATION PROTOCOL
####################################################################


The AI must follow this exact execution protocol.


STEP 1

Read repository.


STEP 2

Identify current workflow.


STEP 3

Create ONLY that workflow.


STEP 4

Test workflow logic.


STEP 5

Provide implementation output.


STEP 6

STOP.


Never continue automatically.


####################################################################
LAYER COMPLETION RULE
####################################################################


A workflow is considered complete only when:


1. Nodes created.

2. Configuration completed.

3. Expressions completed.

4. Airtable mapping completed.

5. Error handling added.

6. Testing instructions provided.


Only then can the workflow be marked completed.


####################################################################
APPROVAL GATE
####################################################################


The AI must wait for explicit user approval.


Valid approval examples:

"Approved"

"Continue"

"Next Workflow"


Without approval:

DO NOT continue.


####################################################################
AIRTABLE POLICY
####################################################################


The AI must use existing Airtable tables.


Locked tables:


Invoice Summary

Invoice Items

Purchase Order Summary

Purchase Order Items

Document Registry


The AI cannot:

- Rename fields
- Delete fields
- Change types
- Create duplicate tables


Any new table requires explicit approval.


####################################################################
FINAL IMPLEMENTATION CONTRACT
####################################################################


This repository defines the complete architecture.


The AI is an implementation assistant only.


The AI must:

Follow documents 01-26.

Follow workflow order.

Create one workflow at a time.

Stop after each workflow.

Wait for approval.


The AI must never:

Redesign.

Simplify.

Skip.

Merge.

Invent.


END OF DOCUMENT
