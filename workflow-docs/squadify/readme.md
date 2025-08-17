# Squadify Deal to Invoice Processing

**Automates the end-to-end process of transforming a HubSpot deal into a Xero invoice, including validation, error handling, Slack notifications, and business/developer-friendly troubleshooting.**

---

## What This Workflow Does

This workflow streamlines the process of turning a closed HubSpot deal into a Xero invoice for Squadify. When a deal reaches a specified stage, the automation fetches all relevant deal data, validates required fields, creates an invoice in Xero, updates the HubSpot deal with the invoice link, and moves the deal to an "invoiced" stage. It includes robust error handling with Slack and email notifications, and leverages OpenAI for clear business/developer error explanations. Ideal for SaaS teams seeking reliable, auditable, and automated deal-to-invoice handoff with minimal manual intervention.

---

## Workflow Steps

| Step Name                       | Trigger Condition                                                                                                    | Action                                                                                                 |
|----------------------------------|---------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| fetch deal data                  | <div><button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button><pre><code class="language-json">{ "items": [{ "propertyValue": "String", "propertyName": "dealstage" }], "hubspotDeal": null }</code></pre></div> | Fetches HubSpot deal, company, contact, and line items by dealstage                                    |
| validate deal                    | <div><button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button><pre><code class="language-json">{ "hubspotDeal": "Object", "validated": null }</code></pre></div> | Validates deal, company, contact, and line item data; notifies Slack on success/error                  |
| create xero invoice              | <div><button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button><pre><code class="language-json">{ "hubspotDeal": "Object", "validated": true }</code></pre></div> | Creates invoice in Xero from deal data; stores invoice ID/URL; notifies Slack on success/error         |
| add invoice link to hubspot      | <div><button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button><pre><code class="language-json">{ "invoiceCreated": true, "invoiceCreatedUrl": "String", "invoiceLinkAdded": null, "hubspotDeal": "Object", "invoiceCreatedNumber": "String" }</code></pre></div> | Adds invoice link and number to HubSpot deal; notifies Slack on success/error                         |
| move hubspot deal to invoiced    | <div><button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button><pre><code class="language-json">{ "invoiceLinkAdded": true, "hubspotDeal": "Object" }</code></pre></div> | Moves deal to "invoiced" stage in HubSpot; sends completion email and Slack notification               |
| subtask                          | <div><button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button><pre><code class="language-json">{ "runsubtask": true }</code></pre></div> | Uses OpenAI to classify errors as business/dev; sends business errors via email                        |
| Debugging Step                   | <div><button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button><pre><code class="language-json">{ "debugErrors": true }</code></pre></div> | Runs Xero/HubSpot debug queries for troubleshooting                                                    |
| OpenAI output                    | <div><button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button><pre><code class="language-json">{ "todo": true }</code></pre></div> | Example code for Xero invoice creation using OpenAI (for reference/testing)                            |

---

## Integrations Used in Example

