<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:020617,45:0f172a,75:1e3a8a,100:334155&height=180&section=header&text=n8n%20Automation%20Lab&fontSize=42&fontColor=f8fafc&fontAlignY=38&desc=Webhook%20Automation%20%7C%20Google%20Sheets%20%7C%20Discord%20Notification&descSize=15&descAlignY=58" alt="n8n Automation Workflow Lab Header" />

<br />

<img src="https://img.shields.io/badge/n8n-Automation-ff6d5a?style=for-the-badge&labelColor=020617" alt="n8n Badge" />
<img src="https://img.shields.io/badge/Webhook-API-2563eb?style=for-the-badge&labelColor=020617" alt="Webhook Badge" />
<img src="https://img.shields.io/badge/Google%20Sheets-Integration-22c55e?style=for-the-badge&labelColor=020617" alt="Google Sheets Badge" />
<img src="https://img.shields.io/badge/Discord-Notification-5865f2?style=for-the-badge&labelColor=020617" alt="Discord Badge" />

<br />
<br />

<a href="https://github.com/Rittiporn12/n8n-automation-workflow-lab">
  <img src="https://img.shields.io/badge/GITHUB-Repository-334155?style=for-the-badge&labelColor=020617&color=475569" alt="GitHub Repository" />
</a>

<br />
<br />

<p>
  <b>n8n Automation Workflow Lab</b>
</p>

<p>
  A workflow automation project built with n8n to receive webhook data, validate input, save valid records to Google Sheets, send Discord notifications, and return API responses.
</p>

<p>
  This project focuses on automation workflow design, API testing, data validation, third-party integration, and error handling.
</p>

</div>

<hr />

<h2 align="center">About This Project</h2>

<p align="center">
  <b>n8n Automation Workflow Lab</b> is an automation workflow built to process incoming JSON data through a webhook endpoint.
</p>

<p align="center">
  The workflow validates required fields, separates valid and invalid data using conditional logic, saves valid records to Google Sheets, sends Discord notifications, and returns proper API responses.
</p>

<p align="center">
  The workflow was developed and tested locally using n8n running in Docker, with Postman used for API request testing.
</p>

<hr />

<h2 align="center">Workflow Overview</h2>

<p align="center">
  The workflow starts from a webhook request and splits into success and error branches based on input validation.
</p>

```txt
Webhook
  ↓
Validate Input
  ↓
Check Valid Data
  ├── false → Respond Error
  └── true  → Save to Google Sheets
                ↓
              Send Discord Notification
                ↓
              Respond Success
```

<div align="center">

<img src="docs/01-workflow-overview.png" alt="Workflow Overview" />

</div>

<hr />

<h2 align="center">Workflow Flow</h2>

<table align="center">
  <tr>
    <th>Step</th>
    <th>Node</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>1</td>
    <td><b>Webhook</b></td>
    <td>Receives JSON data through a POST request.</td>
  </tr>
  <tr>
    <td>2</td>
    <td><b>Validate Input</b></td>
    <td>Validates required fields and prepares clean data.</td>
  </tr>
  <tr>
    <td>3</td>
    <td><b>Check Valid Data</b></td>
    <td>Checks whether the submitted data is valid or invalid.</td>
  </tr>
  <tr>
    <td>4</td>
    <td><b>Respond Error</b></td>
    <td>Returns a 400 Bad Request response when validation fails.</td>
  </tr>
  <tr>
    <td>5</td>
    <td><b>Save to Google Sheets</b></td>
    <td>Appends valid records to Google Sheets.</td>
  </tr>
  <tr>
    <td>6</td>
    <td><b>Send Discord Notification</b></td>
    <td>Sends a notification message to Discord after saving data.</td>
  </tr>
  <tr>
    <td>7</td>
    <td><b>Respond Success</b></td>
    <td>Returns a 200 OK response when the workflow completes successfully.</td>
  </tr>
</table>

<hr />

<h2 align="center">Features</h2>

<table align="center">
  <tr>
    <th>Feature</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Webhook Endpoint</td>
    <td>Receives JSON data using an n8n Webhook node.</td>
  </tr>
  <tr>
    <td>Input Validation</td>
    <td>Checks required fields such as name, email, subject, and message.</td>
  </tr>
  <tr>
    <td>Email Format Check</td>
    <td>Performs a basic email format validation using JavaScript.</td>
  </tr>
  <tr>
    <td>Conditional Branching</td>
    <td>Uses an IF node to separate valid and invalid data paths.</td>
  </tr>
  <tr>
    <td>Google Sheets Integration</td>
    <td>Saves valid request data into Google Sheets.</td>
  </tr>
  <tr>
    <td>Discord Notification</td>
    <td>Sends a Discord message after successful data processing.</td>
  </tr>
  <tr>
    <td>API Response Handling</td>
    <td>Returns success and validation error responses using Respond to Webhook nodes.</td>
  </tr>
  <tr>
    <td>Postman Testing</td>
    <td>Tests success and error cases using Postman requests.</td>
  </tr>
  <tr>
    <td>Reusable Workflow</td>
    <td>Exports the workflow as a reusable JSON file.</td>
  </tr>
