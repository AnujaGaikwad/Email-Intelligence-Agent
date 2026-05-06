# Email Intelligence Agent
An AI-powered email triage system that reads unread Gmail emails, classifies intent and urgency, drafts professional replies using LLMs, and routes everything through a human approval queue before sending.

Built with:

* FastAPI
* Streamlit
* LangChain
* OpenAI GPT-4o
* Google Gmail API
* Python

---

## Features

* Gmail OAuth 2.0 authentication
* Fetch unread emails
* Intent & urgency classification
* AI-generated reply drafts
* Human approval before sending
* Streamlit review dashboard
* Mock email client for testing
* Modular SOLID architecture

---

## Architecture

```text id="2m9q9w"
Streamlit UI
      ↓
   FastAPI
      ↓
  EmailAgent
      ↓
 ┌──────────────┬──────────────┬──────────────┐
 │ Gmail Tool   │ ClassifyTool │ DraftTool    │
 └──────────────┴──────────────┴──────────────┘
      ↓
 Gmail API / Mock Client
```

---

## Folder Structure

```text id="sm6mfc"
email_agent/
├── app/
│   ├── agents/
│   ├── routers/
│   ├── services/
│   ├── tools/
│   └── models/
├── frontend/
├── tests/
├── credentials/
├── requirements.txt
└── .env.example
```

---

## API Endpoints

| Method | Endpoint               | Description                   |
| ------ | ---------------------- | ----------------------------- |
| GET    | `/emails`              | Fetch & process unread emails |
| POST   | `/emails/{id}/approve` | Approve and send reply        |
| POST   | `/emails/{id}/reject`  | Reject draft                  |
| GET    | `/health`              | Health check                  |

---

## Environment Variables

```env id="tw8w7f"
OPENAI_API_KEY=
GMAIL_CREDENTIALS_PATH=./credentials/token.json
CHAT_MODEL=gpt-4o
MAX_EMAILS_PER_RUN=20
HUMAN_IN_THE_LOOP=true
```

---

## Quick Start

```bash id="2qtnkl"
pip install -r requirements.txt

uvicorn app. main: app --reload

streamlit run frontend/streamlit_app.py
```

---

## SOLID Principles

* **SRP** → Each tool handles one task
* **Open/Closed** → Add new tools easily
* **Liskov** → Mock client replaces Gmail client
* **ISP** → Agent only sees clean email data
* **DIP** → Tools injected into agent

---

## Future Enhancements

* Conversation memory
* Calendar scheduling
* Outlook integration
* Sentiment analysis
* CRM integration

---


