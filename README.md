# 🤖 SahulatAI — AI Admission Counselor for SMIT

> **Live Demo:** [https://sahulat-ai-chatbot-01.onrender.com](https://sahulat-ai-chatbot-01.onrender.com) Built for SMIT Hackathon 2026 — The complete codebase was ready on hackathon day, but deployment failed due to internet connectivity issues and free-tier memory limits on cloud platforms. But code zip filed was already uploaded under designated timeline in the zip file format.

After the event, I explored Render, Railway, and Fly.io, optimized the build with Docker + CPU-only PyTorch, pre-baked the ChromaDB index, and finally got it live and stable.



---

## 📖 Overview

**SahulatAI** is a bilingual (English/Urdu) AI-powered admission counselor chatbot for **Saylani Mass IT Training (SMIT)**. It helps prospective students get instant, accurate answers about admissions, courses, fees, campuses, and application procedures — all grounded in SMIT's official knowledge base.

Built for the **SMIT Hackathon 2026** 🏆

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🌐 **Bilingual Support** | English + Urdu (Noto Nastaliq font) |
| 📚 **RAG-Powered Answers** | Retrieval-Augmented Generation from SMIT Master Knowledge Base |
| 🔍 **Source Citations** | Every answer cites exact PDF pages/lines |
| 💬 **Streaming Responses** | Real-time token streaming via SSE |
| 📱 **Fully Responsive** | Desktop 3-panel + Mobile-optimized UI |
| 🎯 **Quick Question Cards** | 10 pre-loaded bilingual questions (auto-scroll carousel) |
| 🔔 **WhatsApp Ready** | Webhook integration (Meta Cloud API) |
| ⚡ **Fast & Lightweight** | Dockerized, optimized for cloud deployment |

---

## 🏗️ Architecture

```
┌─────────────────┐     ┌──────────────────┐     ┌──────────────────┐
│   Frontend      │────▶│   Flask API      │────▶│  ChromaDB        │
│   (HTML/JS/CSS) │     │   (Python)       │     │  (Vector Store)  │
└─────────────────┘     └──────────────────┘     └──────────────────┘
                              │
                              ▼
                       ┌──────────────────┐
                       │  Groq LLM        │
                       │  (GPT-OSS-120B)  │
                       └──────────────────┘
```

**Tech Stack:**
- **Backend:** Flask, Gunicorn, Python 3.11
- **AI/ML:** Groq API, sentence-transformers, ChromaDB
- **Frontend:** Vanilla JS, CSS Grid/Flexbox, Marked.js
- **Deployment:** Docker → Render

---

## 🚀 Quick Start (Local)

```bash
# 1. Clone
git clone https://github.com/MuhammadSami-04/sahulat-ai-chatbot.git
cd sahulat-ai-chatbot

# 2. Install deps
pip install -r requirements.txt

# 3. Configure
cp .env.example .env
# Edit .env with your GROQ_API_KEY

# 4. Run
python run.py
# → http://localhost:5050
```

---

## 🐳 Docker Deployment

```bash
docker build -t sahulat-ai .
docker run -p 10000:10000 --env-file .env sahulat-ai
```

---

## ☁️ Deploy to Render (Free Tier)

1. Fork this repo
2. Go to [Render Dashboard](https://dashboard.render.com) → **New +** → **Web Service**
3. Connect GitHub → Select `sahulat-ai-chatbot`
4. **Runtime:** Docker (auto-detected from `Dockerfile`)
5. Add env var: `GROQ_API_KEY`
6. Deploy 🚀

> **Note:** Free tier (512MB) may hit memory limits during PyTorch install. Upgrade to **Starter ($7/mo)** or use **Railway/Fly.io** for guaranteed builds.

---


## 🧠 How It Works

1. **Ingestion** (once): PDF → chunks → embeddings → ChromaDB
2. **Query:** User asks → embed query → retrieve top-k chunks
3. **Generate:** Chunks + question → Groq LLM → streaming answer
4. **Cite:** Sources attached with page/line numbers
5. **Language:** Auto-detects Urdu/English → responds in same language

---

## 📸 Screenshots

| Desktop | Mobile |
|---------|--------|
| ![Desktop](static/screenshots/desktop.png) | ![Mobile](static/screenshots/mobile.png) |

*(Add screenshots to `static/screenshots/`)*

---

## 🛠️ Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `GROQ_API_KEY` | ✅ | Groq API key (get from console.groq.com) |
| `WHATSAPP_ACCESS_TOKEN` | ❌ | Meta Cloud API token |
| `WHATSAPP_PHONE_NUMBER_ID` | ❌ | WhatsApp Business phone ID |
| `WHATSAPP_BUSINESS_ACCOUNT_ID` | ❌ | WABA ID |
| `WHATSAPP_VERIFY_TOKEN` | ❌ | Custom webhook verify token |

---


---

## 📜 License

MIT License — feel free to use, modify, and distribute.

---

## 🙏 Credits

- **SMIT** — Knowledge base & domain expertise
- **Groq** — Lightning-fast LLM inference
- **Saylani Welfare International Trust** — Mission & vision
- **Open Source** — ChromaDB, sentence-transformers, Flask, and countless others

---

## 📬 Contact

**Developer:** Muhammad Sami  
**GitHub:** [@MuhammadSami-04](https://github.com/MuhammadSami-04)  
**Live App:** [https://sahulat-ai-chatbot-01.onrender.com](https://sahulat-ai-chatbot-01.onrender.com)

---

⭐ **Star this repo if you found it useful!**
