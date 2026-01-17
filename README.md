# Durion Accounting

Financial Management

## Overview

This component is part of the Durion ERP system built on the Moqui Framework.

## Purpose

Provide the Moqui-side entities, services, and screens for Durion's accounting capabilities, aligned to the Accounting domain business rules (financial integrity, auditability, and effective-dated configuration).

## Scope

In scope:
- Chart of Accounts (GL accounts) management with effective dating
- Posting categories, effective-dated mappings, and posting configuration surfaces
- Visibility into accounting artifacts and audit trails (for example: journal/ledger postings and invoice financial snapshots) where integrated
- Integration points to ingest/emit accounting-related events used by other domains

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
- `template/` - Email and document templates
- `test/` - Test specifications

## Dependencies

See `component.xml` for component dependencies.

## Installation

This component is managed via `myaddons.xml` in the Moqui project root.

## License

Same as Durion project.

---

**Last Updated:** December 09, 2025
