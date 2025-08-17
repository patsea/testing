
# Smart Lead Processing Assistant

**Your automated helper that captures and organizes new business contacts from multiple sources - working 24/7 so you don't have to**

## What This Automation Does (In Simple Terms)

• **Captures new contacts** from various business networking tools automatically
• **Organizes information** into a standard format regardless of where it came from  
• **Routes contacts** to the right systems based on their job title and importance
• **Sends notifications** when high-priority contacts need immediate attention
• **Creates documents** automatically for important prospects using AI assistance

## Step-by-Step Breakdown

### Step 1: Process Google Form Task
**What happens:** When someone submits a test form, the system loads sample contact data for testing
**Real-world comparison:** Like a receptionist pulling a practice file to train a new employee
**Why it matters:** Allows you to test the entire process without using real customer data
**Dependencies:** None - this is just for testing purposes

### Step 2: Fetch Event from HubSpot
**What happens:** Retrieves complete contact details when HubSpot sends a notification
**Real-world comparison:** Like looking up a customer's full file when their name appears on your desk
**Why it matters:** Ensures you have all the information needed to process the contact properly
**Dependencies:** Contact must exist in HubSpot with basic information filled out

### Step 3: Normalize HubSpot Data
**What happens:** Converts HubSpot contact information into a standard format
**Real-world comparison:** Like a filing clerk transferring information from different forms onto a standard index card
**Why it matters:** Makes it possible to handle contacts the same way regardless of source
**Dependencies:** HubSpot contacts need standard fields populated (name, email, company)

### Step 4: Normalize Waalaxy Data
**What happens:** Converts LinkedIn contact information from Waalaxy into standard format
**Real-world comparison:** Like transcribing business cards into your address book
**Why it matters:** Allows LinkedIn connections to be processed alongside other contacts
**Dependencies:** Waalaxy must be configured to send contact data when connections are made

### Step 5: Normalize Dripify Data
**What happens:** Converts LinkedIn automation data from Dripify into standard format
**Real-world comparison:** Like a secretary organizing notes from different meetings into one format
**Why it matters:** Ensures LinkedIn outreach contacts are captured and processed consistently
**Dependencies:** Dripify campaigns must include all required contact fields

### Step 6: Normalize DataGardener Data
**What happens:** Converts enriched contact data from DataGardener into standard format
**Real-world comparison:** Like a research assistant organizing findings into a standard report
**Why it matters:** Captures enhanced contact information for better follow-up
**Dependencies:** DataGardener must have valid contact enrichment data

### Step 7: Normalize Apollo Data
**What happens:** Converts sales contact data from Apollo into standard format
**Real-world comparison:** Like transferring leads from a trade show list into your contact system
**Why it matters:** Ensures sales-sourced contacts are processed with the same care
**Dependencies:** Apollo sequences must capture email actions (inquiry, trial request)

### Step 8: If CEO
**What happens:** Identifies CEO contacts for special VIP treatment
**Real-world comparison:** Like flagging mail from the company president for immediate attention
**Why it matters:** Ensures your most important prospects get white-glove service
**Dependencies:** Job title field must be accurately populated in source system

### Step 9: If CFO
**What happens:** Identifies CFO contacts for priority financial discussions
**Real-world comparison:** Like routing financial inquiries directly to your accounting team
**Why it matters:** Financial decision-makers often have urgent needs and buying power
**Dependencies:** Job title must clearly indicate CFO or equivalent role

### Step 10: If CMO
**What happens:** Identifies CMO contacts for marketing-focused follow-up
**Real-world comparison:** Like directing marketing materials to the right department head
**Why it matters:** Marketing executives need different information than other contacts
**Dependencies:** Job title must indicate marketing leadership role

### Step 11: Waalaxy Email Replied
**What happens:** Flags contacts who replied to LinkedIn messages for immediate action
**Real-world comparison:** Like a receptionist running to tell you an important client is on the phone
**Why it matters:** Quick response to engaged prospects dramatically improves conversion
**Dependencies:** Waalaxy must track message reply status accurately

### Step 12: Dripify Premium Lead
**What happens:** Identifies premium LinkedIn members who showed interest
**Real-world comparison:** Like noting when a VIP customer walks into your store
**Why it matters:** Premium members are often serious business professionals worth prioritizing
**Dependencies:** Dripify must identify LinkedIn premium status

