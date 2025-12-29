# AI-Powered Task Routing Automation with n8n

This project contains three n8n automation workflows that demonstrate AI-powered task routing, email automation, and chat applications using Google Gemini AI models.

## Project Overview

This collection showcases how to build intelligent automation workflows using n8n's no-code/low-code platform combined with AI decision-making capabilities. Each workflow demonstrates different use cases for AI integration in business automation.

## Workflows

### 1. Smart Task Dispatcher

A workflow that handles form submissions, routes tasks based on roles, and uses AI for enhanced automation and content generation.

**Workflow File:** SmartTaskDispatcher.json

**Functionality:**
- Captures form submissions with fields: Name, Looks, and Profession
- Creates records in Airtable for task tracking
- Routes tasks based on profession type (Video Editor, Graphic Designer, Manager)
- Assigns different ratings based on profession routing
- Uses AI Agent to generate personalized poems based on submitted data
- Updates Airtable records with AI-generated content

**Workflow Steps:**
1. Form Trigger - Captures user input through a web form
2. Airtable Create - Stores initial form data in Airtable
3. Switch Node - Routes tasks based on profession field
4. Airtable Update - Updates records with profession-specific ratings
5. AI Agent - Generates creative content (poems) using Google Gemini
6. Final Airtable Update - Stores AI-generated content back to records

**Nodes Used:**
- Form Trigger - Captures user inputs
- Airtable Nodes - For creating and updating records
- Switch Node - Routes tasks based on logic conditions
- AI Agent (Tools Agent) - Core intelligence for content generation
- Google Gemini Chat Model (gemini-1.5-flash) - Powers AI responses

**Use Cases:**
- Creative or marketing teams managing requests
- Automating task classification and delegation
- Using AI to validate or augment requests
- Content generation based on user input

### 2. Email Reply Agent

An automated email management system that reads emails from Gmail, analyzes them using AI, and drafts professional, human-like replies.

**Workflow File:** EmailAgent.json

**Functionality:**
- Periodically checks Gmail inbox for unread emails (every 2 hours)
- Retrieves full email details including subject and body
- Analyzes email content using AI Agent with custom instructions
- Generates professional, personalized email replies
- Marks processed emails as read

**Workflow Steps:**
1. Schedule Trigger - Runs every 2 hours to check for new emails
2. Gmail GetAll - Fetches unread emails from inbox
3. Gmail Get - Retrieves full email details including body content
4. AI Agent - Processes email and generates reply using custom instructions
5. Gmail MarkAsRead - Marks email as processed

**AI Agent Configuration:**
The AI Agent is configured with detailed instructions including:
- Role definition as Email Reply Agent
- Primary goal: Draft professional, human-like email replies
- Secondary goal: Build trust and reputation with recipients
- User context information for personalization
- Custom instructions for email analysis and reply generation

**Nodes Used:**
- Schedule Trigger - Periodic email checking
- Gmail Nodes - Email retrieval and management
- AI Agent - Intelligent reply generation
- Google Gemini Chat Model (gemini-1.5-flash) - Natural language processing

**Use Cases:**
- Automated inbox management
- Professional email response automation
- Maintaining consistent communication standards
- Reducing manual email handling time

### 3. Chat Application

A real-time AI chat system that provides instant responses through a webhook-based architecture.

**Workflow File:** ChatApplication.json

**Functionality:**
- Receives chat messages via webhook POST requests
- Processes messages through AI Agent
- Returns intelligent responses in real-time
- No traditional backend required - fully webhook-based

**Workflow Steps:**
1. Webhook Trigger - Receives POST requests at /mychatapp endpoint
2. AI Agent - Processes incoming messages
3. Respond to Webhook - Sends AI-generated response back to client

**Nodes Used:**
- Webhook - Entry point for chat messages
- AI Agent Node - Executes AI logic
- Google Gemini Chat Model (gemini-2.0-flash) - Powers natural language understanding
- Respond to Webhook - Sends response back to frontend

**Technical Details:**
- Webhook path: /mychatapp
- HTTP Method: POST
- Request body format: { "body": { "message": "user message" } }
- Response: AI-generated text response

**Use Cases:**
- Real-time customer support chatbots
- Interactive AI assistants
- Integration with custom frontend applications
- Scalable chat solutions without traditional backend infrastructure

