#  Module 5: Inventory & Stock Management Test Cases

### TC-INV-001: Manual Stock Adjustment (Storekeeper)
- **Pre-condition:** User logged in as `Storekeeper` for Branch A.
- **Steps:**
  1. Select part `OIL-FIL-01`.
  2. Adjust stock count by `+10` units with reason `"Physical Count Correction"`.
  3. Submit adjustment.
- **Expected Result:** Stock updated successfully, audit log entry created (HTTP 200 OK).

---

###  TC-INV-002: Inter-Branch Stock Transfer
- **Pre-condition:** Part exists in Branch A with available quantity >= requested.
- **Steps:**
  1. Initiate transfer from `Branch A` to `Branch B` for item `BRAKE-PAD-02` (Qty: 5).
  2. Submit transfer request.
- **Expected Result:** Quantity reserved in Branch A, status set to `IN_TRANSIT` (HTTP 200 OK).

---

###  TC-INV-003: Unauthorized Stock Adjustment Attempt
- **Pre-condition:** User logged in as `Advisor` or `Tech`.
- **Steps:**
  1. Send `POST` request to `/api/v1/stores/branch-1/stock/adjust`.
- **Expected Result:** Access denied (HTTP 403 Forbidden).