### Step 13: DataGardener Email
**What happens:** Routes contacts with verified email addresses to appropriate systems
**Real-world comparison:** Like sorting mail into boxes based on having a return address
**Why it matters:** Contacts with email can be reached directly for follow-up
**Dependencies:** DataGardener must successfully find and verify email addresses

### Step 14: Apollo Inquiry Lead
**What happens:** Handles contacts who submitted inquiries through Apollo campaigns
**Real-world comparison:** Like flagging customers who asked to speak with a manager
**Why it matters:** Direct inquiries indicate high interest and should be handled quickly
**Dependencies:** Apollo campaigns must track inquiry responses

### Step 15: Apollo Trial Lead
**What happens:** Processes contacts who requested a product trial
**Real-world comparison:** Like a car dealer preparing for a test drive appointment
**Why it matters:** Trial requests are the strongest buying signals and need immediate attention
**Dependencies:** Apollo must capture trial request actions from email campaigns

### Step 16: Create HubSpot Contact
**What happens:** Prepares contact information in the format HubSpot requires
**Real-world comparison:** Like filling out a customer information card for filing
**Why it matters:** Ensures all contacts are properly tracked in your main customer system
**Dependencies:** HubSpot must have required fields configured

### Step 17: Create Airtable Contact
**What happens:** Formats contact data for your spreadsheet-style tracking system
**Real-world comparison:** Like entering a new row in your customer ledger
**Why it matters:** Provides a backup system and easy reporting access
**Dependencies:** Airtable base must have matching column names

### Step 18: Create Apollo Contact
**What happens:** Prepares contact for addition to Apollo sales sequences
**Real-world comparison:** Like adding a prospect to your sales call list
**Why it matters:** Enables automated follow-up campaigns
**Dependencies:** Apollo account must have available contact slots

### Step 19: Write Contact to HubSpot
**What happens:** Actually saves the contact in HubSpot's system
**Real-world comparison:** Like filing the completed customer card in your filing cabinet
**Why it matters:** Makes the contact available for all HubSpot features and reporting
**Dependencies:** HubSpot connection must have write permissions

### Step 20: Write Contact to Airtable
**What happens:** Adds the contact as a new row in your Airtable
**Real-world comparison:** Like writing a new entry in your customer log book
**Why it matters:** Creates a searchable, sortable record outside your main system
**Dependencies:** Airtable base must be shared with proper permissions

### Step 21: Write Contact to Apollo
**What happens:** Creates the contact in Apollo for sales outreach
**Real-world comparison:** Like adding someone to your phone's contact list
**Why it matters:** Enables automated sales sequences and tracking
**Dependencies:** Apollo API access must be active with sufficient credits

### Step 22: Write Apollo Contact to Sequence
**What happens:** Enrolls specific contacts in automated follow-up campaigns
**Real-world comparison:** Like signing someone up for your newsletter
**Why it matters:** Ensures consistent follow-up without manual effort
**Dependencies:** Apollo sequence must be created and active

### Step 23: ChatGPT
**What happens:** Generates personalized email content for trial requests
**Real-world comparison:** Like having a copywriter draft a custom letter
**Why it matters:** Provides professional, personalized communication at scale
**Dependencies:** Email template context must be properly configured

### Step 24: ChatGPT Doc
**What happens:** Creates longer-form content for VIP prospects
**Real-world comparison:** Like having an assistant prepare a detailed proposal
**Why it matters:** Important prospects deserve customized, thoughtful materials
**Dependencies:** Document templates and context must be set up

### Step 25: Message to Google Doc
**What happens:** Saves generated content to a shared document
**Real-world comparison:** Like typing up meeting notes and filing them
**Why it matters:** Creates a permanent record that teams can review and edit
**Dependencies:** Google Doc must be created and shared with proper permissions

### Step 26: Message to Email
**What happens:** Sends notification emails to your team
**Real-world comparison:** Like leaving a note on someone's desk about an important call
**Why it matters:** Ensures human team members know when their attention is needed
**Dependencies:** Email addresses must be valid and monitored

