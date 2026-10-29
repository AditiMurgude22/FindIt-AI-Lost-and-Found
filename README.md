# FindIt — AI Lost-and-Found Agent

## 📌 Project Overview

**FindIt** is an AI-powered college Lost-and-Found management agent built using **n8n, Google Gemini, Telegram, and Google Sheets**.

The system allows students to report lost or found items through Telegram. Gemini AI analyzes the student's message and extracts important information such as the report type, item category, item name, color, description, location, and date.

The extracted information is stored in Google Sheets, where the AI can compare the new report with existing records to identify possible matches.

## 🎯 Objectives

- Provide an easy way for students to report lost or found items.
- Automatically extract structured information from natural-language messages.
- Store Lost-and-Found reports in a centralized Google Sheet.
- Use AI to identify possible matches between lost and found reports.
- Notify the student when a possible matching report is identified.

## 🛠️ Technologies Used

- **n8n** — Workflow automation and orchestration
- **Google Gemini AI** — Item information extraction and matching
- **Telegram** — Student interaction and reporting interface
- **Google Sheets** — Lost-and-Found database
- **JavaScript** — Processing Gemini's structured output
- **Gmail** — Notification of new reports

## 🔄 Workflow

The main workflow follows these steps:

```text
Student
   ↓
Telegram
   ↓
n8n Telegram Trigger
   ↓
Edit Fields
   ↓
Google Gemini AI
   ↓
JavaScript Processing
   ↓
Google Sheets — Get Existing Records
   ↓
Gemini AI — Match Analysis
   ↓
Google Sheets — Save Report
   ↓
Notification
```

## 🤖 AI Features

### 1. Lost/Found Classification

Gemini determines whether the student is reporting a:

- Lost item
- Found item

### 2. Information Extraction

The AI extracts:

- Report Type
- Item Category
- Item Name
- Color
- Description
- Location
- Date Lost/Found

### 3. AI Matching

The system compares a new report with existing Google Sheets records.

A potential match must be between opposite report types:

- Lost ↔ Found

The AI considers details such as:

- Item category
- Item name
- Color
- Description
- Location
- Date

Distinctive identifying information is given more importance than common characteristics such as color alone.

## 📊 Database Structure

The Google Sheets database contains fields such as:

| Field | Description |
|---|---|
| Report ID | Unique report identifier |
| TelegramUserID | Telegram user identifier |
| ReportType | Lost or Found |
| ItemCategory | Category of the item |
| ItemName | Name of the item |
| Color | Item color |
| Description | Detailed item description |
| Location | Location where item was lost/found |
| DateLostFound | Date or time reference |
| Status | Current report status |
| PossibleMatchID | ID of a possible matching report |
| CreatedAt | Report creation timestamp |

## 💬 Example

### Student message

> I lost my black wallet in the computer lab today.

### AI-extracted information

```json
{
  "reportType": "Lost",
  "itemCategory": "Wallet",
  "itemName": "Wallet",
  "color": "black",
  "description": "Black wallet reported lost in the computer lab.",
  "location": "computer lab",
  "dateLostFound": "today"
}
```

The information is then processed by the workflow and stored in the Lost-and-Found database.

## 🔐 Security

API keys, Telegram bot tokens, Google credentials, and other private credentials should **not** be stored in this repository.

Credentials should be configured separately inside n8n.

## 📁 Repository Contents

```text
FindIt-AI-Lost-and-Found/
│
├── README.md
└── findit-workflow.json
```

## 🚀 Future Improvements

- Add automatic unique Report ID generation.
- Improve matching accuracy using additional item attributes.
- Add student confirmation when a possible match is found.
- Add an admin dashboard for managing reports.
- Add report status updates such as claimed or resolved.
- Improve notification and communication features.

## 👥 Project

**FindIt — AI Lost-and-Found Agent**

Developed as part of the **ISE2 Project**.