</table>

<hr />

<h2 align="center">Built With</h2>

<div align="center">

<table>
  <tr>
    <td align="center">n8n</td>
    <td align="center">Docker</td>
    <td align="center">Webhook</td>
    <td align="center">JavaScript</td>
    <td align="center">Google Sheets</td>
    <td align="center">Discord Webhook</td>
    <td align="center">Postman</td>
  </tr>
</table>

</div>

<hr />

<h2 align="center">Project Structure</h2>

```txt
n8n-automation-workflow-lab/
│
├── README.md
├── test-cases.md
│
├── workflow/
│   └── n8n-automation-workflow-lab.json
│
├── samples/
│   ├── request-success.json
│   ├── request-error-missing-email.json
│   └── request-error-invalid-email.json
│
└── docs/
    ├── 01-workflow-overview.png
    ├── 02-webhook-settings.png
    ├── 03-validate-input-code.png
    ├── 04-check-valid-data-if.png
    ├── 05-respond-error-node.png
    ├── 06-google-sheets-node.png
    ├── 07-discord-notification-node.png
    ├── 08-respond-success-node.png
    ├── 09-postman-success-200.png
    ├── 10-postman-error-400.png
    ├── 11-google-sheets-result.png
    ├── 12-discord-notification-result.png
    └── 13-production-url-test.png
```

<hr />

<h2 align="center">Workflow Node Details</h2>

<h3>1. Webhook Node</h3>

The workflow starts with a Webhook node that receives a POST request.

```txt
Method: POST
Path: automation-lab
Response Mode: Using Respond to Webhook Node
```

Example production webhook endpoint:

```txt
http://localhost:5678/webhook/automation-lab
```

<div align="center">

<img src="docs/02-webhook-settings.png" alt="Webhook Settings" />

</div>

<hr />

<h3>2. Validate Input Node</h3>

The Code node validates and normalizes the input data.

Required fields:

```txt
name
email
subject
message
```

Validation rules:

<table align="center">
  <tr>
    <th>Field</th>
    <th>Validation Rule</th>
  </tr>
  <tr>
    <td><code>name</code></td>
    <td>Must not be empty.</td>
  </tr>
  <tr>
    <td><code>email</code></td>
    <td>Must not be empty and must contain <code>@</code>.</td>
  </tr>
  <tr>
    <td><code>subject</code></td>
    <td>Must not be empty.</td>
  </tr>
  <tr>
    <td><code>message</code></td>
    <td>Must not be empty.</td>
  </tr>
</table>

Example validation output:

```json
{
  "id": "REQ-1780000000000",
  "name": "Earth",
  "email": "earth@example.com",
  "subject": "Success Test",
  "message": "This data should be saved and notified.",
  "type": "general",
  "status": "valid",
  "isValid": true,
  "errors": [],
  "createdAt": "2026-06-27T00:00:00.000Z"
}
```

<div align="center">

<img src="docs/03-validate-input-code.png" alt="Validate Input Code Node" />

</div>

<hr />

<h3>3. Check Valid Data Node</h3>

The IF node checks whether the request data is valid.

```txt
isValid is equal to true
```

Branch result:

```txt
true  → Save to Google Sheets
false → Respond Error
```

<div align="center">

<img src="docs/04-check-valid-data-if.png" alt="Check Valid Data IF Node" />

</div>

<hr />

<h3>4. Respond Error Node</h3>

If validation fails, the workflow returns a 400 Bad Request response.

```json
{
  "success": false,
  "message": "Validation failed",
  "errors": [
    "Email is required"
  ]
}
```

Status code:

```txt
400 Bad Request
```

<div align="center">

<img src="docs/05-respond-error-node.png" alt="Respond Error Node" />

</div>

<hr />

<h3>5. Save to Google Sheets Node</h3>

If the request data is valid, the workflow appends the data to Google Sheets.

Google Sheets columns:

```txt
id
createdAt
name
email
subject
message
type
status
```

<div align="center">

<img src="docs/06-google-sheets-node.png" alt="Google Sheets Node" />

</div>

<hr />

<h3>6. Send Discord Notification Node</h3>

After saving data to Google Sheets, the workflow sends a notification to Discord.

