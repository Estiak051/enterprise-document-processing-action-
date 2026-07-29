# 19-Enterprise-Coding-Standards.md

# Enterprise Coding Standards

Version

1.0

Status

Production Standard

Priority

Critical

Applies To

All Code Nodes

All JavaScript

All Expressions

All Utility Functions

Entire Intelligent Document Processing Platform

---

# PURPOSE

This document defines the enterprise coding standards for the entire Intelligent Document Processing Platform.

Every Code Node, JavaScript function, expression, utility, and transformation logic must follow this document.

The objective is to ensure

• Readability

• Maintainability

• Reusability

• Performance

• Scalability

• Security

• Auditability

---

# CODING PHILOSOPHY

Every line of code should have a purpose.

Code should be understandable six months later.

Code should be reusable.

Code should never depend on hidden assumptions.

Business logic must remain deterministic.

---

####################################################################
GENERAL PRINCIPLES
####################################################################

Code must be

Readable

Simple

Modular

Reusable

Documented

Versioned

Auditable

Never write code just because it works.

Write code that another developer can understand.

---

####################################################################
SUPPORTED LANGUAGE
####################################################################

Primary

JavaScript (ECMAScript)

Used in

n8n Code Node

Code Transformations

Business Rules

Metadata Processing

Utility Functions

Expression Helpers

---

####################################################################
CODE NODE HEADER STANDARD
####################################################################

Every Code Node must begin with

Purpose

Input

Output

Dependencies

Author

Version

Example

/*
Node Name:
Generate Duplicate Key

Purpose:
Generate Composite Business Key

Input:
Normalized Document

Output:
duplicateKey

Version:
1.0
*/

---

####################################################################
NODE NAMING STANDARD
####################################################################

Bad

Code

Code1

Function

Script

Good

Generate Duplicate Key

Normalize Invoice Data

Validate Business Rules

Generate Metadata

Merge OCR Results

---

####################################################################
VARIABLE NAMING
####################################################################

Use

camelCase

Examples

invoiceNumber

vendorName

workflowVersion

documentId

duplicateKey

executionId

processingStatus

Avoid

a

b

temp

test

abc

value1

---

####################################################################
CONSTANT NAMING
####################################################################

Use

UPPER_CASE

Example

MAX_RETRY

DEFAULT_CONFIDENCE

MIN_AI_THRESHOLD

SUPPORTED_DOCUMENT_TYPES

---

####################################################################
FUNCTION STANDARD
####################################################################

Functions must

Do one thing only.

Example

generateDuplicateKey()

normalizeDate()

calculateTax()

validateInvoice()

Never create giant functions.

---

####################################################################
FUNCTION LENGTH
####################################################################

Recommended

Less than 50 lines

Split larger functions.

---

####################################################################
COMMENT STANDARD
####################################################################

Comment only

Business logic

Complex algorithms

Validation rules

Never comment obvious code.

---

####################################################################
ERROR HANDLING
####################################################################

Every Code Node must

Validate input

Handle missing fields

Handle NULL

Handle undefined

Return meaningful errors

Never crash unexpectedly.

---

####################################################################
NULL HANDLING
####################################################################

Always check

undefined

null

empty string

missing arrays

missing objects

Example

if (!invoiceNumber)

Never assume data exists.

---

####################################################################
RETURN STANDARD
####################################################################

Every Code Node returns

json

Never return

Random objects

Unexpected arrays

Invalid JSON

Structure must remain predictable.

---

####################################################################
METADATA PRESERVATION
####################################################################

Every Code Node must preserve

Execution ID

Workflow Version

Workflow Name

Document ID

Duplicate Key

Confidence

File Hash

Processing Status

Never remove metadata.

---

####################################################################
IMMUTABILITY
####################################################################

Avoid modifying original objects.

Preferred

Create new object

Return new object

Avoid

Mutating input directly

---

####################################################################
BUSINESS LOGIC
####################################################################

Business logic belongs

Inside dedicated Code Nodes

Never hide business rules inside expressions.

---

####################################################################
EXPRESSION STANDARD
####################################################################

Expressions should remain simple.

If expression becomes difficult

↓

Move logic to Code Node.

---

####################################################################
HARDCODE POLICY
####################################################################

Never hardcode

API Keys

Credentials

IDs

Table Names

Thresholds

Business Values

Use configuration instead.

---

####################################################################
CONFIGURATION STANDARD
####################################################################

Read values from

Configuration Table

Environment Variables

Workflow Configuration

Never duplicate configuration.

---

####################################################################
DATE STANDARD
####################################################################

Store

ISO-8601

Example

2026-07-28T14:15:20Z

Never use ambiguous date formats.

---

####################################################################
CURRENCY STANDARD
####################################################################

Always preserve original currency.

Never convert automatically.

Store

Currency

Amount

Sub Total

Tax

Grand Total

Separately.

---

####################################################################
PERFORMANCE STANDARD
####################################################################

Avoid

Nested loops

Repeated database lookups

Duplicate calculations

Repeated AI calls

Optimize for large document volumes.

---

####################################################################
REUSABILITY
####################################################################

Common logic should exist only once.

Examples

Duplicate Key

Normalize Date

Normalize Amount

Hash Generator

Validation

Reuse everywhere.

---

####################################################################
SECURITY STANDARD
####################################################################

Never log

API Keys

Passwords

OAuth Tokens

Secrets

Personally sensitive information

Never expose credentials.

---

####################################################################
AUDIT STANDARD
####################################################################

Every important business calculation should be traceable.

Store

Execution ID

Timestamp

Node Name

Business Result

---

####################################################################
TESTING STANDARD
####################################################################

Every Code Node must be tested with

Valid Input

Invalid Input

Missing Fields

NULL Values

Duplicate Documents

Unknown Documents

Unexpected Arrays

Large Data

---

####################################################################
VERSIONING
####################################################################

Every important code change requires

Version Update

Documentation

Testing

Approval

Deployment

---

####################################################################
PROHIBITED ACTIONS
####################################################################

Never write undocumented code.

Never remove metadata.

Never hardcode secrets.

Never bypass validation.

Never mutate input unexpectedly.

Never hide business rules inside expressions.

Never create giant Code Nodes.

Never return inconsistent structures.

---

####################################################################
SUCCESS CRITERIA
####################################################################

All code is

Readable

Reusable

Maintainable

Secure

Auditable

Version Controlled

Enterprise Ready

Production Ready

---

END OF SECTION 19