- [HubSpot CRM (Private App)](https://developers.hubspot.com/docs/api/overview)
- [Xero API](https://developer.xero.com/documentation/api/api-overview)
- [Slack API](https://api.slack.com/)
- [SMTP Email](https://nodemailer.com/smtp/)
- [OpenAI API](https://platform.openai.com/docs/api-reference)
- [ALOMA CLI](https://docs.aloma.io/cli/installation)

---

## Setup Instructions (CLI)

1. **Clone the repository and enter the workflow directory**
<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-bash">
git clone &lt;repository-url&gt;
cd &lt;workflow-directory&gt;
</code></pre>
</div>

2. **Update `deploy.yaml` with your connector keys and secrets (see below)**

3. **Deploy the workflow**
<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-bash">
aloma deploy deploy.yaml
</code></pre>
</div>

4. **Complete connector OAuth if required**
<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-bash">
aloma connector list
aloma connector oauth &lt;connector-id&gt;
</code></pre>
</div>

5. **Test with a sample task**
<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-bash">
aloma task new "test deal to invoice" -f example.json
</code></pre>
</div>

6. **View task logs**
<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-bash">
aloma task log &lt;task-id&gt; --logs --changes
</code></pre>
</div>

---

## Configuration (Connectors & Secrets)

Edit `deploy.yaml` and update the following sections with your actual values:

<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-yaml">
connectors:
  - connectorName: "openai.com"
    config:
      apiKey: "<YOUR_OPENAI_API_KEY>"
  - connectorName: "slack.com"
    config:
      mapping: "<YOUR_SLACK_MAPPING>" # optional
  - connectorName: "E-Mail (SMTP)"
    config:
      smtpUser: "<YOUR_SMTP_USER>" # optional
      smtpPassword: "<YOUR_SMTP_PASSWORD>" # optional
      smtpHost: "<YOUR_SMTP_HOST>"
  - connectorName: "Xero"
    config:
      clientId: "<YOUR_XERO_CLIENT_ID>"
      clientSecret: "<YOUR_XERO_CLIENT_SECRET>"
      tenantId: "<YOUR_XERO_TENANT_ID>" # optional
      scope: "<YOUR_XERO_SCOPE>"
  - connectorName: "hubspot.com (private)"
    config:
      apiToken: "<YOUR_HUBSPOT_API_TOKEN>"

secrets:
  - name: "DEAL_STAGE"
    value: "<YOUR_HUBSPOT_DEAL_STAGE_ID>"
    encrypted: false
</code></pre>
</div>

### How to Find These Values

- **OpenAI API Key:** [OpenAI API Keys](https://platform.openai.com/api-keys)
- **Slack Mapping:** Usually not required unless custom mapping is configured; see [Slack App Setup](https://api.slack.com/apps)
- **SMTP Host/User/Password:** Provided by your email service provider (e.g., Gmail, Outlook, SendGrid)
- **Xero Client ID/Secret/Tenant ID/Scope:** [Xero Developer Portal](https://developer.xero.com/)
- **HubSpot API Token:** [HubSpot Private App](https://app.hubspot.com/private-apps)
- **DEAL_STAGE:** In HubSpot, go to Settings → Objects → Deals → Pipelines; copy the stage ID for your "trigger" stage

#### Additional Hardcoded IDs (Review/Replace as Needed)

- **Slack Channel ID:** `"C075PSR2A4T"` is used in notifications. To use a different channel, update the channel ID in step code or add as a secret (e.g., `SLACK_CHANNEL`).
- **HubSpot Invoiced Stage ID:** `'88987687'` is hardcoded for the "invoiced" stage. Replace with your actual stage ID if different.

---

## Sample Task (JSON)

*No example.json provided; create a sample task using the following structure as a template:*

<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-json">
{
  "items": [
    {
      "propertyValue": "YOUR_TRIGGER_DEAL_STAGE_ID",
      "propertyName": "dealstage",
      "objectId": "YOUR_DEAL_OBJECT_ID"
    }
  ]
}
</code></pre>
</div>

*Alternative: see `example.yaml` in repository for YAML format.*

---

## Troubleshooting

- **Missing or invalid connector keys/secrets:** Ensure all values in `deploy.yaml` are filled and correct.
- **OAuth errors (Slack/Xero):** Run `aloma connector oauth <connector-id>` if required.
- **HubSpot API errors:** Confirm your private app token, permissions, and deal stage IDs.
- **Xero API errors:** Check client ID/secret, tenant ID, and scopes; verify contact exists or can be created.
- **Emails not sent:** Check SMTP configuration and recipient spam folders.
- **Slack messages not delivered:** Verify Slack channel ID and connector OAuth.
- **Task not progressing or failing at a step:** Use `aloma task log <task-id> --logs --changes` to debug step-by-step.
- **Business/Dev error classification not working:** Ensure OpenAI API key is valid and has sufficient quota.
- **Hardcoded IDs:** Review and update any hardcoded Slack or HubSpot IDs as per your environment.

---

## Support

If you encounter issues, check the [Aloma documentation](https://docs.aloma.io/) or join the Community support Slack channel: [alomasupport.slack.com](https://alomasupport.slack.com/).
