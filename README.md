

# 🤖 AI-Powered Task Routing Automation with n8n


 I tried something interesting with **[n8n](https://n8n.io/)** — a no-code/low-code automation platform — and built a working automation that brings together **AI decision-making and smart task routing**.

---

## 📋 Workflow Overview

**1.  Smart task dispatcher**

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

---

## 🛠️ Tools & Nodes Used

- **Form Trigger** – To capture user inputs.
- **Airtable Nodes** – For creating and updating records.
- **Switch Node** – Routes tasks based on logic.
- **AI Agent (Tools Agent)** – The core intelligence, enriched with memory and tools.
- **Google Gemini Chat Model** – For understanding and responding to inputs.
- **Google Search Tool** – Adds dynamic, real-time context if needed.

---

## 🎯 Use Case

This setup can serve as a **lightweight AI-driven task intake and routing system**. Perfect for:
- Creative or marketing teams managing requests.
- Automating task classification and delegation.
- Using AI to validate or augment requests.

---

## 💡 Why This?

By combining **n8n’s workflow automation** with **AI reasoning**, this project explores how you can quickly scale smart operations — all with minimal code.

---

![Smart Task Dispatcher](https://github.com/rohan5576/n8n_Automations/blob/main/images/smart_task_dispatcher.png?raw=true)


---

