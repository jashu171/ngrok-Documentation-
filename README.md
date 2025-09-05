# ngrok-Documentation-

# 🌐 n8n + ngrok Setup Guide

Easily expose your **local n8n instance (`localhost:5678`)** to the internet using **ngrok**.  
This is useful for testing webhooks (e.g., WhatsApp, Slack, Stripe, GitHub, etc.) on your local machine.

---

## 📋 Prerequisites
- Installed **n8n** (via npm or desktop).
- Command-line access:
  - **Windows** → PowerShell or CMD  
  - **macOS/Linux** → Terminal  
- Free [ngrok account](https://dashboard.ngrok.com/signup).

---

## ⚡ Quick Start (3 Steps)
```bash
# 1. Start n8n
n8n start

# 2. In another terminal, run ngrok
ngrok http 5678

# 3. Copy the public ngrok URL and set it as WEBHOOK_URL
export WEBHOOK_URL=https://abcd-1234.ngrok.io/
n8n start
