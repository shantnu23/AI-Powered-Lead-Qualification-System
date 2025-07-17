# 🤖 AI-Powered Lead Qualification & Meeting Scheduler

This project showcases my internship work where I built an end-to-end AI-powered system to automate **lead profiling**, **nurturing**, and **meeting scheduling** using cutting-edge LLMs, multi-agent workflows, and real-time integrations.

It streamlines the sales funnel, reduces manual intervention, and personalizes follow-ups — improving the overall lead conversion experience.

---

## 📌 Project Highlights

- ✅ Built with **LangGraph**, **Groq LLMs**, and **FastAPI**
- ✅ Uses **FAISS-based RAG** for personalized emails
- ✅ Automates **Google Meet scheduling** from natural language time inputs
- ✅ Sends invites via **Email** (Mailgun) and **WhatsApp** (MCP webhook)
- ✅ Fully agent-based, context-aware, and modular

---

## 🔁 Full System Workflow

### 1. 🎙️ Transcript Ingestion
- The system starts with a raw **sales call transcript** as input.
- It could be uploaded via UI or passed via an API.

---

### 2. 🧠 Lead Profiler Agent (LLM-powered)
- Extracts structured fields like:
  - Name, Email, Company, Designation
  - Lead intent
  - Preferred meeting time (in natural language)
- Classifies the lead as:
  - `Hot` → high interest
  - `Warm` → moderate interest
  - `Cold` → not worth pursuing now

---

### 3. 🔀 Agent Routing (LangGraph logic)
- `Hot` → routed to **Meeting Scheduler Agent**
- `Warm` → routed to **Lead Nurture Agent**
- `Cold` → not pursued (future work: add cold lead tracker)

---

### 4. ✉️ Lead Nurture Agent (for Warm Leads)
- Uses a **RAG (Retrieval-Augmented Generation)** system:
  - Retrieves past success case studies using **FAISS + SentenceTransformers**
  - Generates a personalized follow-up email based on retrieved context
- Sends the email using **Mailgun API**

---

### 5. 🔄 Warm → Hot Conversion Handling
- If a **warm lead replies later** with:
  - Clear meeting intent
  - Time preference
  - Email ID  
→ The system re-classifies the lead as `Hot` and automatically schedules a meeting as below.

---

### 6. 🗓️ Meeting Scheduler Agent (for Hot Leads)
- Parses natural language time like:
  > “Tomorrow at 10am”  
  using `dateparser`
- Schedules a Google Meet using the **Google Calendar API**
- Generates a meeting link and sends invites:
  - 📧 Email (via Mailgun)
  - 💬 WhatsApp (via MCP webhook)

---

### 7. ⚠️ Fallback Handling
- If time isn't mentioned or is invalid:
  - Lead is logged with a message:  
    > “Time not provided. Meeting not scheduled.”
  - System continues without crashing

---

## 🧠 Tech Stack

| Area                     | Tool / Library                      |
|--------------------------|-------------------------------------|
| LLM & Reasoning          | Groq API (Mixtral / LLaMA3)         |
| Agent Workflow           | LangGraph                           |
| Backend Server           | FastAPI                             |
| Email Service            | Mailgun API                         |
| WhatsApp Integration     | MCP Webhook                         |
| RAG System               | FAISS + SentenceTransformers        |
| Scheduling               | Google Calendar API + `dateparser` |

---

## 🛠️ Functionality Summary

- 🔍 **Lead Parsing**: Extracts structured info from raw transcripts
- 🧭 **Routing Logic**: Classifies and routes leads via LangGraph
- 📨 **Email Personalization**: RAG-generated case study emails
- 📅 **Meeting Booking**: Real-time meeting link creation
- 🔁 **Warm to Hot Flow**: Dynamic state change & re-routing
- 📲 **Multi-channel Notification**: Sends both Email and WhatsApp invites

---

## 🚧 Future Work (Next Steps)

- 🔁 Add cold lead retention & reactivation flow
- 🧑‍💻 Web dashboard to track leads and scheduling status
- 🌐 Frontend UI for uploading transcripts and tracking responses
- 📦 Dockerize for cloud deployment
- 🧩 Integrate with CRM tools like HubSpot/Salesforce

---

## 👨‍💻 Author & Ownership

Developed as part of my internship, this project represents my individual contribution in building a fully functioning LLM-based system — from agent logic to external API integration.

📧 **[Shantnu Saxena](mailto:shatnusaxen2005@gmail.com)**  
🌐 [LinkedIn Profile]([https://www.linkedin.com/in/your-link](https://www.linkedin.com/in/shantnu-saxena-361950249?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app)) (update this if needed)

---

> 🚨 Note: Codebase is maintained privately under the organization’s GitHub. This README is for showcasing the architecture and contributions on my personal GitHub.

