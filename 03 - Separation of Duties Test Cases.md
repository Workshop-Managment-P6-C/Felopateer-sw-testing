# Module 3: Separation of Duties (SoD) Checks

### TC-SOD-001: PO Creator Cannot Approve Own PO
- **Pre-condition:** User `Manager A` created Purchase Order `PO-500`.
- **Steps:**
  1. Using `Manager A` session, send `POST` to `/api/v1/purchase-orders/PO-500/approve`.
- **Expected Result:** HTTP 403 Forbidden or 422 Unprocessable Entity with message `"SoD Violation: Creator cannot approve their own Purchase Order"`.

---

### TC-SOD-002: Technician Cannot Sign Off Own Labour
- **Pre-condition:** User `Tech A` logged hours on Job Card `JC-100`.
- **Steps:**
  1. Using `Tech A` session, send `POST` to `/api/v1/job-cards/JC-100/labour/sign-off`.
- **Expected Result:** HTTP 403 Forbidden with message `"Access Denied: Quality sign-off requires Supervisor role"`