Example notification message:

```txt
New form data received
ID: REQ-1780000000000
Name: Earth
Email: earth@example.com
Subject: Success Test
Message: This data should be saved and notified.
```

<div align="center">

<img src="docs/07-discord-notification-node.png" alt="Discord Notification Node" />

</div>

<hr />

<h3>7. Respond Success Node</h3>

If the workflow completes successfully, it returns a success response.

```json
{
  "success": true,
  "message": "Data saved successfully"
}
```

Status code:

```txt
200 OK
```

<div align="center">

<img src="docs/08-respond-success-node.png" alt="Respond Success Node" />

</div>

<hr />

<h2 align="center">Sample Requests</h2>

<h3>Valid Request</h3>

```json
{
  "name": "Earth",
  "email": "earth@example.com",
  "subject": "Success Test",
  "message": "This data should be saved and notified.",
  "type": "general"
}
```

<h3>Missing Email Request</h3>

```json
{
  "name": "Earth",
  "email": "",
  "subject": "Error Test",
  "message": "This data should not be saved.",
  "type": "general"
}
```

<h3>Invalid Email Format Request</h3>

```json
{
  "name": "Earth",
  "email": "earthgmail.com",
  "subject": "Invalid Email Test",
  "message": "Testing invalid email format.",
  "type": "general"
}
```

<hr />

<h2 align="center">API Responses</h2>

<table align="center">
  <tr>
    <th>Case</th>
    <th>Status</th>
    <th>Response</th>
  </tr>
  <tr>
    <td>Valid request</td>
    <td><code>200 OK</code></td>
    <td><code>{ "success": true, "message": "Data saved successfully" }</code></td>
  </tr>
  <tr>
    <td>Invalid request</td>
    <td><code>400 Bad Request</code></td>
    <td><code>{ "success": false, "message": "Validation failed" }</code></td>
  </tr>
</table>

<h3>Success Response</h3>

```json
{
  "success": true,
  "message": "Data saved successfully"
}
```

<h3>Error Response</h3>

```json
{
  "success": false,
  "message": "Validation failed",
  "errors": [
    "Email is required"
  ]
}
```

<hr />

<h2 align="center">Test Cases</h2>

<p align="center">
  Full test cases are documented in <code>test-cases.md</code>.
</p>

<table align="center">
  <tr>
    <th>Test Case ID</th>
    <th>Scenario</th>
    <th>Expected Status</th>
    <th>Result</th>
  </tr>
  <tr>
    <td>TC-001</td>
    <td>Submit valid data</td>
    <td>200 OK</td>
    <td>Passed</td>
  </tr>
  <tr>
    <td>TC-002</td>
    <td>Submit without email</td>
    <td>400 Bad Request</td>
    <td>Passed</td>
  </tr>
  <tr>
    <td>TC-003</td>
    <td>Submit invalid email format</td>
    <td>400 Bad Request</td>
    <td>Passed</td>
  </tr>
  <tr>
    <td>TC-004</td>
    <td>Submit without name</td>
    <td>400 Bad Request</td>
    <td>Passed</td>
  </tr>
  <tr>
    <td>TC-005</td>
    <td>Submit without subject</td>
    <td>400 Bad Request</td>
    <td>Passed</td>
  </tr>
  <tr>
    <td>TC-006</td>
    <td>Submit without message</td>
    <td>400 Bad Request</td>
    <td>Passed</td>
  </tr>
</table>

<hr />

<h2 align="center">Screenshots</h2>

<h3 align="center">Workflow Overview</h3>

<div align="center">

<img src="docs/01-workflow-overview.png" alt="Workflow Overview" />

</div>

<h3 align="center">Postman Success Response</h3>

<div align="center">

<img src="docs/09-postman-success-200.png" alt="Postman Success 200" />

</div>

<h3 align="center">Postman Error Response</h3>

<div align="center">

<img src="docs/10-postman-error-400.png" alt="Postman Error 400" />

</div>

<h3 align="center">Google Sheets Result</h3>

<div align="center">

<img src="docs/11-google-sheets-result.png" alt="Google Sheets Result" />

</div>

<h3 align="center">Discord Notification Result</h3>

<div align="center">

<img src="docs/12-discord-notification-result.png" alt="Discord Notification Result" />

</div>

<h3 align="center">Production URL Test</h3>

<div align="center">

<img src="docs/13-production-url-test.png" alt="Production URL Test" />

</div>

<hr />

<h2 align="center">How to Import Workflow</h2>

<p align="center">
  Follow the steps below to import and configure the workflow in n8n.
</p>

