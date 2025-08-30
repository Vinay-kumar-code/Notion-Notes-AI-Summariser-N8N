# 🤖 Notion Auto Summariser

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![n8n](https://img.shields.io/badge/n8n-workflow-orange)](https://n8n.io/)
[![Notion](https://img.shields.io/badge/Notion-API-black)](https://developers.notion.com/)
[![Google Gemini](https://img.shields.io/badge/Google-Gemini-blue)](https://ai.google.dev/)

> **Automatically summarise your Notion pages with AI-powered intelligence using n8n workflows.**

This intelligent workflow monitors your Notion database for page updates, extracts content, and generates concise AI summaries using Google Gemini (or any LLM of your choice). The generated summaries are automatically appended to your Notion pages, creating a seamless knowledge management experience.

## ✨ Features

- **🔄 Real-time Monitoring**: Automatically triggers when pages in your Notion database are updated or created
- **📄 Smart Content Extraction**: Intelligently aggregates all child blocks and content into structured text
- **🧠 AI-Powered Summarisation**: Leverages Google Gemini for generating concise, contextual summaries
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

<div align="center">
  <img width="1577" height="693" alt="n8n Workflow Overview - Notion AI Summariser" src="https://github.com/user-attachments/assets/78b46547-ed84-41c4-8e3e-12c20b95c47c" />
  <p><em>Complete n8n workflow showing all nodes and connections</em></p>
</div>

## 🔍 Troubleshooting

### Common Issues

#### **Issue**: Workflow not triggering
**Solution**: 
- Verify the Notion trigger is configured with the correct database ID
- Ensure the Notion integration has access to your database
- Check that the workflow is active in n8n

#### **Issue**: "Unauthorized" errors
**Solution**:
- Refresh your Notion API credentials in n8n
- Verify the integration token has the correct permissions
- Re-share the database with your Notion integration

#### **Issue**: Empty or poor summaries
**Solution**:
- Ensure pages have substantial text content (minimum 100 words recommended)
- Check that the Google Gemini API key is valid
- Review the AI prompt in the Gemini node for customization

#### **Issue**: Summaries appear multiple times
**Solution**:
- The workflow may be triggering multiple times
- Add a condition to check if a summary already exists
- Consider adjusting the trigger polling frequency

### Debug Tips

- **Check Execution History**: Review failed executions in n8n's execution history
- **Test Individual Nodes**: Use n8n's test functionality to debug specific nodes
- **Monitor API Limits**: Both Notion and Gemini have rate limits that may affect performance

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

### Ways to Contribute

- **🐛 Bug Reports**: Submit detailed bug reports with reproduction steps
- **💡 Feature Requests**: Suggest new features or improvements
- **📝 Documentation**: Help improve documentation and tutorials
- **🔧 Code Contributions**: Submit pull requests with enhancements
- **🎨 UI/UX**: Suggest workflow improvements or visual enhancements

### Development Setup

1. Fork this repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes and test thoroughly
4. Submit a pull request with a clear description

### Code Standards

- Follow existing code formatting and structure
- Test your changes with real Notion pages
- Update documentation for any new features
- Ensure backward compatibility when possible

## 🗺️ Roadmap

### Upcoming Features

- **🌍 Multi-language Support**
  - Support for non-English content summarization
  - Language-specific prompt optimization
  - Auto-detection of content language

- **📧 Notification Options**
  - Email summaries to specified recipients
  - Slack integration for team notifications
  - Discord webhook support

- **⚙️ Advanced Customization**
  - Multiple summary length options (short, medium, detailed)
  - Custom AI prompts per database
  - Template-based summary formatting

- **📊 Analytics & Insights**
  - Summary generation statistics
  - Content analysis metrics
  - Performance monitoring dashboard

- **🔄 Enhanced Integration**
  - Support for other AI providers (OpenAI GPT, Claude, etc.)
  - Database field mapping for metadata
  - Conditional summarization based on page properties

### Community Requests

Vote on features and suggest new ones in our [GitHub Issues](https://github.com/Vinay-kumar-code/Notion-Notes-AI-Summariser-N8N/issues)!

## 📜 License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.

**Free to use, modify, and share** under the terms of the GPL v3.0 license.

## 🙋 Support

### Getting Help

- **📚 Documentation**: Check this README for comprehensive setup instructions
- **🐛 Issues**: Report bugs or request features via [GitHub Issues](https://github.com/Vinay-kumar-code/Notion-Notes-AI-Summariser-N8N/issues)
- **💬 Discussions**: Join the conversation in [GitHub Discussions](https://github.com/Vinay-kumar-code/Notion-Notes-AI-Summariser-N8N/discussions)
- **📧 Contact**: Reach out to the maintainer for direct support

### Show Your Support

If this project helped you, please consider:

- ⭐ **Star this repository** to show your appreciation
- 🍴 **Fork the project** to contribute your improvements
- 📢 **Share with others** who might find it useful
- 💝 **Contribute** to make it even better

---

<div align="center">
  <p>Made with ❤️ by <a href="https://github.com/Vinay-kumar-code">Vinay Kumar</a></p>
  <p>Happy automating! 🚀</p>
</div>
