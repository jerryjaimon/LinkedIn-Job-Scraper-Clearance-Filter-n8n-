# LinkedIn Job Scraper + AI Analysis (n8n + Notion)

This repository contains an **n8n automation workflow** that scrapes public LinkedIn job listings, applies configurable job filters, analyzes job descriptions using an LLM (Google Gemini), and stores structured results in a **user-owned Notion database**.

Each user must **duplicate the provided Notion database template** into their own workspace before running the workflow.

---

## 🧠 What This Workflow Does

1. Scrapes **public LinkedIn job listings** (no login required)
2. Applies **job filters** (role, location, keywords, exclusions)
3. Extracts structured job data
4. Prevents duplicates using Notion
5. Uses AI to:
   - Analyze job descriptions
   - Detect UK clearance requirements (BPSS / SC / DV / CTC)
   - Score relevance
6. Stores results in Notion
7. (Optional) Sends Telegram alerts

---

## 🗂️ Notion Database (REQUIRED)

### 🔹 Step 1: Duplicate the Database Template

Use this template:

🔗 https://striped-cuticle-169.notion.site/Common-Database-2e0d23ec37b98059aabfe5741714d5b1

Steps:
1. Open the link
2. Click **Duplicate** (top-right)
3. Select your own Notion workspace
4. The database will now exist **inside your account**

⚠️ Do NOT use the original database.  
Each user must work with their **own duplicated copy**.

---

### 🔹 Step 2: Create a Notion Integration

1. Notion → **Settings → Connections → Develop or manage integrations**
2. **+ New integration**
3. Name it (e.g., `n8n Job Scraper`)
4. Copy the **Internal Integration Token**
5. Enable:
   - Read
   - Insert
   - Update

---

### 🔹 Step 3: Share the Database with the Integration

1. Open your duplicated database
2. Click **••• → Connect to**
3. Select your integration

---

### 🔹 Step 4: Get Your Database ID

1. Open the duplicated database
2. Copy the URL
3. Extract the 32-character ID

Example:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

---

## 🔑 Required Credentials (n8n)

### 1️⃣ Notion API
- **Credentials → New → Notion API**
- Paste integration token

### 2️⃣ Google Gemini (PaLM)
- Create PaLM / Gemini API key
- **Credentials → New → Google PaLM API**

### 3️⃣ Telegram (Optional)
- Create bot via **@BotFather**
- Store token as n8n credential

---

## 🧩 Nodes That MUST Be Configured

| Node Name               | Required Configuration |
|------------------------|------------------------|
| Get Existing Jobs      | Notion credential + Database ID |
| Get Unprocessed Jobs   | Notion credential + Database ID |
| Add to Notion          | Notion credential + Database ID |
| Update Notion          | Notion credential + Database ID |
| Google Gemini Chat Model | Gemini credential |
| Telegram Alert (optional) | Telegram credential |

---

## 🎯 Job Filters (IMPORTANT)

The workflow supports **configurable job filters** to control which roles are scraped and processed.

### 🔹 Where Filters Are Defined

Filters are configured in **Set / Code nodes** near the start of the workflow (commonly named):

- `Search Config1`


---

## 🔍 Available Job Filters

### 1️⃣ Job Title / Role Keywords
Used to define what roles to search for.

Example values:
```text
return [
  // 🇬🇧 United Kingdom
  { json: { role: "Penetration Tester", location: "United Kingdom" } },
  // 🇪🇺 Europe
  { json: { role: "Penetration Tester", location: "Europe" } },
 
];

