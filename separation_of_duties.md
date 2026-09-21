# Separation of Duties (SoD) & Data Scope Definitions
**Project:** WST-P6C | QA & Security Guidelines

---

## 🛡️ Separation of Duties (SoD) Rules

1. **Purchase Orders Isolation (PO Creator != PO Approver):**
   * The user who creates a Purchase Order (`purchase-order:create`) is strictly prohibited from approving it (`purchase-order:approve`). Approvals require independent sign-off from a Manager.

2. **Quality & Labour Isolation (Technician != Quality Signer):**
   * A Technician logging work/hours (`labour:log`) cannot perform the final quality sign-off (`labour:signOff`). Quality sign-off must be completed by a designated Supervisor or Quality Checker.

3. **Assessment & Certification Isolation (Evaluator != Certificate Issuer):**
   * The mentor or instructor entering student evaluation grades (`assessment:enter`) cannot be the sole entity signing off on assessments (`assessment:sign`) or issuing the final certificate (`certificate:issue`). Certificate issuance requires Supervisor verification.

4. **Stock Control Authorization:**
   * Only Storekeepers and Managers are authorized to execute manual stock adjustments (`stock:adjust`) or reversals (`stock:reverse`). Technicians and Advisors cannot modify inventory stock levels directly.

---

## 🔒 Data Scope Definitions

* **`Own`:** Restricts user access strictly to their personal records (e.g., Students can only view their own attendance and training records).
* **`Assigned`:** Restricts access strictly to job cards, vehicles, or operational tasks assigned to the specific user (e.g., Technicians can only access job cards assigned to them).
* **`Store`:** Restricts inventory actions and stock views strictly to the branch/store location associated with the storekeeper.
* **`Group`:** Restricts access to student or operational cohorts assigned to the specific Supervisor.