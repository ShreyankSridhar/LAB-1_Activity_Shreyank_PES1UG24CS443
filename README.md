# Pharmacy Expiry & Re-order Dispatch Engine

**Course:** PES1UG24CS443 - Software Engineering Lab 1  
**Problem Statement:** #15 - Healthcare & Telemedicine

This repository contains the Requirements Engineering and UML Use-Case Modelling deliverables for a hospital-pharmacy stock management engine. The engine tracks medicine batches and their expiry dates, produces First-Expired-First-Out (FEFO) dispensing recommendations, and automates re-order dispatches when inventory reaches a safety threshold.

## Question / Problem Statement

The original assignment PDF is preserved exactly as provided: [15_SE_Lab1_SE_Problem_Statements.pdf](problem-statement/15_SE_Lab1_SE_Problem_Statements.pdf).

## Repository contents

| Deliverable | Location |
|---|---|
| Requirements source file | [docs/requirements.md](docs/requirements.md) |
| Requirements PDF | [deliverables/pdf/requirements.pdf](deliverables/pdf/requirements.pdf) |
| UML use-case diagram (viewable SVG) | [diagrams/use-case-diagram.svg](diagrams/use-case-diagram.svg) |
| UML use-case diagram source | [diagrams/use-case-diagram.puml](diagrams/use-case-diagram.puml) |
| UML use-case diagram PDF | [deliverables/pdf/uml-use-case-diagram.pdf](deliverables/pdf/uml-use-case-diagram.pdf) |
| Use-case flow source file | [docs/use-case-flow-specification.md](docs/use-case-flow-specification.md) |
| Use-case flow specification PDF | [deliverables/pdf/use-case-flow-specification.pdf](deliverables/pdf/use-case-flow-specification.pdf) |

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
