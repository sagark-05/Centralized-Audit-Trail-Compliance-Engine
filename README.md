# Centralized Audit Trail Compliance Engine

## Project Overview

The **Centralized Audit Trail Compliance Engine** is a compliance logging platform designed to securely ingest, process, store, search, and export enterprise application audit logs.

The system focuses on protecting sensitive information and maintaining the integrity of audit records. It identifies Personally Identifiable Information (PII), such as Social Security Numbers and credit card numbers, masks the sensitive fields before persistence, and generates cryptographic SHA-256 hashes for integrity verification.

The system is intended for use by **Compliance Officers** and **Security Auditors** who need reliable and verifiable audit evidence.

---

## Problem Statement

Enterprise applications generate large volumes of audit logs containing information about user activities, transactions, and system events. These logs may contain sensitive PII and must be protected from unauthorized exposure or modification.

The proposed system provides a centralized mechanism to:

- Ingest structured JSON audit logs
- Validate incoming audit records
- Detect sensitive PII fields
- Mask PII before storing audit records
- Generate SHA-256 integrity hashes
- Securely store audit records
- Search and filter historical audit logs
- Generate compliance-ready audit exports
- Verify the integrity of stored audit records

---

## Target Stakeholders / Actors

### 1. Enterprise Application

External applications that submit structured JSON audit logs to the compliance engine.

### 2. Compliance Officer

Uses the system to search audit records and generate compliance-related audit exports.

### 3. Security Auditor

Uses the system to investigate audit records, generate audit evidence, and verify record integrity.

---

## Key Functionalities

The system provides the following major functionalities:

1. **Audit Log Ingestion**
   - Accepts structured JSON audit logs from registered applications.

2. **Audit Log Validation**
   - Validates JSON structure and mandatory audit fields.

3. **PII Detection and Masking**
   - Identifies sensitive information such as credit card numbers and Social Security Numbers.
   - Masks detected PII before persistence.

4. **SHA-256 Integrity Hashing**
   - Generates a cryptographic SHA-256 hash for every masked audit record.
   - Enables detection of unauthorized modifications.

5. **Audit Log Search and Filtering**
   - Allows authorized users to search historical audit records using attributes such as:
     - Timestamp
     - Application
     - User
     - Event type
     - Severity

6. **Audit Export**
   - Generates exports containing selected masked audit records and their integrity hashes.

7. **Integrity Verification**
   - Allows Security Auditors to verify whether stored audit records have been modified.

---

## Lab 1 – Requirements Engineering & UML Use-Case Modelling

This repository contains the deliverables for **Lab 1: Requirements Engineering & UML Use-Case Modelling**.

The objective of this lab is to:

- Identify system requirements
- Define Functional Requirements (FRs)
- Define Non-Functional Requirements (NFRs)
- Identify system actors
- Identify system use cases
- Model system behavior using UML Use-Case diagrams
- Document a detailed use-case flow

---

## Requirements Summary

### Functional Requirements

- **FR-001:** Parse JSON audit logs and detect and mask PII before persistence.
- **FR-002:** Accept and validate structured JSON audit logs.
- **FR-003:** Generate SHA-256 integrity hashes for masked audit records.
- **FR-004:** Provide authorized audit log search and filtering.
- **FR-005:** Generate audit exports containing masked records and integrity hashes.

### Non-Functional Requirements

- **NFR-001:** Support complex filtering across 10 million historical records in under 1 second.
- **NFR-002:** Ensure that only authenticated and authorized users can access audit logs and generate exports.

---

## Main Audit Log Processing Flow

```text
Enterprise Application
          |
          v
   Submit JSON Log
          |
          v
   Validate Audit Log
          |
          v
    Process Audit Log
          |
          +---------------+
          |               |
          v               v
      Mask PII      Generate SHA-256
          |               |
          +-------+-------+
                  |
                  v
          Secure Storage
                  |
                  v
        Search / Export / Verify