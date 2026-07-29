# 18-Enterprise-AI-Prompt-Engineering-Standards.md

# Enterprise AI Prompt Engineering Standards

Version

1.0

Status

Production Standard

Priority

Critical

Applies To

All AI Agents

All LLM Providers

OpenAI

Claude

Gemini

Grok

Future Models

---

# PURPOSE

This document defines the enterprise prompt engineering standards for the Intelligent Document Processing Platform.

Every AI prompt used in this project must comply with this document.

This document applies to

System Prompts

User Prompts

Developer Prompts

Extraction Prompts

Classification Prompts

Validation Prompts

Future AI Agents

---

# PROMPT ENGINEERING PHILOSOPHY

AI must never guess.

AI must never hallucinate.

AI must always follow deterministic business rules.

AI exists to assist the workflow.

AI does not replace business logic.

Rule Engine always executes first.

Prompt Engineering exists only for intelligent fallback.

---

####################################################################
PROMPT EXECUTION HIERARCHY
####################################################################

Business Rules

↓

Rule-Based Engine

↓

Duplicate Detection

↓

Confidence Check

↓

AI Prompt

↓

Validation

↓

Human Review

---

AI must NEVER execute before

Rule Engine

Duplicate Detection

---

####################################################################
PROMPT TYPES
####################################################################

The platform supports the following prompt categories.

SYS

System Prompt

DEV

Developer Prompt

USR

User Prompt

CLS

Classification Prompt

EXT

Extraction Prompt

VAL

Validation Prompt

REV

Review Prompt

RPT

Reporting Prompt

---

####################################################################
SYSTEM PROMPT STANDARD
####################################################################

Every System Prompt must define

Purpose

Scope

Restrictions

Output Format

Business Rules

Allowed Behaviour

Forbidden Behaviour

Confidence Rules

Validation Rules

Human Review Rules

System prompts are immutable unless versioned.

---

####################################################################
DEVELOPER PROMPT STANDARD
####################################################################

Developer prompts define

Workflow context

Architecture rules

Available metadata

JSON schema

Expected output

Developer prompts must never contain business secrets.

---

####################################################################
USER PROMPT STANDARD
####################################################################

User prompts should contain only

Document content

OCR text

Business request

Never include

Internal metadata

API Keys

Database IDs

Workflow secrets

---

####################################################################
CLASSIFICATION PROMPT STANDARD
####################################################################

Classification prompts determine

Document Type

Confidence

Detected Elements

Business Reason

Allowed document types

Invoice

Purchase Order

Payment Receipt

Unknown

Classification must NEVER depend on

Filename

Attachment Name

Email Subject

Folder Name

Only document content.

---

####################################################################
EXTRACTION PROMPT STANDARD
####################################################################

Extraction prompts extract

Invoice Number

Supplier

Customer

Amounts

Dates

Line Items

Payment Information

Never invent values.

If unavailable

Return NULL.

---

####################################################################
VALIDATION PROMPT STANDARD
####################################################################

Validation prompts verify

Business completeness

Field consistency

Date consistency

Currency consistency

Arithmetic consistency

Duplicate indicators

Never modify extracted values.

Only validate.

---

####################################################################
OUTPUT FORMAT STANDARD
####################################################################

Every AI response must use structured JSON.

No markdown.

No explanation.

No commentary.

No natural language.

Only valid JSON.

---

####################################################################
JSON SCHEMA RULES
####################################################################

Every output must

Match schema

Contain required fields

Contain proper data types

Contain confidence

Contain reasoning

Missing values must be NULL.

Never fabricate values.

---

####################################################################
CONFIDENCE STANDARD
####################################################################

Confidence Range

0

↓

100

Recommended

95+

Very High

90+

High

80+

Medium

Below Threshold

↓

Human Review

Confidence must be based on

Document content only.

---

####################################################################
HALLUCINATION POLICY
####################################################################

The AI must NEVER

Guess invoice numbers

Guess supplier names

Guess dates

Guess totals

Guess line items

Guess currencies

If uncertain

Return NULL

Lower confidence

---

####################################################################
TOKEN OPTIMIZATION
####################################################################

Keep prompts concise.

Avoid duplicate instructions.

Avoid unnecessary examples.

Reuse shared context.

Minimize token usage without reducing accuracy.

---

####################################################################
PROMPT VERSIONING
####################################################################

Every prompt must include

Prompt Name

Prompt Version

Created Date

Modified Date

Author

Purpose

Change Log

Example

CLS-001

Version

1.2

---

####################################################################
PROMPT TESTING
####################################################################

Every prompt must be tested against

Invoice

Purchase Order

Payment Receipt

Scanned PDF

Digital PDF

Image

Blank Document

Corrupted Document

Unknown Document

Before production release.

---

####################################################################
PROMPT CHANGE POLICY
####################################################################

Changing a prompt requires

Version increment

Testing

Approval

Documentation update

Git commit

Deployment

Never overwrite prompt versions.

---

####################################################################
MULTI-MODEL COMPATIBILITY
####################################################################

Prompts must remain compatible with

OpenAI

Claude

Gemini

Grok

Future enterprise LLMs

Avoid provider-specific assumptions.

---

####################################################################
SECURITY POLICY
####################################################################

Never expose

API Keys

Credentials

OAuth Tokens

Environment Variables

Internal Database IDs

Internal Airtable URLs

Prompt secrets

---

####################################################################
PROMPT AUDIT
####################################################################

Every AI execution must store

Prompt Name

Prompt Version

Model

Temperature

Tokens

Latency

Execution ID

Workflow

Confidence

---

####################################################################
PROHIBITED ACTIONS
####################################################################

Never classify using filename.

Never bypass Rule Engine.

Never bypass Duplicate Detection.

Never output invalid JSON.

Never fabricate business values.

Never skip confidence scoring.

Never modify business rules.

Never update Airtable directly.

Never expose internal prompts.

---

####################################################################
SUCCESS CRITERIA
####################################################################

Every prompt is

Deterministic

Version Controlled

Auditable

Reusable

Scalable

LLM Independent

Enterprise Ready

Rule Engine Compatible

Human Review Compatible

Production Ready

---

END OF SECTION 18
