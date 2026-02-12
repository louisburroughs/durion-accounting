# Durion Accounting

Financial Management

## Overview

This component is part of the Durion ERP system built on the Moqui Framework.

It provides comprehensive accounting functionality including accounts receivable, payments, and refund management.

## Purpose

Provide the Moqui-side entities, services, and screens for Durion's accounting capabilities, aligned to the Accounting domain business rules (financial integrity, auditability, and effective-dated configuration).

## Scope

In scope:
- Chart of Accounts (GL accounts) management with effective dating
- Posting categories, effective-dated mappings, and posting configuration surfaces
- Visibility into accounting artifacts and audit trails (for example: journal/ledger postings and invoice financial snapshots) where integrated
- Integration points to ingest/emit accounting-related events used by other domains
- Accounts Receivable (AR) transaction management
- Payment processing and tracking
- Refund payment management with full lifecycle support

Out of scope:
- Authoritative tax/fee rule definition (sourced externally; accounting consumes results)
- Invoice lifecycle transitions (owned by Billing domain)
- Inventory valuation and product master management (owned by Inventory/Product domains)

## Structure

- `data/` - Seed and demo data
- `entity/` - Entity definitions
- `screen/` - UI screens and forms
- `service/` - Service definitions
- `src/` - Groovy/Java source code
  - `src/main/java/com/durion/accounting/enums/` - Java enums (e.g., RefundPaymentStatus)
- `template/` - Email and document templates
- `test/` - Test specifications

## Key Features

### Refund Payment Management

The component includes comprehensive refund payment functionality with a well-defined status lifecycle:

**RefundPaymentStatus Enum Values:**
- `INITIATED` - Refund request created, pending approval
- `APPROVED` - Refund approved, ready for processing
- `PROCESSING` - Refund payment being processed
- `COMPLETED` - Refund successfully completed
- `FAILED` - Refund failed during processing
- `CANCELLED` - Refund cancelled before completion

**Refund Payment Workflow:**
1. **Initiation**: Create a refund request using `durion.initiateRefundPayment`
2. **Approval**: Approve the refund using `durion.approveRefundPayment`
3. **Processing**: Process the refund using `durion.processRefundPayment`
4. **Completion**: Complete the refund using `durion.completeRefundPayment`

**Status Transitions:**
- INITIATED → APPROVED or CANCELLED
- APPROVED → PROCESSING or CANCELLED
- PROCESSING → COMPLETED or FAILED

**Available Services:**
- `durion.initiateRefundPayment` - Create a new refund request
- `durion.approveRefundPayment` - Approve a refund
- `durion.processRefundPayment` - Start processing a refund
- `durion.completeRefundPayment` - Complete a refund (creates AR transaction)
- `durion.failRefundPayment` - Mark a refund as failed
- `durion.cancelRefundPayment` - Cancel a refund
- `durion.findRefundPayments` - Query refund payments with filters
- `durion.getRefundPaymentSummary` - Get refund statistics

**Supported Refund Methods:**
- ORIGINAL_METHOD - Refund to original payment method
- CHECK - Physical check
- ACH - Electronic bank transfer
- WIRE_TRANSFER - Wire transfer
- STORE_CREDIT - Store credit for future purchases

### Accounts Receivable

Manage AR transactions including invoices, credit memos, payments, and refunds with full GL integration.

### Payment Processing

Track customer payments through their lifecycle with support for various payment methods (cash, check, credit card, ACH, wire transfer).

## Dependencies

See `component.xml` for component dependencies.

## Installation

This component is managed via `myaddons.xml` in the Moqui project root.

## License

Same as Durion project.

---

**Last Updated:** February 12, 2026
