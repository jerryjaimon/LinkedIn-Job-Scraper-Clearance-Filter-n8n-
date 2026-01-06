# LinkedIn Job Scraper & Clearance Filter (n8n)

This project is an **n8n automation workflow** that scrapes publicly available LinkedIn job listings, filters roles based on **UK security clearance requirements**, and processes them using an LLM for structured analysis.

It is designed for **research, job monitoring, and automation learning purposes**.

---

## ✨ Features

- Scrapes **public LinkedIn job listings** (no login required)
- Extracts:
  - Job title
  - Company name
  - Location
  - Job description
- Detects UK clearance keywords:
  - BPSS
  - SC
  - DV
  - CTC
- Uses **Google Gemini (via n8n credentials)** for:
  - Job summarisation
  - Role relevance classification
- Can be extended to:
  - Telegram alerts
  - Notion database storage
  - CSV / Google Sheets export

---

## 🧠 Use Cases

- Cybersecurity & defence job monitoring
- Clearance-based role filtering
- Automation & AI agent experimentation
- Research on AI-assisted job intelligence

---

## 🛠️ Requirements

- **n8n** (self-hosted or cloud)
- Google Gemini / PaLM API key
- (Optional) Notion account
- Internet access

---

## 🚀 Setup Instructions

### 1. Install n8n
Choose one:
- n8n Cloud  
- Docker  
- Local install  

Docs: https://docs.n8n.io

---

### 2. Import the workflow
1. Open n8n
2. Click **Import**
3. Upload: job_hunter.json


