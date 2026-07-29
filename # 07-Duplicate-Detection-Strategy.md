# 07-Duplicate-Detection-Strategy.md

# Enterprise Duplicate Detection Strategy

Version

1.0

Status

Production Standard

Priority

Critical

Execution Order

Rule Engine
↓

Duplicate Detection
↓

Confidence Check
↓

AI Fallback

Never change this order.

---

# PURPOSE

Prevent duplicate processing.

Prevent duplicate database records.

Prevent duplicate API calls.

Prevent duplicate business transactions.

Every document must pass Duplicate Detection before entering AI.

---

# DUPLICATE DETECTION PRINCIPLES

Duplicate detection must NEVER use:

❌ File Name

❌ Attachment Name

❌ Email Subject

❌ Gmail Thread

❌ Attachment Extension

Duplicate detection must ALWAYS use:

✓ Document Content

✓ Extracted Text

✓ OCR Text

✓ Rule Engine Output

✓ File Hash

✓ Composite Business Key

---

# DUPLICATE DETECTION PIPELINE

Document Text

↓

Rule Based Classification

↓

Field Extraction

↓

Composite Business Key Generation

↓

File Hash Generation

↓

Search Document Registry

↓

Duplicate Decision

↓

Continue OR Stop

---

####################################################################
LEVEL 1
DOCUMENT CONTENT IDENTIFICATION
####################################################################

Purpose

Identify the document using its content.

Source

Digital PDF Text

OCR Text

Vision OCR

Never use filename.

---

####################################################################
LEVEL 2
COMPOSITE BUSINESS KEY
####################################################################

Purpose

Identify business duplicates.

Rule

Invoice

Invoice Number

+

Supplier

+

Invoice Date

+

Total Amount

Purchase Order

PO Number

+

Supplier

+

PO Date

+

Grand Total

Payment Receipt

Receipt Number

+

Amount

+

Supplier

+

Receipt Date

Example

Invoice

INV-2026-1003

↓

Digital Edge Solutions

↓

2026-06-05

↓

47000

Composite Key

INV-2026-1003|digital edge solutions|2026-06-05|47000

Store

Document Registry

Field

Duplicate Key

---

####################################################################
LEVEL 3
FILE HASH
####################################################################

Purpose

Detect identical files.

Algorithm

SHA-256

Generate

Immediately after download.

Store

Document Registry

Field

File Hash

Example

A81C9D...

Never regenerate after processing.

---

####################################################################
LEVEL 4
AIRTABLE SEARCH
####################################################################

Search Table

Document Registry

Search Priority

1

File Hash

↓

2

Duplicate Key

↓

3

Document Type

↓

4

Processing Status

Rules

If File Hash exists

Duplicate

If Duplicate Key exists

Duplicate

Otherwise

Continue

---

####################################################################
LEVEL 5
DUPLICATE DECISION MATRIX
####################################################################

| File Hash | Duplicate Key | Decision |
|------------|---------------|----------|
| Match | Match | Duplicate |
| Match | No Match | Duplicate |
| No Match | Match | Duplicate |
| No Match | No Match | Continue |

---

####################################################################
LEVEL 6
DUPLICATE ACTIONS
####################################################################

If Duplicate

Update Registry

Processing Status

Duplicate

Duplicate Status

True

Duplicate Reason

File Hash Match

or

Business Key Match

Workflow

Stop

No AI

No OCR Retry

No Database Update

No Notification

---

####################################################################
LEVEL 7
NON-DUPLICATE ACTIONS
####################################################################

Update Registry

Processing Status

Processing

Continue

↓

Confidence Check

↓

AI if needed

---

####################################################################
LEVEL 8
FALSE POSITIVE POLICY
####################################################################

If duplicate is suspected but:

Amounts differ

Supplier differs

Document Date differs

Invoice Number differs

Do NOT mark duplicate automatically.

Send to Human Review.

---

####################################################################
LEVEL 9
FALSE NEGATIVE POLICY
####################################################################

If AI later detects

Same invoice

Different OCR

Different formatting

Generate Review Flag

Human Review

---

####################################################################
LEVEL 10
REPROCESSING RULE
####################################################################

Documents marked

Duplicate

cannot be reprocessed automatically.

Reprocessing requires:

Manual approval

OR

Registry reset

---

####################################################################
LEVEL 11
DOCUMENT REGISTRY UPDATE
####################################################################

When duplicate detected update:

Duplicate Status

Duplicate Reason

Duplicate Timestamp

Execution ID

Workflow Name

Processing Status

Last Checked

---

####################################################################
LEVEL 12
API OPTIMIZATION
####################################################################

Duplicate Detection

MUST happen

BEFORE

AI

BEFORE

OpenAI

BEFORE

Vision

BEFORE

Database Update

Reason

Reduce API Cost

Reduce Runtime

Reduce Airtable Writes

---

####################################################################
LEVEL 13
WORKFLOW POSITION
####################################################################

Correct Order

Gmail

↓

Attachment

↓

Text Extraction

↓

Normalization

↓

Rule Engine

↓

Duplicate Detection

↓

Confidence Check

↓

AI Fallback

↓

Validation

↓

Business Rules

↓

Database Update

Wrong

AI

↓

Duplicate Detection

Never allowed.

---

####################################################################
LEVEL 14
HUMAN REVIEW CONDITIONS
####################################################################

Send to Human Review if:

Duplicate confidence uncertain

Partial duplicate

Missing Invoice Number

Conflicting Amount

Multiple Suppliers

Unreadable OCR

---

####################################################################
LEVEL 15
SUCCESS CRITERIA
####################################################################

Duplicate documents

Never reach AI.

Duplicate documents

Never update business tables.

Duplicate documents

Always update Document Registry.

Duplicate detection

Must finish in under 1 second for normal registry sizes.

---

# PROHIBITED ACTIONS

Never use filename.

Never use attachment name.

Never bypass registry.

Never skip file hash.

Never skip composite key.

Never call AI before duplicate detection.

Never update Invoice Summary before duplicate detection.

Never update Purchase Order Summary before duplicate detection.

Never update Payment tables before duplicate detection.

END OF SECTION 7
