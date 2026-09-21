#  Module 2: Authorization & RBAC Checks

###  TC-AUTH-006: Tech Attempting Manager Action (Privilege Escalation)
- **Pre-condition:** User is logged in with `Tech` role.
- **Steps:**
  1. Send `POST` request to `/api/v1/purchase-orders/PO-101/approve`.
- **Expected Result:** HTTP 403 Forbidden with message `"Access Denied: Insufficient permissions"`.

---

###  TC-AUTH-007: Student Accessing Another Student Data (IDOR Violation)
- **Pre-condition:** User logged in as `Student A` (ID: 10).
- **Steps:**
  1. Send `GET` request to `/api/v1/training-records/student-11` (Student B's record).
- **Expected Result:** HTTP 403 Forbidden or 404 Not Found (`Own` scope enforced).