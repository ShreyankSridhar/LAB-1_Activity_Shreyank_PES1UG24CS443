# Use-Case Flow Specification: Generate and Dispatch Purchase Order

| Item | Specification |
|---|---|
| **Use-case ID** | UC-05 |
| **Primary actor** | Pharmacy Clerk |
| **Supporting actor** | Inventory Supplier |
| **Goal** | Replenish a medicine whose available stock is below its safety threshold. |
| **Trigger** | A stock transaction causes the threshold check to detect a shortage, or the clerk initiates a threshold review. |

## Preconditions

1. The Pharmacy Clerk is authenticated and authorized to approve purchase orders.
2. The medicine, its safety threshold, re-order quantity rule, and assigned Inventory Supplier are configured.
3. Current inventory balances are available and the supplier dispatch endpoint is reachable.

## Postconditions

- **Success:** A uniquely referenced, approved purchase order is stored and dispatched to the assigned supplier; its status is recorded as `Dispatched` and an audit entry is created.
- **Failure:** No purchase order is dispatched; the cause and current order status are recorded for the clerk to review.

## Main Success Scenario

1. The system calculates the medicine's available stock and detects that it is below the configured safety threshold.
2. The system calculates the required re-order quantity according to the configured re-order rule.
3. The system creates a draft purchase order containing the medicine, required quantity, supplier, date, and unique order reference.
4. The system presents the draft to the Pharmacy Clerk for review.
5. The Pharmacy Clerk verifies the details and approves the purchase order.
6. The system records the approval with the clerk identity and timestamp.
7. The system dispatches the approved purchase order to the assigned Inventory Supplier.
8. The Inventory Supplier acknowledges receipt of the order.
9. The system changes the order status to `Dispatched`, stores the acknowledgement, and shows confirmation to the Pharmacy Clerk.

## Alternate Flow A1 - Supplier Does Not Acknowledge Dispatch

1. At Step 8, the supplier endpoint does not return an acknowledgement within the configured timeout.
2. The system marks the order as `Dispatch Pending`, retains the approved order, and records the failed attempt in the audit log.
3. The system notifies the Pharmacy Clerk and provides the **Retry Failed Dispatch** option.
4. When the clerk selects **Retry Failed Dispatch**, the system re-dispatches the same uniquely referenced order; it must not create a duplicate purchase order.
