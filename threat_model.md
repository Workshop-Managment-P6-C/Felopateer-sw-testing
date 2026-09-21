# Threat Model & Security Testing Strategy: RBAC & SoD Controls

**Project:** WST-P6C | QA & Security Guidelines  
**Scope:** Role-Based Access Control (RBAC), Data Scopes, & Separation of Duties (SoD)

---

## 1. Overview
This threat model identifies potential authorization vulnerabilities, privilege escalation vectors, and SoD bypass risks within the WST application endpoints. It establishes the test cases required for security verification.

---

## 2. Key Threat Scenarios

### 🚨 Threat 1: Vertical Privilege Escalation (Role Bypassing)
* **Description:** A user with a low-privilege role (e.g., `Tech` or `Student`) attempts to call an admin/manager endpoint (e.g., `purchase-order:approve` or `export:run`).
* **Attack Vector:** Tampering with request headers, JWT claims, or directly sending HTTP requests to restricted routes.
* **Impact:** Unauthorized financial approvals or system-wide data extraction.
* **QA Test Mitigation:**
  * Integration tests must send requests using `Tech`/`Student` tokens to Manager endpoints.
  * Expected Response: `403 Forbidden`.

---

### 🚨 Threat 2: Separation of Duties (SoD) Bypass
* **Description:** A single user executes two conflicting action steps (e.g., creating a purchase order and approving it, or logging labour and signing it off).
* **Attack Vector:** An advisor or tech creates a resource and immediately triggers the approval API with their own credentials.
* **Impact:** Operational fraud, unverified quality sign-offs, and unauthorized financial commitments.
* **QA Test Mitigation:**
  * Integration tests must attempt a self-approval workflow (`PO.creator_id == PO.approver_id`).
  * Expected Response: `403 Forbidden` or `422 Unprocessable Entity`.

---

### 🚨 Threat 3: Broken Object Level Authorization / IDOR (Horizontal Access Violation)
* **Description:** A user accesses or modifies data outside their permitted **Data Scope** (`Own`, `Assigned`, `Store`, `Group`).
* **Attack Vectors:**
  * A `Student` changes the student ID parameter in a URL to view another student's training grades (`Own` scope violation).
  * A `Tech` updates a job card not assigned to them (`Assigned` scope violation).
  * A `Storekeeper` alters stock levels in a different store branch (`Store` scope violation).
* **Impact:** Privacy breaches, data manipulation, and cross-branch inventory distortion.
* **QA Test Mitigation:**
  * Integration tests must query/update resources belonging to other entities/users.
  * Expected Response: `403 Forbidden` or `404 Not Found`.

---

### 🚨 Threat 4: Unauthorized Bulk Data Export
* **Description:** Unauthorized execution of global data exports (`export:run`) or reading system audit logs (`audit:read`).
* **Attack Vector:** Directly invoking export endpoints to harvest system records.
* **Impact:** Mass data exfiltration and compliance failure.
* **QA Test Mitigation:**
  * Security tests must verify that `Tech`, `Advisor`, and `Storekeeper` roles cannot access `export:run`.
  * Expected Response: `403 Forbidden`.

---

## 3. Authorization Security Test Matrix

| Target Endpoint / Permission | Allowed Roles | Prohibited Roles (Must return 403) | Enforced Security Rule / Scope |
| :--- | :--- | :--- | :--- |
| `purchase-order:approve` | `Manager` | `Advisor`, `Tech`, `Storekeeper`, `Supervisor`, `Student` | SoD: Creator != Approver |
| `labour:signOff` | `Manager`, `Supervisor` | `Advisor`, `Tech`, `Storekeeper`, `Student` | SoD: Logger != Signer |
| `stock:adjust` | `Manager`, `Storekeeper` | `Advisor`, `Tech`, `Supervisor`, `Student` | Scope: `Store` Isolation |
| `training-record:read` | `Manager`, `Advisor`, `Supervisor`, `Student` | `Tech`, `Storekeeper` | Scope: `Own` (Student), `Group` (Supervisor) |