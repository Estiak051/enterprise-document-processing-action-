# 06-Metadata-Standard.md

# Enterprise Metadata Standard

Version

1.0

Status

Production Standard

Applies To

Entire Platform

---

# PURPOSE

This document defines the metadata standard used throughout the Enterprise Intelligent Document Processing Platform.

Every node must preserve metadata.

Every workflow must maintain metadata integrity.

Metadata is considered business-critical information.

No node may remove, overwrite, or destroy metadata.

---

# METADATA PHILOSOPHY

Metadata is the backbone of enterprise software.

It enables:

• Traceability

• Audit

• Monitoring

• Recovery

• Analytics

• Debugging

• Duplicate Detection

• Workflow Tracking

• AI Tracking

Every document must always carry its metadata from the beginning of the workflow until completion.

---

# METADATA LIFECYCLE

Gmail

↓

Attachment

↓

Text Extraction

↓

Normalization

↓

Classification

↓

Duplicate Detection

↓

AI

↓

Validation

↓

Database

↓

Audit

↓

Dashboard

↓

Archive

Metadata must survive every step.

---

# GLOBAL METADATA OBJECT

Every workflow item must contain the following metadata object.

metadata

executionId

workflowName

workflowVersion

workflowRunId

documentId

gmailMessageId

threadId

emailFrom

emailSubject

receivedTimestamp

attachmentName

attachmentExtension

attachmentMimeType

attachmentSize

originalFileHash

processingStatus

documentType

confidence

duplicateStatus

validationStatus

aiUsed

humanReviewRequired

createdAt

updatedAt

---

# REQUIRED METADATA FIELDS

These fields are mandatory.

Execution ID

Workflow Name

Workflow Version

Document ID

Processing Status

Document Type

Confidence

Duplicate Status

Created At

Updated At

No workflow may remove these fields.

---

####################################################################
SECTION A
WORKFLOW METADATA
####################################################################

Fields

Execution ID

Workflow Name

Workflow Version

Workflow Run ID

Current Layer

Current Node

Node Status

Start Time

End Time

Duration

Purpose

Track workflow execution.

---

####################################################################
SECTION B
EMAIL METADATA
####################################################################

Fields

Gmail Message ID

Thread ID

From

To

CC

BCC

Subject

Received Time

Attachment Count

Purpose

Maintain email traceability.

---

####################################################################
SECTION C
FILE METADATA
####################################################################

Fields

Original File Name

Original Extension

Original MIME Type

Original File Size

File Hash (SHA256)

Page Count

Document Language

Purpose

Track original attachment.

---

####################################################################
SECTION D
DOCUMENT METADATA
####################################################################

Fields

Document ID

Document Type

Invoice Number

PO Number

Receipt Number

Document Date

Supplier

Customer

Amount

Currency

Purpose

Identify the business document.

---

####################################################################
SECTION E
CLASSIFICATION METADATA
####################################################################

Fields

Rule Engine Used

Rule Confidence

Detected Elements

AI Used

AI Confidence

Classification Source

Classification Time

Purpose

Track classification history.

---

####################################################################
SECTION F
DUPLICATE METADATA
####################################################################

Fields

Composite Business Key

File Hash

Duplicate Status

Duplicate Reason

Original Document ID

Registry Search Time

Purpose

Support duplicate detection.

---

####################################################################
SECTION G
VALIDATION METADATA
####################################################################

Fields

Validation Status

Validation Time

Business Rules Passed

Schema Passed

Required Fields Passed

Validation Errors

Purpose

Track validation results.

---

####################################################################
SECTION H
HUMAN REVIEW METADATA
####################################################################

Fields

Review Required

Review Status

Reviewer

Review Time

Review Notes

Approval Status

Purpose

Track manual review.

---

####################################################################
SECTION I
DATABASE METADATA
####################################################################

Fields

Database Updated

Updated Tables

Updated Records

Database Timestamp

Database Status

Purpose

Track Airtable updates.

---

####################################################################
SECTION J
AUDIT METADATA
####################################################################

Fields

Audit ID

Execution ID

Workflow

Action

Node

Timestamp

Performed By

Purpose

Complete audit history.

---

####################################################################
SECTION K
ERROR METADATA
####################################################################

Fields

Error Code

Error Message

Node

Layer

Retry Count

Recovery Status

Purpose

Track failures.

---

####################################################################
SECTION L
NOTIFICATION METADATA
####################################################################

Fields

Notification Sent

Channel

Recipient

Timestamp

Status

Purpose

Track notifications.

---

# METADATA PRESERVATION RULES

The AI MUST NEVER:

Remove metadata

Rename metadata

Overwrite metadata

Delete metadata

Replace metadata

Only append new metadata.

---

# METADATA UPDATE POLICY

Every layer updates only its own metadata.

Example

Layer 4

Updates:

Document Type

Confidence

Layer 5

Updates:

Duplicate Status

Layer 6

Updates:

AI Used

AI Confidence

No layer may modify unrelated metadata.

---

# METADATA VERSIONING

Metadata Version

1.0

Future versions must remain backward compatible.

---

# REQUIRED METADATA VALIDATION

Before every Airtable update verify:

Execution ID exists

Document ID exists

Workflow Name exists

Processing Status exists

Document Type exists

Duplicate Status exists

Confidence exists

If any required metadata is missing,

STOP.

Do not continue.

---

# ENTERPRISE TRACEABILITY RULE

A document must be traceable from:

Gmail

↓

Attachment

↓

Extraction

↓

Classification

↓

Duplicate Detection

↓

Validation

↓

Database Update

↓

Audit

↓

Dashboard

Complete traceability is mandatory.

---

# PROHIBITED ACTIONS

Never delete metadata.

Never invent metadata.

Never generate fake IDs.

Never replace Execution IDs.

Never modify Gmail Message IDs.

Never remove File Hash.

Never remove Duplicate Key.

---

END OF SECTION 6
