## Notion Auto Summariser (n8n Workflow)

Automatically summarise your Notion pages with n8n + Google Gemini (PaLM).
This workflow watches for new or updated pages in your Notion database, extracts their content, sends it to Gemini for summarisation, and appends the summary back into the same page.

🚀 Features

🔄 Auto-trigger: Runs whenever a page in your Notion database is updated.

📑 Content aggregation: Collects all child blocks into one text file.

🤖 AI-powered summarisation: Uses Google Gemini (PaLM) to generate concise summaries.

📝 In-page summary: Appends the generated summary to the bottom of the same Notion page.

⚡ n8n powered: Easy to customise, extend, or self-host.

🛠️ Setup Instructions
1. Requirements

n8n
 installed (self-hosted or cloud).

A Notion API integration with access to your database.

A Google Gemini (PaLM) API key.

2. Import the Workflow

Clone this repo:

git clone https://github.com/YOUR_USERNAME/notion-auto-summariser-n8n.git


In your n8n dashboard, go to Workflows → Import → From File.

Select the Notion Notes automatic summariser.json file.

3. Configure Credentials

Notion API: Add your integration token in n8n’s Credentials → Notion.

Google Gemini (PaLM): Add your API key in Credentials → Google PaLM API.

4. Run It

Activate the workflow.

Update or add a page in your Notion database.

The workflow will fetch content → summarise with Gemini → append summary to your page.

📂 Workflow Overview

Trigger: Watches for Notion database page updates.

Get Page + Child Blocks: Fetches full content.

Aggregate & Format: Combines blocks into one text file.

Summarise: Sends content to Gemini for AI summarisation.

Append: Writes the summary back into the Notion page.

📸 Screenshots

(Add screenshots of your workflow canvas and a Notion page before/after summarisation here.)

🔮 Future Improvements

Multi-language support.

Option to email or Slack summaries.

Custom summary length (short, medium, detailed).

📜 License

MIT License. Free to use, modify, and share.
