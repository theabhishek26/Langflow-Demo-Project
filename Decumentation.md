````markdown
# 📧 Gmail + 📅 Google Calendar Assistant (Langflow + Composio)

This project demonstrates how to build an **AI Agent in Langflow** that:
- Reads emails from Gmail  
- Extracts relevant information  
- Creates events in Google Calendar automatically  

It uses **Composio** for authentication and tool integration, and connects with **Cluede MCP server** as an external tool.

---

## 🚀 Features
- Fetch Gmail emails (`GMAIL_FETCH_EMAILS`, `GMAIL_FETCH_MESSAGE_BY_ID`, etc.)
- Analyze email content using **OpenAI GPT models**
- Create and manage Google Calendar events (`GOOGLECALENDAR_CREATE_EVENT`, `GOOGLECALENDAR_FIND_FREE_SLOTS`, etc.)
- End-to-end automation pipeline:
  - Chat Input → Gmail Tool → Agent → Calendar Tool → Chat Output
- MCP server integration (Cluede) for querying mails as external tool

---

## 🛠️ Requirements
- [Langflow](https://github.com/langflow-ai/langflow)
- OpenAI API key
- Composio API key (for Gmail + Google Calendar connection)

---

## 📥 Installation

```bash
# Clone this repository
git clone https://github.com/theabhishek26/Langflow-Demo-Project.git


# Create virtual environment
python -m venv langflow_test_env
source langflow_test_env/bin/activate   # (Linux/Mac)
langflow_test_env\Scripts\activate     # (Windows)

# Install dependencies
pip install -r requirements.txt
````

---

## 🔑 Authentication with Composio

Before running Langflow, you must connect **Gmail** and **Google Calendar**.

Run the helper script:


---

## 🧩 Langflow Setup

The Langflow pipeline looks like this:

```
ChatInput → Gmail Toolset → Agent (OpenAI GPT-4o-mini) → Google Calendar Toolset → ChatOutput
```

### Node Details

* **Chat Input**: Accepts user queries (e.g. "Check for upcoming meetings from HR email and add to calendar").
* **Gmail Toolset**:

  * `GMAIL_FETCH_EMAILS`
  * `GMAIL_FETCH_MESSAGE_BY_ID`
* **Agent**:

  * Model: `gpt-4o-mini`
  * Instructions: *"You are a helpful assistant that can read emails and schedule calendar events"*
* **Google Calendar Toolset**:

  * `GOOGLECALENDAR_CREATE_EVENT`
  * `GOOGLECALENDAR_FIND_FREE_SLOTS`
* **Chat Output**: Displays the assistant’s response.

---

## ▶️ Running the Project

1. Start Langflow inside your virtual environment:

   ```bash
   langflow run
   ```
2. Open Langflow UI at: [http://localhost:7860](http://localhost:7860)
3. Import your flow JSON (if stored separately) or rebuild it in the UI.
4. Start chatting! Example:

   **User:**
   "Check my Gmail for meeting invites and schedule them in Google Calendar."

   **Agent:**

   * Fetches latest email
   * Extracts date/time
   * Creates a Google Calendar event
   * Confirms: *"Event created for 21 Sept at 3PM: Team Sync with HR"*

---

## 📡 MCP Server (Cluede Integration)

This flow also connects to **Cluede MCP server** so you can:

* Query emails via MCP
* Use them as inputs for the Agent
* Automate workflows across systems

---

## 📂 Project Structure

```
.
├── requirements.txt       # Python dependencies
├── README.md              # Project documentation
└── flows/
    └── gmail_calendar.json  # (Optional) Exported Langflow flow
```

