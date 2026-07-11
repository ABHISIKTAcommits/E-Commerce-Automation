<div align="center">

# 🤖 AI-Powered E-Commerce Support Agent

**An autonomous, multimodal customer support agent that handles order inquiries, refund requests, and shipping updates via Telegram.**
<br>
Capable of transcribing voice notes, understanding customer intent, detecting sentiment, and querying a database for real-time order status.

<br>

[![n8n](https://img.shields.io/badge/Built_with-n8n-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io)
[![Gemini](https://img.shields.io/badge/LLM-Gemini_1.5-4285F4?style=for-the-badge&logo=googlegemini&logoColor=white)](https://deepmind.google/technologies/gemini/)
[![Whisper](https://img.shields.io/badge/Speech-Whisper-74AA9C?style=for-the-badge&logo=openai&logoColor=white)](https://openai.com/research/whisper)
[![Telegram](https://img.shields.io/badge/Channel-Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)](https://telegram.org)

</div>

<br>

---

## ✨ Features

- 🗣️ **Multimodal Input** — Processes both text messages and voice notes seamlessly using OpenAI Whisper.
- 🧠 **Intent Extraction** — Uses Google Gemini to accurately extract customer intent (e.g., `order_status`, `refund_request`) from unstructured text.
- 😠 **Sentiment Analysis** — Detects customer emotions (positive, neutral, angry) to tailor the AI's tone.
- 🛒 **Database Lookup** — Dynamically queries order databases (Shopify/Sheets) using extracted Order IDs.
- 🛡️ **Fault Tolerant** — Gracefully handles missing order IDs by politely prompting the user instead of crashing.

<br>

---

## 📺 Demo

<div align="center">

### Text Interaction
<img src="assets/text-demo.png" alt="Text Demo" width="600"><br><br>

### Voice Note Interaction
<img src="assets/voice-demo.png" alt="Voice Demo" width="600">

</div>

<br>

---

## 🏗️ Architecture

```text
[Telegram Trigger]
       │
       ├── (Text Path) ──> [Clean Text Code Node] ──┐
       │                                            │
       ├── (Voice Path) ─> [Download] ─> [Whisper] ─┤
       │                                            ▼
       │                                 [Gemini: Intent Extraction]
       │                                            │
       │                                            ▼
       │                                  [Parse Intent & Extract ID]
       │                                            │
       │                                   ┌────────┴────────┐
       │                                Has ID?          No ID?
       │                                   │                │
       │                                   ▼                ▼
       │                            [Shopify / DB]    [Skip Lookup]
       │                                   │                │
       │                                   └────────┬────────┘
       │                                            ▼
       │                                 [Gemini: Final Reply Generator]
       │                                            │
       └────────────────────────────────────────────┤
                                                      ▼
                                          [Telegram: Send Reply]
```

<br>

---

## 🛠️ Tech Stack

| Category | Technology |
| :--- | :--- |
| **Orchestration** | n8n (Workflow Automation) |
| **LLM / NLP** | Google Gemini 1.5 Flash |
| **Speech-to-Text** | OpenAI Whisper API |
| **Platform APIs** | Telegram Bot API, Shopify REST API |
| **Data Parsing** | JavaScript (Node.js environment) |

<br>

---

## ⚙️ Setup & Installation

### Prerequisites
- An n8n account ([n8n.cloud](https://n8n.cloud) or self-hosted)
- Telegram Bot Token (via [@BotFather](https://t.me/botfather))
- Google Gemini API Key
- OpenAI API Key (for Whisper)
- Shopify Admin API Access (or a Google Sheet for testing)

### Steps
1. Clone the repository (or download the `.json` file).
2. Open your n8n instance.
3. Click the **Menu (≡) → Import from File** → select `ecommerce-ai-agent.json`.
4. **Add your credentials** — go to n8n Credentials and add your Telegram, OpenAI, Gemini, and Shopify API keys.
5. **Open each node** and confirm the correct credentials are selected from the dropdown.
6. Toggle the workflow to **Active (Green)** in the top right corner.
7. Go to **Telegram** and start chatting with your bot!

<br>

---

## 🚀 Future Enhancements

- [ ] Integrate with a Vector Database (Pinecone) for RAG-based FAQ answering.
- [ ] Add a "Human-in-the-loop" escalation path to Slack for angry customers.
- [ ] Support for WhatsApp and Instagram DMs.
- [ ] Analytics dashboard tracking intent distribution and resolution times.

<br>

---

<div align="center">

**Made with ❤️ by [Your Name](https://yourwebsite.com)**

</div>
