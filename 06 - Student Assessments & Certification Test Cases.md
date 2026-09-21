#  Module 6: Student Assessments & Certification Test Cases

### TC-ASS-001: Enter Student Training Assessment
- **Pre-condition:** User logged in as `Supervisor` assigned to Student Group A.
- **Steps:**
  1. Select Student `STD-202`.
  2. Enter score `85/100` for practical assessment.
  3. Save assessment.
- **Expected Result:** Grade saved successfully and visible to the student under `Own` scope (HTTP 200 OK).

---

### TC-ASS-002: Issue Final Certificate
- **Pre-condition:** Student completed all required modules; user logged in as `Supervisor` or `Manager`.
- **Steps:**
  1. Open completed student profile `STD-202`.
  2. Click "Issue Certificate".
- **Expected Result:** Unique Certificate ID generated with PDF generation triggered (HTTP 201 Created).

---

### TC-ASS-003: Prevent Self-Certification by Evaluator
- **Pre-condition:** User logged in as `Advisor`/Instructor who entered the assessment grades.
- **Steps:**
  1. Attempt to trigger certificate issuance directly.
- **Expected Result:** Rejected due to SoD policy (HTTP 403 Forbidden).