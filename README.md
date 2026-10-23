**🚀 Automated Lead Follow-Up System**
An automated lead-nurturing pipeline built using n8n, Google Sheets, Google Gemini AI,
and Gmail.
This workflow detects non-responsive leads, leverages Google Gemini to draft personalized follow-up emails,
dispatches them via Gmail, and logs the execution status in real time.

**🛠️ Prerequisites**
Before getting started, make sure you have:
An active n8n instance (either n8n Cloud or self-hosted via Docker/Podman)
Google Account with access to:Google Sheets (containing your leads database).
Gmail (used to dispatch follow-up emails).Google Gemini API Key (from Google AI Studio)
.📋 Google Sheet Setup
Ensure your target Google Sheet includes the following column headers in the primary sheet:
Column Name
PurposeNameLead's full name

EmailLead's primary email
addressI
NQUIRY
Original inquiry or message from the lead
StatusUpdated automatically (e.g., Email Sent)
AI Draft SubjectStores the AI-generated email subject lineDates Followed upLogs timestamp of the follow-up 

**Setup & Installation Guide**

Step 1: Import the Workflow JSON into n8nLog into your n8n Dashboard.
Click Workflows in the left sidebar menu, then click + Create Workflow (or open an empty workflow).
In the top-right corner of the workflow canvas, click the ... (three dots) menu.
Select Import from File.Select the exported .json file from this repository to load the entire pipeline onto your canvas.

Step 2: Configure CredentialsOpen each node in the imported workflow to authorize your accounts:Google Sheets Trigger & Update Nodes:Connect your Google Sheets OAuth2 API account.
Select your target Spreadsheet and Sheet name.Google Gemini AI Node (Message a model):Add/select your Google Gemini API Key.Gmail Node (Send a message):Connect your Gmail OAuth2 account.

Step 3: Activate the WorkflowReview all node connections to ensure no configuration warnings remain.Look at the top-right corner of the workflow canvas.
Toggle the workflow switch from Inactive to Active (Green).
Note: Once activated, the n8n Cloud or background instance will continuously listen for trigger events 24/7 without requiring manual intervention.

**🧪 Testing the Pipeline**

Submit a test inquiry via your connected Google Form or manually add a new lead row to your Google Sheet
.Observe the automated process:n8n captures the new/unprocessed row.
<img width="1353" height="612" alt="Screenshot from 2026-10-23 13-55-48" src="https://github.com/user-attachments/assets/8ef2ff89-2f31-4132-81e7-b0926d8aead9" />
Gemini AI generates a personalized follow-up subject and body based on the INQUIRY text.Gmail sends the email to the lead's address.
Google Sheets updates the row's Status to Email Sent and records the Dates Followed up timestamp.
