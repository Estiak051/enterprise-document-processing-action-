# 17-n8n-Development-Standards.md

# Enterprise n8n Development Standards

Version

1.0

Status

Production Standard

Priority

Critical

Applies To

All n8n Workflows

---

# PURPOSE

This document defines the mandatory development standards for all n8n workflows in this project.

Every workflow must follow these standards.

No workflow may violate this document.

---

# DEVELOPMENT PRINCIPLES

Every workflow must be

✔ Readable

✔ Maintainable

✔ Modular

✔ Reusable

✔ Scalable

✔ Auditable

✔ Easy to Debug

✔ Easy to Upgrade

---

# NODE NAMING STANDARD

Every node must have a descriptive name.

Never keep default names.

❌ Code

✔ Generate Duplicate Key

❌ IF

✔ Check Duplicate Document

❌ Merge

✔ Merge OCR Results

❌ Switch

✔ Route Document Type

---

# NODE PREFIX STANDARD

Use prefixes.

TRG

Trigger

ACT

Action

VAL

Validation

DB

Database

AI

AI Agent

OCR

OCR

MERGE

Merge

IF

Decision

SW

Switch

LOG

Logging

CFG

Configuration

UTIL

Utility

---

Examples

TRG Gmail Trigger

OCR Extract PDF Text

OCR Vision OCR

AI Document Classifier

VAL Business Validation

DB Create Invoice Summary

DB Search Document Registry

LOG Audit Logger

---

# WORKFLOW NAMING STANDARD

WF-01 Gmail Intake

WF-02 Attachment Processor

WF-03 Duplicate Detection

WF-04 AI Classification

WF-05 OCR

WF-06 Extraction

WF-07 Validation

WF-08 Human Review

WF-09 Database Update

---

# CODE NODE STANDARD

Every Code Node must contain

Purpose

Input

Output

Comments

Error Handling

Example

/*
Purpose:
Generate Composite Business Key

Input:
Normalized Document

Output:
duplicateKey
*/

---

# IF NODE STANDARD

Every IF node must answer ONE question only.

✔ Is Duplicate?

✔ Confidence High?

✔ AI Required?

Never combine multiple business decisions into one IF.

---

# SWITCH NODE STANDARD

Switch nodes only for routing.

Examples

Document Type

Workflow Type

Language

Never use Switch for validation.

---

# MERGE NODE STANDARD

Merge only related data.

Examples

OCR Results

Metadata

AI Output

Never merge unrelated business objects.

---

# EXPRESSION STANDARD

Expressions must be readable.

Avoid nested expressions longer than necessary.

Use Code Node if expression becomes complex.

---

# METADATA RULE

Every workflow must preserve

Execution ID

Workflow Version

Workflow Name

Document ID

Processing Status

Confidence

Duplicate Key

File Hash

These values must never be lost.

---

# ERROR HANDLING

Every external node

must have retry strategy.

Every validation

must stop invalid data.

---

# AI NODE STANDARD

Every AI node must include

System Prompt Version

Prompt Name

Model Name

Temperature

Output Schema

Confidence

---

# DATABASE NODE STANDARD

Database nodes

must never hardcode values.

Use mapped fields only.

---

# COMMENT STANDARD

Every major workflow section must contain a Note node explaining

Purpose

Inputs

Outputs

Dependencies

---

# REUSABILITY

Business logic should be isolated.

Avoid duplicating Code Nodes.

Reuse logic whenever possible.

---

# PERFORMANCE

Avoid unnecessary Merge nodes.

Avoid unnecessary Code nodes.

Avoid unnecessary AI calls.

Prefer Rule Engine whenever possible.

---

# PROHIBITED ACTIONS

Never leave default node names.

Never hardcode IDs.

Never use undocumented expressions.

Never remove metadata.

Never bypass validation.

Never bypass duplicate detection.

Never update Airtable directly from AI.

---

# SUCCESS CRITERIA

Every workflow is

Easy to read

Easy to maintain

Easy to debug

Easy to scale

Enterprise compliant.

END OF SECTION 17
