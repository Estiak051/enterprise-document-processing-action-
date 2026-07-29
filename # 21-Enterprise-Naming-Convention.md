# 21-Enterprise-Naming-Convention.md

# Enterprise Naming Convention

Version

1.0

Status

Production Standard

Priority

Critical

Applies To

Entire Intelligent Document Processing Platform

---

# PURPOSE

This document defines the official naming convention for every component of the Intelligent Document Processing Platform.

Every workflow, node, Airtable table, field, prompt, AI agent, log, configuration, dashboard, version, and document must follow this standard.

Consistent naming ensures

• Readability

• Maintainability

• Scalability

• Team Collaboration

• Auditability

---

# NAMING PHILOSOPHY

Every name should immediately describe

What it is

What it does

Where it belongs

Never use meaningless names.

Examples

❌ Code

❌ Test

❌ Merge1

❌ Node

✔ Generate Duplicate Key

✔ Validate Invoice

✔ Route Document Type

✔ Update Invoice Summary

---

####################################################################
GENERAL RULES
####################################################################

Use English only.

Use descriptive names.

Avoid abbreviations unless officially defined.

Never use spaces in IDs.

Use Title Case for node names.

Use PascalCase for class names.

Use camelCase for variables.

Use snake_case only when required by external APIs.

---

####################################################################
WORKFLOW NAMING
####################################################################

Format

WF-XX Workflow Name

Examples

WF-01 Gmail Intake

WF-02 Attachment Processor

WF-03 Duplicate Detection

WF-04 OCR Processing

WF-05 AI Classification

WF-06 Data Extraction

WF-07 Validation Engine

WF-08 Human Review

WF-09 Database Update

WF-10 Monitoring & Logging

WF-11 Error Handling

WF-12 Notifications

WF-13 Dashboard

WF-14 Analytics

WF-15 Archive Manager

Workflow names must never change after production deployment.

---

####################################################################
NODE NAMING
####################################################################

Format

<Action> + <Object>

Examples

Download Attachments

Extract PDF Text

Normalize Document

Generate Duplicate Key

Search Document Registry

Validate Invoice

Create Invoice Summary

Update Purchase Order

Route Document Type

Create Audit Log

Never leave default names.

---

####################################################################
NODE PREFIXES
####################################################################

TRG

Trigger

OCR

OCR

AI

AI Agent

DB

Database

VAL

Validation

MERGE

Merge

SW

Switch

IF

Decision

CFG

Configuration

LOG

Logging

UTIL

Utility

Examples

TRG Gmail Trigger

OCR Extract PDF

AI Classify Document

DB Create Invoice Summary

VAL Business Validation

LOG Audit Logger

---

####################################################################
AIRTABLE TABLE NAMING
####################################################################

Existing tables (LOCKED)

Invoice Summary

Invoice Items

Purchase Order Summary

Purchase Order Items

Document Registry

Future tables

Human Review Queue

Audit Log

Workflow Execution Log

Error Log

Notification Queue

Configuration

Dashboard Metrics

AI Prompt Registry

AI Execution Log

System Settings

Never rename production tables.

---

####################################################################
AIRTABLE FIELD NAMING
####################################################################

Rules

Title Case

Meaningful

Business Friendly

Examples

Invoice Number

Vendor Name

Document ID

Execution ID

Workflow Name

Duplicate Status

Composite Business Key

Confidence Score

Never use

Field1

ColumnA

Test

Temp

---

####################################################################
PROMPT NAMING
####################################################################

Format

PR-XXX Prompt Name

Examples

PR-001 Rule Classification

PR-002 AI Classification

PR-003 Invoice Extraction

PR-004 Purchase Order Extraction

PR-005 Validation

PR-006 Human Review

PR-007 Dashboard Summary

PR-008 Notification Generator

Prompt names never change.

Only versions change.

---

####################################################################
AI AGENT NAMING
####################################################################

Examples

Document Classification Agent

Invoice Extraction Agent

Purchase Order Agent

Validation Agent

Human Review Assistant

Analytics Agent

Never

Agent1

AI Test

GPT Node

---

####################################################################
CONFIGURATION NAMING
####################################################################

Examples

OCR Provider

AI Provider

Confidence Threshold

Duplicate Threshold

Maximum Retry

Workflow Version

Environment

Default Currency

Timezone

---

####################################################################
ENVIRONMENT NAMING
####################################################################

Development

Testing

Staging

Production

Never create custom environment names.

---

####################################################################
VERSION NAMING
####################################################################

Major.Minor.Patch

Examples

1.0.0

1.1.0

1.1.1

2.0.0

Never skip versions.

---

####################################################################
DOCUMENT NAMING
####################################################################

Examples

01-Complete-Architecture-Diagram.md

02-Master-System-Prompt.md

03-AI-Working-Protocol.md

...

25-Enterprise-Master-Blueprint.md

Numbering is permanent.

Never rename released documents.

---

####################################################################
GITHUB COMMIT NAMING
####################################################################

Format

TYPE: Description

Examples

FEATURE: Added AI Fallback

FIX: Duplicate Detection

UPDATE: Airtable Schema

DOCS: Monitoring Guide

REFACTOR: Validation Engine

TEST: OCR Improvements

---

####################################################################
RELEASE NAMING
####################################################################

Examples

Release v1.0

Release v1.1

Release v2.0

Never use

Final

Latest

New

---

####################################################################
LOG NAMING
####################################################################

Examples

Workflow Execution Log

Audit Log

AI Execution Log

Error Log

Notification Log

Human Review Log

---

####################################################################
DASHBOARD NAMING
####################################################################

Examples

Executive Dashboard

Workflow Dashboard

AI Dashboard

OCR Dashboard

Business Dashboard

Operations Dashboard

Audit Dashboard

---

####################################################################
FILE NAMING
####################################################################

Documentation

01-Architecture.md

02-System-Prompt.md

Workflow JSON

WF-01-Gmail-Intake.json

WF-02-Attachment-Processor.json

Prompt Files

PR-001-Classification.md

PR-002-Extraction.md

---

####################################################################
PROHIBITED NAMES
####################################################################

Never use

Test

Demo

Copy

Copy 2

Node1

Code

Temp

Sample

Example

Dummy

Final Final

New Workflow

Workflow Copy

---

####################################################################
SUCCESS CRITERIA
####################################################################

Every project component has

A unique name

A meaningful name

A consistent format

A version

A documented purpose

The entire platform remains readable, scalable, and enterprise compliant.

---

END OF SECTION 21
