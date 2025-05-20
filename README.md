

# 🤖 AI-Powered Task Routing Automation with n8n


 I tried something interesting with **[n8n](https://n8n.io/)** — a no-code/low-code automation platform — and built a working automation that brings together **AI decision-making and smart task routing**.

---

## 📋 Workflow Overview

**Smart task dispatcher** [👉 View Workflow JSON](https://github.com/rohan5576/n8n_Automations/blob/main/workflows/email_reply_agent.json)

![Smart Task Dispatcher](https://github.com/rohan5576/n8n_Automations/blob/main/images/smart_task_dispatcher.png?raw=true)

This n8n workflow acts as a **smart task dispatcher**, handling form inputs, routing tasks based on roles, and using AI for enhanced automation.

### 🔄 Step-by-Step Flow

1. **📝 On Form Submission**
   - The workflow is triggered when a form is submitted (e.g., task request or role selection).

2. **📤 Airtable Record Creation**
   - Captures the form data and creates a new record in Airtable.

3. **🔀 Switch Logic (Routing)**
   - A Switch node checks the role or task type (e.g., Graphic Designer or Manager).
   - Based on the condition, it updates the appropriate Airtable table.

4. **🤖 AI Agent Integration**
   - An AI Agent processes the input using:
     - A Chat Model (Google Gemini),
     - Toolset and Memory capabilities,
     - Real-time Google Search if required.
   - It can enhance, validate, or suggest next steps for the request.

5. **📁 Final Airtable Update**
   - The AI output is stored back in another Airtable record for tracking or further use.


## 🛠️ Tools & Nodes Used

- **Form Trigger** – To capture user inputs.
- **Airtable Nodes** – For creating and updating records.
- **Switch Node** – Routes tasks based on logic.
- **AI Agent (Tools Agent)** – The core intelligence, enriched with memory and tools.
- **Google Gemini Chat Model** – For understanding and responding to inputs.
- **Google Search Tool** – Adds dynamic, real-time context if needed.


## 🎯 Use Case

This setup can serve as a **lightweight AI-driven task intake and routing system**. Perfect for:
- Creative or marketing teams managing requests.
- Automating task classification and delegation.
- Using AI to validate or augment requests.


## 💡 Why This?

By combining **n8n’s workflow automation** with **AI reasoning**, this project explores how you can quickly scale smart operations — all with minimal code.


---



# 📬 AI-Powered Email Reply Agent (n8n Automation)

This project demonstrates how to use **n8n** and an **AI Agent** (powered by the Google Gemini Chat Model) to automate **professional email replies** in a human-like and context-aware way. It's ideal for professionals looking to automate inbox management while maintaining personalization and professionalism.

[👉 View Workflow JSON](https://github.com/rohan5576/n8n_Automations/blob/main/EmailAgent.json)

![Email Reply Agent](https://github.com/rohan5576/n8n_Automations/blob/main/images/EmailReplyAgent.png)
![Email Reply Agent](https://github.com/rohan5576/n8n_Automations/blob/main/images/EmailAIIntrustions.png)


## 🧠 Overview

This automation setup reads emails from your Gmail inbox, analyzes them using a custom-configured **AI Agent**, and drafts personalized, professional replies.

### 🌟 Agent Capabilities

- 📥 Reads all incoming emails
- 🧠 Analyzes email subject and content
- ✍️ Drafts thoughtful, human-like replies
- 🤝 Aims to build **trust and reputation** in responses
- ✅ Marks emails as read after processing


## 🔧 Workflow Structure

### Nodes Used:

- **Schedule Trigger** – To periodically check emails
- **Gmail Nodes** – To fetch and update emails
- **AI Agent** – The intelligent engine that creates the reply
- **Google Gemini Chat Model** – For natural language understanding and generation


## 💼 Agent Instructions

```xml
<Role>
  <name>Email Reply Agent</name>
  <Description>Helpful email reply agent</Description>
</Role>

<Goal>
  <primary>Draft custom but very professional email replies which are 100% humanlike.</primary>
  <secondary>Build trust and reputation with the person you are replying to.</secondary>
</Goal>

<Instructions>
  <Instruction>Understand and analyze the subject line and full email body</Instruction>
  <Instruction>Review <Details> and <Aims> to understand the user's context before replying</Instruction>
  <Instruction>Use <Userinfo> to personalize the email</Instruction>
</Instructions>


