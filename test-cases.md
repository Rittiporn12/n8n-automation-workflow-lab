# Test Cases

## TC-001: Submit Valid Data

**Objective:**
Verify that the workflow can receive valid input data, save it to Google Sheets, send a Discord notification, and return a success response.

**Request Body**

```json
{
  "name": "Earth",
  "email": "earth@example.com",
  "subject": "Success Test",
  "message": "This data should be saved and notified.",
  "type": "general"
}
```

**Expected Result**

- Response status code is `200 OK`
- Response body returns success message
- Data is saved to Google Sheets
- Discord notification is sent successfully

**Actual Result**

- Passed

---

## TC-002: Submit Without Email

**Objective:**
Verify that the workflow rejects data when the email field is empty.

**Request Body**

```json
{
  "name": "Earth",
  "email": "",
  "subject": "Error Test",
  "message": "This data should not be saved.",
  "type": "general"
}
```

**Expected Result**

- Response status code is `400 Bad Request`
- Response body returns validation error
- Error message includes `Email is required`
- Data is not saved to Google Sheets
- Discord notification is not sent

**Actual Result**

- Passed

---

## TC-003: Submit Invalid Email Format

**Objective:**
Verify that the workflow rejects data when the email format is invalid.

**Request Body**

```json
{
  "name": "Earth",
  "email": "earthgmail.com",
  "subject": "Invalid Email Test",
  "message": "Testing invalid email format.",
  "type": "general"
}
```

**Expected Result**

- Response status code is `400 Bad Request`
- Response body returns validation error
- Error message includes `Email format is invalid`
- Data is not saved to Google Sheets
- Discord notification is not sent

**Actual Result**

- Passed

---

## TC-004: Submit Without Name

**Objective:**
Verify that the workflow rejects data when the name field is empty.

**Request Body**

```json
{
  "name": "",
  "email": "earth@example.com",
  "subject": "Missing Name Test",
  "message": "Testing missing name validation.",
  "type": "general"
}
```

**Expected Result**

- Response status code is `400 Bad Request`
- Response body returns validation error
- Error message includes `Name is required`
- Data is not saved to Google Sheets
- Discord notification is not sent

**Actual Result**

- Passed

---

## TC-005: Submit Without Subject

**Objective:**
Verify that the workflow rejects data when the subject field is empty.

**Request Body**

```json
{
  "name": "Earth",
  "email": "earth@example.com",
  "subject": "",
  "message": "Testing missing subject validation.",
  "type": "general"
}
```

**Expected Result**

- Response status code is `400 Bad Request`
- Response body returns validation error
- Error message includes `Subject is required`
- Data is not saved to Google Sheets
- Discord notification is not sent

**Actual Result**

- Passed

---

## TC-006: Submit Without Message

**Objective:**
Verify that the workflow rejects data when the message field is empty.

**Request Body**

```json
{
  "name": "Earth",
  "email": "earth@example.com",
  "subject": "Missing Message Test",
  "message": "",
  "type": "general"
}
```

**Expected Result**

- Response status code is `400 Bad Request`
- Response body returns validation error
- Error message includes `Message is required`
- Data is not saved to Google Sheets
- Discord notification is not sent

**Actual Result**

- Passed

---

## Test Summary

| Test Case ID | Scenario                    | Expected Status | Result |
| ------------ | --------------------------- | --------------: | ------ |
| TC-001       | Submit valid data           |          200 OK | Passed |
| TC-002       | Submit without email        | 400 Bad Request | Passed |
| TC-003       | Submit invalid email format | 400 Bad Request | Passed |
| TC-004       | Submit without name         | 400 Bad Request | Passed |
| TC-005       | Submit without subject      | 400 Bad Request | Passed |
| TC-006       | Submit without message      | 400 Bad Request | Passed |
