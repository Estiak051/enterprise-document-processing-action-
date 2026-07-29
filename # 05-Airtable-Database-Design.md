# 05-Airtable-Database-Design.md

# Enterprise Airtable Database Design

Version

1.0

Status

Production Standard

Database Engine

Airtable

Database Policy

Single Source of Truth (SSOT)

---

# DATABASE DESIGN PRINCIPLES

The Airtable database is the primary business database.

Every workflow reads and writes from Airtable.

Google Sheets is NOT the master database.

No data may bypass Airtable.

Every record must be traceable.

Every update must be auditable.

Every document must preserve metadata.

---

# DATABASE LOCK POLICY

The following database structure is production-approved.

It is immutable.

The AI is NOT allowed to:

Rename tables

Delete tables

Rename fields

Delete fields

Change field types

Change relationships

Change primary fields

without explicit user approval.

---

# LOCKED TABLES

The following five tables already exist.

These are production tables.

They are LOCKED.

The AI must use them exactly as defined.

1.

Invoice Summary

Status

LOCKED

Modification

NOT ALLOWED

---

2.

Invoice Items

Status

LOCKED

Modification

NOT ALLOWED

---

3.

Purchase Order Summary

Status

LOCKED

Modification

NOT ALLOWED

---

4.

Purchase Order Items

Status

LOCKED

Modification

NOT ALLOWED

---

5.

Document Registry

Status

LOCKED

Modification

NOT ALLOWED

---

####################################################################
TABLE 1
Invoice Summary
####################################################################

Status

Existing

Locked

Purpose

Store one record per invoice.

Used By

WF-11 Database Update

Primary Key

Document ID

Fields

| Field Name | Airtable Type | Required | Purpose |
|------------|--------------|----------|----------|
| Document ID | Single line text | Yes | Unique document identifier |
| Invoice Number | Single line text | Yes | Invoice Number |
| Vendor Name | Single line text | Yes | Vendor |
| Vendor Email | Email | No | Vendor email |
| Vendor Address | Long text | No | Vendor address |
| Invoice Date | Date | Yes | Invoice date |
| Due Date | Date | No | Due date |
| Currency | Single Select | Yes | Currency |
| Sub Total | Currency | Yes | Invoice subtotal |
| Tax Amount | Currency | No | Tax amount |
| Total Amount | Currency | Yes | Invoice total |
| Payment Status | Single Select | Yes | Pending / Paid |
| Document Status | Single Select | Yes | Received / Processing / Completed |
| Composite Business Key | Single line text | Yes | Duplicate detection |
| Duplicate Status | Checkbox | Yes | Duplicate |
| Source Email ID | Single line text | No | Sender email |
| Gmail Message ID | Single line text | Yes | Gmail message |
| Execution ID | Single line text | Yes | Workflow execution |
| Workflow Name | Single line text | Yes | Workflow |
| Document URL | URL | No | Original document |
| Created Time | Created Time | Auto | Airtable |
| Updated Time | Last Modified Time | Auto | Airtable |
| Notes | Long text | No | Comments |

---

####################################################################
TABLE 2
Invoice Items
####################################################################

Status

Existing

Locked

Purpose

Store invoice line items.

Used By

Invoice Processor

Primary Key

Item ID

Fields

| Field Name | Airtable Type |
|------------|--------------|
| Item ID | Auto Number |
| Invoice Number | Link to Invoice Summary |
| Description | Long Text |
| SKU | Single Line Text |
| Category | Single Line Text |
| Quantity | Number |
| Unit Price | Currency |
| Tax Rate | Number |
| Tax Amount | Currency |
| Line Total | Currency |
| Created Time | Created Time |
| Notes | Long Text |

---

####################################################################
TABLE 3
Purchase Order Summary
####################################################################

Status

Existing

Locked

Purpose

Store purchase order header.

Primary Key

Document ID

Fields

(Use exactly the structure provided by the user.)

Document ID

PO Number

Supplier Name

Supplier Email

Buyer Name

PO Date

Delivery Date

Currency

Sub Total

Tax Amount

Grand Total

PO Status

Document Status

Composite Business Key

Duplicate Status

Source Email ID

Gmail Message ID

Execution ID

Workflow Name

Document URL

Created Time

Updated Time

Notes

---

####################################################################
TABLE 4
Purchase Order Items
####################################################################

Status

Existing

Locked

Purpose

Store purchase order line items.

Primary Key

PO Item ID

Fields

PO Item ID

Document ID

Execution ID

Composite Business Key

PO Number

Line Number

Item Description

Product Code

Quantity

Unit Of Measure

Unit Price

Line Total

Currency

Item Status

Confidence Score

Created Time

Updated Time

---

####################################################################
TABLE 5
Document Registry
####################################################################

Status

Existing

Locked

Purpose

Master registry of every processed document.

Primary Key

Document ID

Fields

Document ID

Document Type

Duplicate Key

Processing Status

Original File Name

File Hash

Invoice Number

PO Number

Receipt Number

Document Date

Supplier

Customer

Amount

Source Type

Execution ID

Created At

Purpose

Duplicate Detection

Audit

Workflow Tracking

---

####################################################################
NEW TABLE POLICY
####################################################################

The AI CANNOT create new tables automatically.

If a new table becomes necessary,

the AI must stop.

Explain:

Why the table is required.

How it will be used.

Which workflow will use it.

What fields are required.

What Airtable field types are required.

Only after explicit user approval may the table be created.

---

####################################################################
APPROVAL REQUIRED TABLES
####################################################################

The following tables are NOT created yet.

Status

Approval Required

The AI must NOT assume these tables exist.

Human Review Queue

Workflow Execution Log

Audit Trail

Error Log

Retry Queue

Notification Queue

AI Processing Log

Prompt Version History

Workflow Configuration

Vendor Master

Customer Master

---

####################################################################
DATABASE RELATIONSHIPS
####################################################################

Invoice Summary

↓

Invoice Items

Purchase Order Summary

↓

Purchase Order Items

Every Document

↓

Document Registry

Document Registry

↓

Duplicate Detection

Document Registry

↓

Audit

---

####################################################################
DATABASE RULES
####################################################################

Every document must exist in Document Registry.

Every Invoice must exist in Invoice Summary.

Every Invoice Item must belong to an Invoice.

Every PO Item must belong to a PO.

No orphan records.

No duplicate Composite Business Keys.

No duplicate File Hashes.

Validation required before update.

---

####################################################################
DATABASE IMPLEMENTATION ORDER
####################################################################

Step 1

Verify Locked Tables

↓

Step 2

Verify Field Names

↓

Step 3

Verify Field Types

↓

Step 4

Verify Relationships

↓

Step 5

Start Workflow

Never bypass these steps.

END OF SECTION 5
