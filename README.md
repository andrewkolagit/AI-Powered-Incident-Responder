# 🛡️ AI-Powered Incident Responder with n8n & Gemini
> Automate incident triage, email reporting, and logging using Google Gemini, Gmail, and Google Sheets — all powered by n8n.

<img width="1484" height="547" alt="image" src="https://github.com/user-attachments/assets/faa5f7f7-26f5-42e2-9212-03da60a003a3" />

## 📌 Project Overview
This project builds an automated cybersecurity incident responder using:
* 🧠 Gemini (Google LLM) for incident summarization, severity scoring, and generating email responses.
* 🔁 n8n as the automation backbone to handle incoming alerts, API calls, email delivery, and data logging.
* 📧 Gmail to deliver professional, formatted incident response emails.
* 📊 Google Sheets to log incidents for auditing and post-incident analysis.

## ⚙️ Technologies Used
|Tool         |Purpose                          |
|-------------|---------------------------------|
|n8n          |Automation platform              |
|Gemini       |Natural language understanding   |
|Gmail        |Automated incident email delivery|
|Google Sheets|Incident log storage             |

## 🧠 How It Works
```
A[Webhook Trigger] --> B[Function Node: Extract Alert Text]
B --> C[LLM Chain Node: Gemini]
C --> D[Function: Format Email HTML]
D --> E[Gmail Node: Send Formatted Email]
C --> F[Google Sheets Node: Append Log Entry]
```

## 🧪 Sample Input Alert
```json
{
  "source": "Antivirus",
  "message": "[Malware Alert] Trojan.Generic detected on Host-22. Quarantined by antivirus."
}
```

## 📤 Sample Gemini Output
```json
{
  "subject": "Malware Alert: Trojan Detected on Host-22",
  "body": "Hi Team,\n\nA file named 'invoice_2025.pdf.exe' was detected...",
  "severity": 7,
  "source": "Antivirus"
}
```

## 📧 Sample Email Output
Subject: 🔐 Malware Alert: Trojan Detected on Host-22

Hi Team,\
A malicious file was detected and quarantined on Host-22...

Severity: 🔴 7/10

Recommended Actions:

* Scan the system
* Review the download source

*Best regards,*\
*🤖 Incident Responder Bot*

## 📊 Sample Google Sheets Log
|Timestamp          |Source   |Subject                          |Body                 |Severity|
|-------------------|---------|---------------------------------|---------------------|--------|
|2025-07-21 14:22:33|Antivirus|Malware Alert: Trojan Detected...|Hi Team,\n\nA file...|7       |

## 🧰 Features
* 🔐 Handles multiple types of alerts: malware, phishing, brute-force, insider threats, etc.
* 💡 Uses Gemini for reasoning and response generation
* 📩 Sends incident emails with emojis, severity color badges, and professional formatting
* 📈 Logs all incidents to Google Sheets with timestamp, severity, and message

## 🚀 How to Use
1. Clone this repo
2. Import the provided .json workflow into your n8n instance
3. Set up credentials for:
    * Gmail
    * Google Sheets
    * Gemini (via Vertex AI or OpenRouter)
4. Trigger alerts using POST requests to the webhook (see samples/alerts.json)
5. Review email and Google Sheets logs
