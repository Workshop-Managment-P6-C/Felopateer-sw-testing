#  Module 1: Authentication Test Cases

###  TC-AUTH-001: Login with Empty Fields
- **Pre-condition:** User is on the login page
- **Steps:**
  1. Leave Email blank
  2. Leave Password blank
  3. Click "Login"
- **Expected Result:** Validation error `"Email and Password are required"

---

###  TC-AUTH-002: Login with Email Only
- **Pre-condition:** User is on the login page
- **Steps:**
  1. Enter `manager@wst.com`
  2. Leave Password blank
  3. Click "Login"
- **Expected Result:** Validation error `"Password is required"`.

---

###  TC-AUTH-003: Login with Invalid Email Format
- **Pre-condition:** User is on the login page
- **Steps:**
  1. Enter `manager.wst.com`
  2. Enter any password
  3. Click "Login"
- **Expected Result:** Validation error `"Please enter a valid email address"`.

---

### TC-AUTH-004: Login with Incorrect Credentials
- **Pre-condition:** User is on the login page
- **Steps:**
  1. Enter `advisor@wst.com`
  2. Enter `wrongPass123`
  3. Click "Login"
- **Expected Result:** HTTP 401 Unauthorized with message `"Invalid email or password"`.

---

###  TC-AUTH-005: Successful Login
- **Pre-condition:** User is on the login page
- **Steps:**
  1. Enter `manager@wst.com`
  2. Enter `Admin#2026`
  3. Click "Login"
- **Expected Result:** HTTP 200 OK, store JWT, redirect to Manager Dashboard.