# Deal to Invoice Automation for Squadify

**Turn closed deals into invoices—automatically and reliably, so your team can focus on what matters most.**

---

## What This Automation Does (In Simple Terms)

- Watches for deals marked as "ready to invoice" in your HubSpot system.
- Gathers all the important details about the deal, company, and contacts.
- Checks that nothing is missing or incorrect.
- Creates an invoice in Xero using those details.
- Adds the invoice link back to the original deal in HubSpot for easy tracking.
- Moves the deal to the "invoiced" stage to keep your pipeline tidy.
- Notifies your team on Slack and by email about progress or any issues.
- Explains any problems in clear, business-friendly language.

---

## Step-by-Step Breakdown

### 1. Gather Deal Details

- **Step Name:** Gather Deal Details
- **What happens:** The automation looks for deals in HubSpot that have reached the "ready to invoice" stage and collects all the related information (company, contact, products/services).
- **Real-world comparison:** Like a filing clerk pulling together all the paperwork for a new client folder when a sale is marked as complete.
- **Why it matters:** Ensures nothing is missed and all the information needed for the next steps is in one place.
- **Dependencies:** The list of deals and their stages in HubSpot must be kept up to date. Make sure deals are moved to the correct stage when they’re ready.

---

### 2. Check for Missing Information

- **Step Name:** Check for Missing Information
- **What happens:** The automation reviews the gathered details to make sure everything needed for an invoice is present (amount, company, contact, line items).
- **Real-world comparison:** Like a personal assistant double-checking a checklist before sending out an important document.
- **Why it matters:** Prevents errors and delays by catching missing or incorrect details early.
- **Dependencies:** Company, contact, and line item details in HubSpot must be filled in and accurate.

---

### 3. Create Invoice in Xero

- **Step Name:** Create Invoice in Xero
- **What happens:** Using the checked details, the automation creates a new invoice in Xero, making sure the right customer and items are included.
- **Real-world comparison:** Like an office manager entering all the details into the company’s billing system to generate an invoice.
- **Why it matters:** Saves time and reduces mistakes compared to manual entry, ensuring invoices go out quickly.
- **Dependencies:** Xero account must be set up and connected. Customer details in Xero should match those in HubSpot.

---

### 4. Add Invoice Link to Deal

- **Step Name:** Add Invoice Link to Deal
- **What happens:** The automation adds the link to the new invoice and its number back into the original HubSpot deal for easy reference.
- **Real-world comparison:** Like a clerk stapling a copy of the invoice to the client’s file so anyone can find it later.
- **Why it matters:** Keeps everyone on the same page and makes it easy to find invoices without searching in multiple places.
- **Dependencies:** HubSpot deal records must allow for custom fields or notes to store invoice links.

---

### 5. Move Deal to "Invoiced" Stage

- **Step Name:** Move Deal to "Invoiced" Stage
- **What happens:** The automation updates the deal’s stage in HubSpot to show it’s been invoiced and sends a confirmation email and Slack message to the team.
- **Real-world comparison:** Like moving a folder to the “completed” drawer and letting the team know the job is done.
- **Why it matters:** Keeps your sales pipeline organized and your team informed, so nothing falls through the cracks.
- **Dependencies:** HubSpot pipeline stages must be set up correctly, and team notification channels (Slack/email) must be maintained.

---

### 6. Explain and Notify About Errors

- **Step Name:** Explain and Notify About Errors
- **What happens:** If something goes wrong, the automation uses a smart assistant to figure out if it’s a business issue (like missing info) or a technical one, and sends a clear explanation to the right people.
- **Real-world comparison:** Like a help desk agent who not only spots a problem but also tells you exactly what’s wrong and how to fix it, in plain English.
- **Why it matters:** Makes troubleshooting fast and stress-free, so issues get resolved quickly.
- **Dependencies:** Email addresses and Slack channels for notifications must be current. HubSpot and Xero access must be maintained.

---

### 7. Troubleshooting and Debugging

- **Step Name:** Troubleshooting and Debugging
- **What happens:** The automation can run extra checks and gather details to help fix any technical issues.
- **Real-world comparison:** Like calling in a specialist to dig deeper when something unusual happens.
- **Why it matters:** Helps your technical team quickly get to the bottom of any problems.
- **Dependencies:** Access to HubSpot and Xero must be kept up to date for these checks to work.

---

## Decision Points (for Branching Logic)

### Error Handling

- **Decision:** If the automation finds missing or incorrect information, or if something goes wrong when creating the invoice, it decides how to handle the issue.
- **Path A (Business Issue):** If the problem is something like missing deal details or a mismatch between systems, the automation sends a clear, friendly explanation to the business team so they can fix it.
    - Steps in this path: Explain and Notify About Errors
- **Path B (Technical Issue):** If the problem is a technical hiccup, the automation gathers details and notifies the technical team for a quick fix.
    - Steps in this path: Troubleshooting and Debugging

This way, the right people get the right information, and nothing gets stuck or lost.

---

## Impact Section

### What Makes This Special

- **Speed:** Invoices are created as soon as deals are ready—no waiting for manual entry.
- **Accuracy:** Double-checks every detail, so invoices are always correct.
- **Consistency:** Every deal is handled the same way, every time.
- **Cost Benefits:** Frees up your team from repetitive tasks, letting them focus on building relationships and closing more deals.

---

### Before vs After

| Before Automation                  | After Automation                                 |
|------------------------------------|--------------------------------------------------|
| Manual data entry, prone to errors | Automatic, reliable, and error-checked           |
| Chasing missing info by email      | Smart assistant flags missing details instantly  |
| Delays in invoicing                | Invoices created as soon as deals are ready      |
| Team unsure if invoice is sent     | Everyone notified and deal status always clear   |

---

### Who Benefits

- **Sales Team:** No more double entry or chasing invoices—focus on selling!
- **Finance Team:** Invoices are always accurate and on time, with all details in one place.
- **Operations Managers:** Clear, up-to-date pipeline and fewer manual checks.
- **Business Owners:** Faster cash flow, fewer mistakes, and happier customers.

---

## Conclusion

**Bottom Line:**  
This automation acts like a super-reliable personal assistant for your sales and finance teams. It takes care of the repetitive, detail-heavy work of turning deals into invoices—quickly, accurately, and with friendly notifications—so your people can focus on what really matters: growing your business and building great relationships.

---

## Support

If you need help or have questions, check the [Aloma documentation](https://docs.aloma.io/) or join the Community support Slack channel: [alomasupport.slack.com](https://alomasupport.slack.com/).
