# Task 3 - n8n Cloud Integration Workflow

## Workflow Overview

This n8n workflow listens to a webhook and appends incoming data to a Google Sheet. It demonstrates how to automate cloud-based tasks using n8n.

---

## Workflow Steps

1. **Webhook Node**

   - Trigger: `POST` request to a Production URL.
   - Collects incoming data (e.g., `name` and `email`) from the request body.

2. **Google Sheets Node**
   - Action: Append a new row to a Google Sheet.
   - Columns mapped:
     - `Name` → `{{$json.body.name}}`
     - `Email` → `{{$json.body.email}}`
   - Uses Google Sheets OAuth2 credentials.

---

## How to Use

### 1. Import the Workflow

- In n8n, click **+ New Workflow → Import from JSON**.
- Select `task3-workflow.json`.
- The workflow will appear in your editor.

### 2. Set Up Credentials

- Go to **Credentials → New Credential → Google Sheets OAuth2**.
- Authorize your Google account.
- Connect this credential to the **Google Sheets node**.

### 3. Activate Workflow

- Click **Activate** (top-right).
- Copy the **Production webhook URL** from the Webhook node.
- Make sure the node panel is closed before testing.

### 4. Test Webhook

Send a `POST` request using Postman or Thunder Client to the Production URL:

```json
{
  "name": "Archit",
  "email": "archit@example.com"
}
```
