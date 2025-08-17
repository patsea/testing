# Automated Industry and Company News Research & Outreach Workflow

**Streamlines industry/company news research, PDF generation, and personalised outreach for investment banking using AI and Google Workspace.**

---

## What This Workflow Does

This workflow automates the end-to-end process of gathering industry and company-specific news, generating research reports, creating PDFs, storing them in Google Drive, updating Google Sheets, and sending personalised outreach emails. It leverages AI (Perplexity, Claude) for research and message generation, integrates with Google Sheets and Drive for data management, and uses SMTP for email delivery. Designed for investment banking teams needing to efficiently prepare for client meetings and execute targeted outreach based on up-to-date market intelligence.

---

## Workflow Steps

| Step Name                     | Trigger Condition                                                                 | Action                                                      |
|-------------------------------|----------------------------------------------------------------------------------|-------------------------------------------------------------|
| get google sheet data         | `{ "getData": true }`                                                            | Reads company/industry data from Google Sheet               |
| get company news - step 1     | `{ "getCompanyNews": true, "companies": Array, "nextStep": 1 }`                  | Prepares for company news subtasks, manages batch index     |
| get company news - step 2     | `{ "getCompanyNews": true, "nextStep": 2 }`                                      | Launches batch subtasks to fetch company news via AI        |
| get company news - subtask    | `{ "runsubtask": true }`                                                         | Uses Perplexity to research and summarise company news      |
| email message construction    | `{ "getCompanyNews": true, "companies": [{ "response": Object }], "nextStep": 3 }` | Generates personalised outreach email using Claude AI       |
| add to google sheet           | `{ "companies": [{ "message": String }] }`                                       | Updates Google Sheet with email subject/message, marks as processed |
| get industry news - part 1    | `{ "getIndustryNews": true, "companies": Array, "nextStep": 1 }`                 | Uses Perplexity to generate industry news report            |
| get industry news - part 2    | `{ "getIndustryNews": true, "companies": Array, "nextStep": 2 }`                 | Manages batch index for company news subtasks               |
| get industry news - part 3    | `{ "getIndustryNews": true, "nextStep": 3 }`                                     | Launches batch subtasks to fetch company news for industry  |
| get industry news - subtask   | `{ "runsubtask2": true }`                                                        | Uses Perplexity to research and summarise company news (industry context) |
| get industry news - part 4    | `{ "getIndustryNews": true, "nextStep": 4 }`                                     | Aggregates industry and company news into single report     |
| generate pdf                  | `{ "generatePDF": true }`                                                        | Generates PDF from HTML research using Document Generation  |
| save to google drive folder   | `{ "pdfCreated": true }`                                                         | Uploads PDF to Google Drive and updates Google Sheet        |
| email industry news           | `{ "sendEmail": true }`                                                          | Sends industry news PDF link via SMTP email                 |

---

## Integrations used in example

- [Google Sheets](https://developers.google.com/sheets/api) – Read/write company and outreach data
- [Google Drive](https://developers.google.com/drive/api) – Store generated PDFs
- [Perplexity AI](https://docs.perplexity.ai/) – AI-powered news and research summarisation
- [Claude AI](https://docs.anthropic.com/claude/reference/complete_post) – AI-powered email message generation
- [Document Generation](https://docs.aloma.io/connectors/document-generation) – Convert HTML research to PDF
- [E-Mail (SMTP)](https://nodemailer.com/smtp/) – Send outreach emails

---

## Setup Instructions (CLI)

<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-bash">
git clone &lt;repository-url&gt;
cd &lt;workflow-directory&gt;

# Edit deploy.yaml with your connector keys and secrets (see below)

aloma deploy deploy.yaml

# (If required) Complete OAuth for Google Sheets, Google Drive, and SMTP
aloma connector list
aloma connector oauth &lt;connector-id&gt;

# Test with a sample task
aloma task new "test industry news" -f example.json

# View task logs
aloma task log &lt;task-id&gt; --logs --changes
</code></pre>
</div>

---

## Configuration (Connectors & Secrets)

Edit `deploy.yaml` and update the following sections with your actual credentials and IDs:

<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-yaml">
connectors:
  - connectorName: "Document Generation"
  - connectorName: "E-Mail (SMTP)"
    config:
      smtpUser: "&lt;YOUR_SMTP_USER&gt;"
      smtpPassword: "&lt;YOUR_SMTP_PASSWORD&gt;"
      smtpHost: "&lt;YOUR_SMTP_HOST&gt;"
  - connectorName: "Claude-ai"
    config:
      apiKey: "&lt;YOUR_CLAUDE_API_KEY&gt;"
  - connectorName: "Google Sheets"
    config:
      googleServiceAccountKey: "&lt;YOUR_GOOGLE_SERVICE_ACCOUNT_KEY&gt;"
  - connectorName: "Google Drive"
    config:
      googleServiceAccountKey: "&lt;YOUR_GOOGLE_SERVICE_ACCOUNT_KEY&gt;"
  - connectorName: "Perplexity"
    config:
      apiKey: "&lt;YOUR_PERPLEXITY_API_KEY&gt;"

secrets:
  - name: "GOOGLE_SHEET"
    value: "&lt;YOUR_GOOGLE_SHEET_ID&gt;"
    encrypted: false
  - name: "GOOGLE_DRIVE_FOLDER"
    value: "&lt;YOUR_GOOGLE_DRIVE_FOLDER_ID&gt;"
    encrypted: false
</code></pre>
</div>

### How to find these values

- **GOOGLE_SHEET**: The ID from your Google Sheets URL (the string between `/d/` and `/edit`).
- **GOOGLE_DRIVE_FOLDER**: The folder ID from your Google Drive folder URL.
- **Google Service Account Key**: Create a service account in Google Cloud Console, enable Sheets/Drive API, and download the JSON key.
- **Perplexity API Key**: [Get from Perplexity AI dashboard](https://www.perplexity.ai/settings/api).
- **Claude AI API Key**: [Get from Anthropic account](https://console.anthropic.com/).
- **SMTP Credentials**: Provided by your email service provider (e.g., Gmail, SendGrid, Outlook).

---

## Sample Task (JSON)

<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-json">
{
  "getData": true,
  "getCompanyNews": true,
  "getIndustryNews": false,
  "companies": [
    {
      "Client name": "Example Telecom",
      "Business Industry Type": "Telecom",
      "Business Development Phase": "Growth",
      "rowIndex": 2
    }
  ]
}
</code></pre>
</div>

*Alternative: see `example.yaml` in repository.*

---

## Troubleshooting

- **Missing or invalid connector keys/secrets**: Ensure all values in `deploy.yaml` are filled and correct.
- **Google Sheets/Drive OAuth**: Run `aloma connector oauth <connector-id>` if required.
- **Perplexity/Claude API errors**: Confirm your API keys and account permissions.
- **Emails not sent**: Check SMTP configuration and recipient spam folders.
- **PDFs not generated or uploaded**: Verify Document Generation and Google Drive connector settings.
- **Sheet not updated**: Confirm Google Sheets ID and service account permissions.
- **Task not progressing**: Use `aloma task log <task-id> --logs --changes` to debug step-by-step.

---

## Support

For issues or questions, check the [Aloma documentation](https://docs.aloma.io/) or join the Community support Slack channel: [alomasupport.slack.com](https://alomasupport.slack.com/).
