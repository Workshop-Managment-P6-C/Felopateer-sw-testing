#  Module 4: Job Cards & Repair Orders Test Cases

###  TC-JC-001: Create Job Card with Valid Data
- **Pre-condition:** User is logged in as `Advisor`.
- **Steps:**
  1. Select a registered vehicle and customer.
  2. Enter reported issue description.
  3. Click "Create Job Card".
- **Expected Result:** Job Card created successfully with status `OPEN` and unique ID (HTTP 201 Created).

---

###  TC-JC-002: Add Spare Parts to Job Card
- **Pre-condition:** Job Card status is `IN_PROGRESS` and user is logged in as `Tech`.
- **Steps:**
  1. Select Job Card `JC-101`.
  2. Request spare part item code `PART-505` with quantity `2`.
  3. Submit request.
- **Expected Result:** Item added to Job Card line items, pending Storekeeper issuing (HTTP 200 OK).

---

###  TC-JC-003: Log Labour Hours
- **Pre-condition:** User is logged in as `Tech` assigned to the Job Card.
- **Steps:**
  1. Enter start time and end time for task execution (e.g., 2.5 hours).
  2. Click "Log Hours".
- **Expected Result:** Labour hours recorded, waiting for Supervisor sign-off (HTTP 200 OK).