# 🤖 Notion Auto Summariser

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![n8n](https://img.shields.io/badge/n8n-workflow-orange)](https://n8n.io/)
[![Notion](https://img.shields.io/badge/Notion-API-black)](https://developers.notion.com/)
[![Google Gemini](https://img.shields.io/badge/Google-Gemini-blue)](https://ai.google.dev/)

> **Automatically summarise your Notion pages with AI-powered intelligence using n8n workflows.**

This intelligent workflow monitors your Notion database for page updates, extracts content, and generates concise AI summaries using Google Gemini (or any LLM of your choice). The generated summaries are automatically appended to your Notion pages, creating a seamless knowledge management experience.

## ✨ Features

- **🔄 Real-time Monitoring**: Automatically triggers when pages in your Notion database are updated or created
- **� Smart Content Extraction**: Intelligently aggregates all child blocks and content into structured text
- **� AI-Powered Summarisation**: Leverages Google Gemini for generating concise, contextual summaries
- **📝 Seamless Integration**: Automatically appends summaries directly to your Notion pages
- **⚡ n8n Workflow**: Easy to customize, extend, and self-host with visual workflow editor
- **🔧 LLM Flexibility**: Easily configurable to work with different AI providers (OpenAI, Claude, etc.)
- **🎯 Zero Manual Intervention**: Fully automated workflow requiring no user interaction

## 📋 Table of Contents

- [Prerequisites](#-prerequisites)
- [Quick Start](#-quick-start)
- [Installation Guide](#-installation-guide)
- [Configuration](#-configuration)
- [Workflow Overview](#-workflow-overview)
- [Usage](#-usage)
- [Screenshots](#-screenshots)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [Roadmap](#-roadmap)
- [License](#-license)
- [Support](#-support)

## 🔧 Prerequisites

Before setting up this workflow, ensure you have:

- **n8n Instance**: Either [self-hosted](https://docs.n8n.io/hosting/) or [n8n Cloud](https://n8n.io/cloud/) account
- **Notion Workspace**: With admin access to create integrations
- **Google Gemini API**: Free tier available at [Google AI Studio](https://aistudio.google.com/)
- **Basic Knowledge**: Familiarity with n8n workflows (helpful but not required)

## 🚀 Quick Start

1. **Clone this repository**
   ```bash
   git clone https://github.com/Vinay-kumar-code/Notion-Notes-AI-Summariser-N8N.git
   cd Notion-Notes-AI-Summariser-N8N
   ```

2. **Import the workflow** into your n8n instance
3. **Configure credentials** for Notion and Google Gemini
4. **Activate the workflow** and start creating/updating Notion pages!

## 📦 Installation Guide

### Step 1: Setup n8n

Choose one of the following options:

#### Option A: n8n Cloud (Recommended for beginners)
- Sign up at [n8n.io/cloud](https://n8n.io/cloud/)
- No local installation required

#### Option B: Self-hosted with Docker
```bash
docker run -it --rm --name n8n -p 5678:5678 n8nio/n8n
```

#### Option C: NPM Installation
```bash
npm install n8n -g
n8n start
```

### Step 2: Import Workflow

1. Open your n8n dashboard
2. Navigate to **Workflows** → **Import** → **From File**
3. Select `Notion Notes automatic summariser.json` from this repository
4. Click **Import**

## ⚙️ Configuration

### Notion API Setup

1. **Create a Notion Integration**
   - Go to [Notion Developers](https://www.notion.so/my-integrations)
   - Click "New Integration"
   - Name your integration (e.g., "AI Summariser")
   - Select your workspace
   - Copy the **Internal Integration Token**

2. **Share Database with Integration**
   - Open your Notion database
   - Click "Share" → "Add people, emails, groups, or integrations"
   - Search for your integration and add it

3. **Configure in n8n**
   - In n8n, go to **Credentials** → **Add Credential** → **Notion API**
   - Paste your Integration Token
   - Test the connection

### Google Gemini API Setup

1. **Get API Key**
   - Visit [Google AI Studio](https://aistudio.google.com/)
   - Click "Get API Key"
   - Create a new project or select existing
   - Generate and copy your API key

2. **Configure in n8n**
   - Go to **Credentials** → **Add Credential** → **Google PaLM API**
   - Enter your API key
   - Test the connection

### Workflow Configuration

1. **Update Database ID**
   - In the Notion Trigger node, select your target database
   - The workflow will monitor this database for changes

2. **Customize Summary Prompt** (Optional)
   - Edit the Gemini node to modify the summarization prompt
   - Adjust tone, length, or focus areas as needed

## 📊 Workflow Overview

The workflow consists of five main components:

1. **🔍 Notion Trigger**
   - Monitors your Notion database for page updates
   - Triggers every minute to check for changes
   - Captures page ID and metadata

2. **📖 Get Page Content**
   - Retrieves the updated page details
   - Fetches all child blocks and content
   - Handles various content types (text, lists, headings, etc.)

3. **📝 Content Aggregation**
   - Combines all blocks into structured text
   - Formats content for optimal AI processing
   - Maintains document hierarchy and context

4. **🤖 AI Summarisation**
   - Sends formatted content to Google Gemini
   - Generates concise, contextual summaries
   - Maintains key information and insights

5. **✍️ Append Summary**
   - Adds the generated summary to the Notion page
   - Formats summary with clear headings
   - Preserves original content structure

## 🎯 Usage

### Getting Started

1. **Activate the Workflow**
   - In n8n, switch the workflow toggle to "Active"
   - The workflow will now monitor your database

2. **Test the Integration**
   - Create or update a page in your monitored Notion database
   - Wait 1-2 minutes for processing
   - Check that a summary appears at the bottom of your page

### Best Practices

- **Page Content**: Ensure pages have substantial content for meaningful summaries
- **Database Structure**: Use consistent page templates for better results
- **Summary Formatting**: The workflow adds summaries with a clear "## AI Summary" heading
- **Performance**: Larger pages may take longer to process (30-60 seconds)

### Advanced Usage

- **Custom Prompts**: Modify the Gemini node to change summarization style
- **Multiple Databases**: Duplicate the workflow for different databases
- **Integration Chains**: Connect with other n8n workflows for extended functionality

## 📸 Screenshots

<img width="1577" height="693" alt="image" src="https://github.com/user-attachments/assets/78b46547-ed84-41c4-8e3e-12c20b95c47c" />


## 🚧 Troubleshooting

- **Workflow not triggering**: Check Notion Trigger settings and database ID
- **API key issues**: Ensure Notion and Google Gemini API keys are correct
- **Connection errors**: Test and re-save credentials in n8n
- **Summary not appearing**: Verify Append node configuration and Notion page permissions

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/YourFeature`)
3. Make your changes
4. Commit and push (`git commit -m 'Add new feature'`)
5. Submit a pull request

## 🚀 Roadmap

Planned improvements and features:

- Multi-language support
- Option to email or Slack summaries
- Custom summary length (short, medium, detailed)
- Enhanced error handling and notifications
- User-friendly dashboard for summary management

## 📜 License

GNU Public License. Free to use, modify, and share.

If you like my work, feel free to star the repo.

Open for contributions to this repo.

## 🙋 Support

For questions or support, please open an issue on GitHub or contact me directly.

Happy automating!