## Technical Stack

**Platform:** n8n (no-code/low-code automation platform)

**AI Models:**
- Google Gemini 1.5 Flash - Used in Email Agent and Smart Task Dispatcher
- Google Gemini 2.0 Flash - Used in Chat Application

**Integrations:**
- Airtable - Database and record management
- Gmail - Email processing and management
- Google Gemini API - AI language model integration

**Key n8n Nodes:**
- Form Trigger
- Webhook
- Schedule Trigger
- Airtable (Create, Update operations)
- Gmail (GetAll, Get, MarkAsRead operations)
- Switch (Conditional routing)
- AI Agent (LangChain integration)
- Respond to Webhook

## Setup Instructions

### Prerequisites
- n8n instance (self-hosted or cloud)
- Google Gemini API credentials
- Airtable account with Personal Access Token (for Smart Task Dispatcher)
- Gmail account with OAuth2 credentials (for Email Agent)

### Installation Steps

1. Import Workflow JSON files into your n8n instance
2. Configure credentials:
   - Google Gemini API credentials
   - Airtable Personal Access Token (for Smart Task Dispatcher)
   - Gmail OAuth2 credentials (for Email Agent)
3. Update workflow-specific settings:
   - Airtable base and table IDs (Smart Task Dispatcher)
   - Webhook URLs and paths (Chat Application)
   - Schedule intervals (Email Agent)
4. Activate workflows in n8n

### Configuration Notes

**Smart Task Dispatcher:**
- Configure Airtable base ID and table ID
- Update form field names to match your requirements
- Adjust profession types and ratings as needed
- Customize AI Agent prompt for different content types

**Email Agent:**
- Set appropriate schedule interval for email checking
- Configure Gmail label filters if needed
- Update system message with your user information
- Adjust email processing limits

**Chat Application:**
- Note the webhook URL generated by n8n
- Configure frontend to send POST requests to webhook endpoint
- Update request/response format as needed
- Add authentication if required for production use

## Optimization Improvements

The workflows have been optimized for better performance and reliability:

**EmailAgent.json:**
- Fixed messageId reference to use correct Gmail message ID field
- Improved email body extraction to use full text content instead of snippet
- Corrected XML formatting in AI Agent system message
- Fixed unclosed XML tags and improved structure

**SmartTaskDispatcher.json:**
- Fixed typo in AI prompt ("externly" to "extremely")
- Corrected field reference in poem generation prompt
- Improved prompt formatting for better AI understanding

**ChatApplication.json:**
- Already optimized with latest Gemini 2.0 Flash model
- Clean webhook-based architecture

## Best Practices

1. **Error Handling:** Add error handling nodes to catch and log failures
2. **Rate Limiting:** Be mindful of API rate limits for Gmail and Gemini
3. **Security:** Use environment variables for sensitive credentials
4. **Monitoring:** Set up execution monitoring and alerts in n8n
5. **Testing:** Test workflows with sample data before production use
6. **Documentation:** Keep workflow documentation updated with any customizations

## Use Case Examples

**Smart Task Dispatcher:**
- Team task intake and routing system
- Automated content generation based on user input
- Role-based task assignment and tracking

**Email Agent:**
- Automated customer support responses
- Professional email reply generation
- Inbox management and prioritization

**Chat Application:**
- Customer service chatbots
- Interactive AI assistants
- Real-time communication systems

## Limitations and Considerations

- AI responses may vary and should be reviewed for critical communications
- Gmail API has rate limits that may affect high-volume email processing
- Airtable API limits apply to record creation and updates
- Webhook-based chat requires stable network connectivity
- Customize AI prompts based on your specific use case requirements

## Future Enhancements

Potential improvements for these workflows:
- Add memory capabilities to AI Agents for context retention
- Implement error handling and retry logic
- Add logging and monitoring capabilities
- Create workflow templates for different industries
- Integrate additional AI tools and capabilities
- Add user authentication and authorization
- Implement response validation and quality checks

## Support and Maintenance

- Regularly update n8n to latest version for security and features
- Monitor API usage and costs
- Review and update AI prompts based on performance
- Test workflows after n8n updates
- Keep credentials secure and rotate regularly

## License

This project contains n8n workflow configurations for automation purposes. Ensure compliance with n8n licensing and terms of service for your use case.