### Step 27: Message to Slack
**What happens:** Posts updates to your team chat channel
**Real-world comparison:** Like making an announcement in the break room
**Why it matters:** Provides real-time visibility of important activities
**Dependencies:** Slack channel must exist and team must have access

### Step 28: Message to ServiceNow
**What happens:** Creates support tickets for issues requiring follow-up
**Real-world comparison:** Like filling out a work order for maintenance
**Why it matters:** Ensures nothing falls through the cracks
**Dependencies:** ServiceNow must have proper ticket categories configured

### Step 29: Service Now Information
**What happens:** Processes incoming ServiceNow requests
**Real-world comparison:** Like checking your inbox for new work assignments
**Why it matters:** Allows the system to respond to internal team requests
**Dependencies:** ServiceNow must be configured to send webhook notifications

### Step 30: Netcom Urgency 1
**What happens:** Handles high-priority ServiceNow tickets immediately
**Real-world comparison:** Like a fire alarm that requires immediate response
**Why it matters:** Critical issues get addressed without delay
**Dependencies:** ServiceNow urgency levels must be properly set

### Step 31: Netcom Urgency 2
**What happens:** Routes standard priority tickets for normal processing
**Real-world comparison:** Like regular mail that can be handled during business hours
**Why it matters:** Balances quick response with efficient resource use
**Dependencies:** ServiceNow ticket priorities must be consistently applied

### Step 32: ComposeDoc Task
**What happens:** Handles requests to create new documents
**Real-world comparison:** Like asking an assistant to draft a letter
**Why it matters:** Automates document creation based on team requests
**Dependencies:** ServiceNow must include clear document requirements

### Step 33: End If Nothing To Do
**What happens:** Gracefully closes tasks that don't require any action
**Real-world comparison:** Like filing a "no action needed" report
**Why it matters:** Prevents system resources from being wasted
**Dependencies:** None - this is a cleanup step

## Decision Points

### Path A: VIP Contact Processing (CEO/CFO/CMO)
When the system identifies an executive-level contact, it follows a special high-priority path:
- If CEO
- ChatGPT Doc
- Message to Google Doc
- Message to Email
- Message to ServiceNow

### Path B: Engaged Contact Processing
When contacts show high engagement (replies, inquiries, trial requests), they get immediate attention:
- Waalaxy Email Replied
- Apollo Inquiry Lead
- Apollo Trial Lead
- ChatGPT
- Message to Email
- Message to ServiceNow

### Path C: Standard Contact Processing
Regular contacts are efficiently processed and stored for future outreach:
- Create HubSpot Contact
- Create Airtable Contact
- Create Apollo Contact
- Write Contact to HubSpot
- Write Contact to Airtable
- Write Contact to Apollo
- Message to Slack

## What Makes This Special

**Speed:** Processes new contacts in seconds instead of hours of manual data entry

**Accuracy:** Eliminates typos and missing information that happen with manual processing

**Consistency:** Every contact is handled the same way, every time, following your best practices

**Cost Savings:** One automated assistant doing the work of multiple data entry specialists

## Before vs After

**Before:**
- Sales reps spending 2-3 hours daily on data entry
- Contacts from different sources handled inconsistently  
- 24-48 hour delay before new leads get attention
- Important contacts sometimes missed in the shuffle
- Manual copying between multiple systems

**After:**
- Sales reps focus on building relationships
- All contacts processed identically regardless of source
- New leads processed within minutes, 24/7
- VIP contacts automatically flagged and prioritized
- Information flows seamlessly between all your systems

## Who Benefits

**Sales Teams:** Spend time selling instead of data entry, never miss a hot lead

**Marketing Teams:** See all lead sources in one place, measure what's working

**Executives:** Get instant alerts about VIP prospects, see real-time pipeline growth

**Operations Teams:** Reduce errors, ensure compliance, scale without adding headcount

**Customers:** Receive faster responses and more personalized attention

## Bottom Line

This automation acts like a tireless assistant who never takes a break, never makes mistakes, and ensures every potential customer gets the attention they deserve. It's not about replacing people - it's about freeing them to do what humans do best: build relationships, solve problems, and grow the business.

## Support

If you need help with this automation, reach out to your automation team or visit the community support channel at alomasupport.slack.com.
