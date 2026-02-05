# NGO Voice Analyst: AI-Driven Crisis Mapping

An automated pipeline designed to bridge the gap between emergency call recordings and actionable insights for NGOs. This system utilizes AI to transcribe, categorize, and prioritize humanitarian requests in real-time.

---

## 🚀 Overview
The **NGO Voice Analyst** automates the labor-intensive process of auditing call logs. By converting raw audio into structured data, the system allows NGO operators to identify urgent cases instantly and map community needs geographically and categorically.

## ✨ Key Features
* **Speech-to-Text (STT):** High-accuracy transcription of call recordings.
* **Urgency Mapping:** AI-powered sentiment and keyword analysis to flag high-priority requests.
* **Structured Categorization:** Automatically maps requests to specific departments (e.g., Medical, Food Security, Legal Aid).
* **Frontend Integration:** A dedicated dashboard for visualizing incoming data and managing response workflows.

## 🏗️ Technical Stack
* **Orchestration:** n8n (Advanced Workflow Automation)
* **AI Engine:** Gemini API / LLM Integration
* **Backend:** Node.js / Express (MERN Stack)
* **Storage:** MongoDB / Pinecone (Vector Database)
* **Frontend:** React.js

## 🛡️ Production Notice & Repository Scope
**Note:** This project is currently in a live production environment. To maintain security and data privacy standards:
* The full production workflow and environment variables are **omitted**.
* This repository contains the **Frontend implementation** and a **redacted version** of the n8n logic.
* API keys and proprietary prompt templates have been removed.

## 🛠️ How it Works
1.  **Ingestion:** Call recordings are pushed to the webhook listener.
2.  **Processing:** The n8n workflow triggers audio-to-text conversion.
3.  **Analysis:** The LLM extracts the "Intent" and assigns an "Urgency Score".
4.  **Delivery:** Structured JSON data is sent to the React frontend for real-time display.
