# Complete Requirements Table

## Functional Requirements

| ID | Type | Description | Priority | Acceptance Criteria | Rationale |
|---|---|---|---|---|---|
| FR-001 | Functional | The system shall allow a Pharmacy Clerk to record each received medicine batch with medicine identifier, batch number, quantity, received date, expiry date, and supplier. | High | **Pass:** A valid batch is saved and is available in inventory with all six fields. **Fail:** The system accepts a missing batch number, quantity, or expiry date. | Batch-level data is essential for expiry tracking, traceability, and FEFO selection. |
| FR-002 | Functional | The system shall identify and display batches that are expired or will expire within a configurable alert period. | High | **Pass:** On the daily check, all expired batches and batches within the configured period are listed with status and expiry date. **Fail:** A qualifying batch is absent from the alert list. | Early visibility prevents unsafe dispensing and reduces wastage. |
| FR-003 | Functional | The system shall generate a FEFO dispensing list that orders only unexpired batches of a selected medicine by nearest expiry date first. | High | **Pass:** The nearest-expiring valid batch is first; expired batches are excluded. **Fail:** A newer-expiry batch precedes an older valid batch. | FEFO minimizes expiry-related loss while ensuring patients receive safe stock. |
| FR-004 | Functional | The system shall compare the available stock of each medicine against its configured safety threshold after every stock receipt and dispensing transaction. | High | **Pass:** A threshold breach is detected immediately after a transaction lowers available stock below the threshold. **Fail:** A below-threshold medicine is not flagged. | Continuous threshold checking prevents stock-outs of essential medicines. |
| FR-005 | Functional | The system shall generate a purchase order for a below-threshold medicine and dispatch it to the assigned Inventory Supplier after Pharmacy Clerk approval. | High | **Pass:** An approved order contains medicine, calculated re-order quantity, supplier, and order reference, and the supplier receives it. **Fail:** An order is dispatched without approval or missing required details. | Automating re-order preparation shortens replenishment time while retaining clerk control. |

## Non-Functional Requirements

| ID | Type | Description | Priority | Acceptance Criteria | Rationale |
|---|---|---|---|---|---|
| NFR-001 | Performance | Under a simulated peak load of 100 concurrent clerk requests, the system shall return a FEFO dispensing list or threshold-check result within 2 seconds for 95% of requests. | High | **Pass:** Load-test results show the 95th-percentile response time is at most 2 seconds. **Fail:** The 95th percentile exceeds 2 seconds. | Pharmacy operations require prompt recommendations at checkout and during busy periods. |
| NFR-002 | Security | The system shall require authenticated Pharmacy Clerk access for inventory changes and purchase-order approval, and shall keep an audit record of the user, timestamp, and action for at least 12 months. | High | **Pass:** Unauthenticated changes/approvals are denied; each authorized action has a complete audit record retained for 12 months. **Fail:** An unauthenticated action succeeds or an audit record is incomplete. | Inventory and procurement records are sensitive operational data and need accountability. |

