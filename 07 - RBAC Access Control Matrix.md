
This document defines the official Role-Based Access Control (RBAC) matrix and Data Scopes for the WST Management System, mapped directly from the system specification.

---

## 📊 Access Control Matrix

| Permission / Endpoint | Manager | Advisor | Tech | Storekeeper | Supervisor | Student |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| `customer:create` | 🟢 Yes | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔴 No |
| `customer:readUpdate` | 🟢 Yes | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔴 No |
| `vehicle:create` | 🟢 Yes | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔴 No |
| `vehicle:read` | 🟢 Yes | 🟢 Yes | 🟡 Assigned | 🔴 No | 🔵 Group | 🔴 No |
| `job-card:create` | 🟢 Yes | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔴 No |
| `job-card:readChangeStage` | 🟢 Yes | 🟢 Yes | 🟡 Assigned | 🔴 No | 🔵 Group | 🔴 No |
| `labour:log` | 🟢 Yes | 🟢 Yes | 🟡 Assigned | 🔴 No | 🔴 No | 🔴 No |
| `labour:signOff` | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔵 Group | 🔴 No |
| `purchase-order:create` | 🟢 Yes | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔴 No |
| `purchase-order:approve` | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔴 No | 🔴 No |
| `purchase-order:receive` | 🟢 Yes | 🔴 No | 🔴 No | 🟠 Store | 🔴 No | 🔴 No |
| `stock:adjust` | 🟢 Yes | 🔴 No | 🔴 No | 🟠 Store | 🔴 No | 🔴 No |
| `stock:reverse` | 🟢 Yes | 🔴 No | 🔴 No | 🟠 Store | 🔴 No | 🔴 No |
| `vendor:manage` | 🟢 Yes | 🔴 No | 🔴 No | 🟠 Store | 🔴 No | 🔴 No |
| `invoice:view` | 🟢 Yes | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔴 No |
| `assessment:enter` | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔵 Group | 🔴 No |
| `assessment:sign` | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔵 Group | 🔴 No |
| `certificate:issue` | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔵 Group | 🔴 No |
| `training-session:schedule` | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔵 Group | 🔴 No |
| `training-record:read` | 🟢 Yes | 🟢 Yes | 🔴 No | 🔴 No | 🔵 Group | 🟣 Own |
| `attendance:record` | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔵 Group | 🔴 No |
| `dashboard:view` | 🟢 Yes | 🟢 Yes | 🔴 No | 🟠 Store | 🔵 Group | 🔴 No |
| `export:run` | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔵 Group | 🔴 No |
| `audit:read` | 🟢 Yes | 🔴 No | 🔴 No | 🔴 No | 🔴 No | 🔴 No |

---

## 🔒 Data Scope Definitions

> **Legend & Scope Explanations:**
> - 🟢 **`Yes`**: Full unrestricted access across organizational scope.
> - 🔴 **`No`**: Access explicitly denied (HTTP 403 Forbidden).
> - 🟡 **`Assigned`**: Access restricted strictly to job cards, vehicles, or tasks assigned directly to the technician.
> - 🟠 **`Store`**: Access restricted strictly to the inventory/store location associated with the storekeeper.
> - 🔵 **`Group`**: Access restricted strictly to student groups or training cohorts assigned to the supervisor.
> - 🟣 **`Own`**: Access restricted strictly to the user's personal student records/grades.