# 🚨 Negative Alert System
> AI-powered customer feedback system with real-time sentiment analysis, instant Telegram alerts, and automated email responses.

![Made with n8n](https://img.shields.io/badge/Made%20with-n8n-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white)
![AI Powered](https://img.shields.io/badge/AI-Groq%20LLaMA-00C896?style=for-the-badge)
![Telegram](https://img.shields.io/badge/Alerts-Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)
![Gmail](https://img.shields.io/badge/Email-Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Logs-Google%20Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)

---

## 📌 The Problem

Every day, restaurant and business owners **lose customers silently.**

- 😡 A customer has a bad experience → leaves without saying anything
- 📵 The owner has no idea what happened at any branch
- 🕐 By the time they find out — it's already a negative Google review

**91% of unsatisfied customers never come back** if no one reaches out within 24 hours.

---

## ✅ The Solution

**Negative Alert System** detects unhappy customers **in real-time** — before they tell anyone else.

The moment a customer submits feedback:

| Step | What happens | Time |
|------|-------------|------|
| 1️⃣ | Customer fills a branded feedback form | 0s |
| 2️⃣ | AI analyzes sentiment (Arabic + English) | ~2s |
| 3️⃣ | If negative → instant Telegram alert to owner | ~4s |
| 4️⃣ | Automatic apology email sent to customer | ~4s |
| 5️⃣ | Everything logged in Google Sheets with status | ~5s |

**Total time from complaint to action: under 10 seconds.**

---

## 🎯 Live Demo

> 🍕 **Hamza Pizza** — Branded feedback form built with this system:
> **[https://hamzaa-feedback.netlify.app](https://hamzaa-feedback.netlify.app)**

---

## 🛠️ Tech Stack

| Tool | Role |
|------|------|
| **n8n** | Workflow automation engine |
| **Groq (LLaMA 3.1 8B)** | AI sentiment analysis — Free |
| **Google Sheets** | Feedback log + status tracking |
| **Telegram Bot** | Instant owner alerts with action buttons |
| **Gmail** | Automated customer emails |
| **Netlify** | Hosting the feedback form |

---

## ⚙️ How It Works

```
Customer submits form
        ↓
  JavaScript Code Node
  (formats date + data)
        ↓
  Groq AI (LLaMA 3.1)
  Analyzes sentiment:
  positive / negative / neutral
        ↓
       IF
      /    \
 negative   positive/neutral
    /              \
Telegram Alert    Thank-you Email
+ Apology Email   (Gmail)
(Gmail)
    \              /
     Google Sheets Log
     (name, review, sentiment,
      phone, branch, date, status)
```

---

## 📲 Telegram Alert Features

When a negative review is detected, the owner receives:

```
🚨 بلاغ سلبي جديد يحتاج تدخل!

👤 العميل: Ahmed Mohamed
📍 الفرع: المعادي
📅 التاريخ: 23-04-2026
💬 الشكوى: "الأكل جه بارد وبطيء جداً"
📞 رقم الهاتف: [clickable phone link]

⚠️ يرجى اتخاذ إجراء سريع لإرضاء العميل.

[ ✅ تم التواصل ]  [ 🎁 تعويض العميل ]
```

**Action buttons** let the owner respond directly from Telegram — no other app needed.

---

## 🤖 AI Prompt — Bilingual Sentiment Analysis

The system understands:
- ✅ Egyptian Arabic slang (`زي الزفت`, `جامد`, `ضايع`)
- ✅ English reviews (`bad experience`, `very good service`)
- ✅ Mixed language (`الـ Order اتأخر جداً`)

```
You are a bilingual sentiment analysis expert (Arabic/Egyptian Dialect & English).

Respond with ONLY one word:
- positive
- negative  
- neutral

Guidelines:
1. Understand Egyptian slang (e.g., "جامد" = positive, "ضايع" = negative)
2. Understand English technical terms (e.g., "Quality", "Support", "Delivery")
3. Handle Mixed text (e.g., "الـ Order اتأخر جداً" = negative)

Do not explain. Do not add punctuation. Just reply with one word only.
```

---

## 📊 Google Sheets Log

Every submission is automatically logged:

| Name | Review | Sentiment | Phone | Branch | Date | Status |
|------|--------|-----------|-------|--------|------|--------|
| Ahmed | الأكل بارد | negative | 010xxx | المعادي | 23-04-2026 | قيد الانتظار ⏳ |
| Sara | ممتاز جداً | positive | 011xxx | الزمالك | 23-04-2026 | ✅ |

---

## 🚀 Setup Guide

### 1. Import the workflow
- Download `Negative_Alerts.json`
- In n8n: **Settings → Import workflow** → upload the file

### 2. Set up credentials
Add these in n8n credentials:
- **Groq API** — free at [console.groq.com](https://console.groq.com)
- **Gmail OAuth2** — Google Cloud Console
- **Google Sheets OAuth2** — same Google account
- **Telegram Bot** — create via [@BotFather](https://t.me/BotFather)

### 3. Configure the workflow
- Set your **Telegram Chat ID** in the Telegram node
- Set your **Google Sheet ID** in the Sheets node
- Set your **Gmail** in the email nodes

### 4. Deploy the feedback form
- Edit `hamza-feedback-form.html` — replace with your branding
- Add your n8n **production webhook URL**:
```javascript
fetch('https://YOUR-N8N-INSTANCE/webhook/YOUR-PATH', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ name, phone, email, review, rating })
});
```
- Deploy on [Netlify Drop](https://netlify.com/drop) — free

### 5. Activate
- Toggle workflow **Active** in n8n
- Share the form link with customers 🎉



---


**Eng. Adham Abdelnasser**
AI Automation Specialist

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Adham%20Abdelnasser-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/adhamabdelnasser/)
[![Email](https://img.shields.io/badge/Email-adhamnasser601%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:adhamnasser601@gmail.com)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-01016943739-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/201016943739)


⭐ **If this project helped you, give it a star!**