<table align="center">
  <tr>
    <th>Step</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>1</td>
    <td>Open n8n.</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Go to <b>Workflows</b>.</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Click <b>Import from File</b>.</td>
  </tr>
  <tr>
    <td>4</td>
    <td>Select <code>workflow/n8n-automation-workflow-lab.json</code>.</td>
  </tr>
  <tr>
    <td>5</td>
    <td>Configure your own Google Sheets credential.</td>
  </tr>
  <tr>
    <td>6</td>
    <td>Replace <code>YOUR_DISCORD_WEBHOOK_URL</code> with your Discord Webhook URL.</td>
  </tr>
  <tr>
    <td>7</td>
    <td>Replace Google Sheet placeholders if needed.</td>
  </tr>
  <tr>
    <td>8</td>
    <td>Save and activate the workflow.</td>
  </tr>
  <tr>
    <td>9</td>
    <td>Test the production webhook URL using Postman.</td>
  </tr>
</table>

<hr />

<h2 align="center">Local Development</h2>

<p align="center">
  This workflow was developed and tested using n8n running locally with Docker.
</p>

<table align="center">
  <tr>
    <th>Type</th>
    <th>URL</th>
  </tr>
  <tr>
    <td>n8n Local URL</td>
    <td><code>http://localhost:5678</code></td>
  </tr>
  <tr>
    <td>Test Webhook URL</td>
    <td><code>http://localhost:5678/webhook-test/automation-lab</code></td>
  </tr>
  <tr>
    <td>Production Webhook URL</td>
    <td><code>http://localhost:5678/webhook/automation-lab</code></td>
  </tr>
</table>

<hr />

<h2 align="center">Security Notes</h2>

<p align="center">
  This repository does not include real credentials, tokens, or private webhook URLs.
</p>

<p align="center">
  Sensitive values were replaced with placeholders before publishing.
</p>

<table align="center">
  <tr>
    <th>Placeholder</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><code>YOUR_DISCORD_WEBHOOK_URL</code></td>
    <td>Discord Webhook URL placeholder.</td>
  </tr>
  <tr>
    <td><code>YOUR_GOOGLE_SHEET_ID</code></td>
    <td>Google Sheet ID placeholder.</td>
  </tr>
  <tr>
    <td><code>YOUR_GOOGLE_SHEET_URL</code></td>
    <td>Google Sheet URL placeholder.</td>
  </tr>
</table>

<h3>Do not publish:</h3>

<ul>
  <li>Real Discord Webhook URL</li>
  <li>Google OAuth Client Secret</li>
  <li>Google access token</li>
  <li>Google refresh token</li>
  <li>Private credentials</li>
  <li>Personal or sensitive data from Google Sheets</li>
</ul>

<hr />

<h2 align="center">What I Learned</h2>

<table align="center">
  <tr>
    <th>Topic</th>
    <th>Practice</th>
  </tr>
  <tr>
    <td>n8n Workflow Automation</td>
    <td>Created a complete automation workflow using multiple nodes.</td>
  </tr>
  <tr>
    <td>Webhook API</td>
    <td>Received and tested JSON requests through webhook endpoints.</td>
  </tr>
  <tr>
    <td>Data Validation</td>
    <td>Validated input fields using JavaScript inside the Code node.</td>
  </tr>
  <tr>
    <td>Error Handling</td>
    <td>Returned proper 400 Bad Request responses for invalid data.</td>
  </tr>
  <tr>
    <td>Google Sheets Integration</td>
    <td>Saved valid records to Google Sheets automatically.</td>
  </tr>
  <tr>
    <td>Discord Notification</td>
    <td>Sent notification messages using an HTTP Request node.</td>
  </tr>
  <tr>
    <td>API Testing</td>
    <td>Tested success and error cases using Postman.</td>
  </tr>
  <tr>
    <td>Documentation</td>
    <td>Documented workflow logic, screenshots, requests, and test cases.</td>
  </tr>
</table>

<hr />

<h2 align="center">Author</h2>

<div align="center">

<p>
  <b>Rittiporn Phungphai</b>
</p>

<p>
  Software Development | Automation Workflow | Full-Stack Development | Software Quality
</p>

<p>
  <a href="https://github.com/Rittiporn12">
    GitHub Profile
  </a>
  &nbsp;|&nbsp;
  <a href="https://rittiporn12.github.io/portfolio/">
    Portfolio Website
  </a>
</p>

</div>

<hr />

<div align="center">

<p>
  <b>Thank you for visiting this project.</b>
</p>

<p>
  Feel free to explore the workflow, review the test cases, and adapt it for your own automation use cases.
</p>

</div>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:334155,45:1e3a8a,75:0f172a,100:020617&height=100&section=footer" alt="Footer" />
