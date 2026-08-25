# Pharmacy Expiry & Re-order Dispatch Engine

**Course:** PES1UG24CS443 - Software Engineering Lab 1  
**Problem Statement:** #15 - Healthcare & Telemedicine

This repository contains the Requirements Engineering and UML Use-Case Modelling deliverables for a hospital-pharmacy stock management engine. The engine tracks medicine batches and their expiry dates, produces First-Expired-First-Out (FEFO) dispensing recommendations, and automates re-order dispatches when inventory reaches a safety threshold.

## Repository contents

| Deliverable | Location |
|---|---|
| Complete requirements table | [docs/requirements.md](docs/requirements.md) |
| UML use-case diagram (viewable SVG) | [diagrams/use-case-diagram.svg](diagrams/use-case-diagram.svg) |
| UML use-case diagram source | [diagrams/use-case-diagram.puml](diagrams/use-case-diagram.puml) |
| Core use-case flow specification | [docs/use-case-flow-specification.md](docs/use-case-flow-specification.md) |

## Domain and actors

- **Pharmacy Clerk:** records stock receipts, requests dispensing recommendations, reviews alerts, and approves re-orders.
- **Inventory Supplier:** receives purchase orders and returns dispatch acknowledgements.

## Traceability

| Requirement | Use case(s) |
|---|---|
| FR-001, FR-002 | Record Batch Receipt, Monitor Batch Expiry |
| FR-003 | Generate FEFO Dispensing List |
| FR-004 | Check Re-order Threshold |
| FR-005 | Generate Purchase Order, Approve Purchase Order, Dispatch Purchase Order, Receive Supplier Acknowledgement |
| NFR-001, NFR-002 | All system use cases |
