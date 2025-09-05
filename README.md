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

## ⚡ Quick Start (All-in-One)
```bash
# Install ngrok (choose method based on OS)

# Windows (winget)
winget install ngrok.ngrok

# Windows (manual - download zip from https://ngrok.com/download, unzip, move ngrok.exe to C:\Windows\System32)

# macOS (Homebrew)
brew install ngrok/ngrok/ngrok

# macOS (manual - download zip from https://ngrok.com/download, unzip, move ngrok to /usr/local/bin)

# Add your authtoken (from https://dashboard.ngrok.com/get-started/your-authtoken)
ngrok config add-authtoken <YOUR_AUTHTOKEN>

# Start n8n
n8n start

# Expose n8n on port 5678 with ngrok
ngrok http 5678

# Set WEBHOOK_URL to ngrok public URL (replace with your actual URL)
# macOS/Linux
export WEBHOOK_URL=https://abcd-1234.ngrok.io/
n8n start

# Windows PowerShell
$env:WEBHOOK_URL="https://abcd-1234.ngrok.io/"
n8n start

# Windows CMD
set WEBHOOK_URL=https://abcd-1234.ngrok.io/
n8n start

# Test webhook (replace /webhook/test with your actual webhook path in n8n)
curl -X POST https://abcd-1234.ngrok.io/webhook/test \
     -H "Content-Type: application/json" \
     -d '{"hello":"world"}'

# Troubleshooting
# Kill process using port 5678 on Linux/macOS
lsof -i :5678
kill -9 <PID>

# Kill process using port 5678 on Windows (PowerShell)
netstat -ano | findstr :5678
taskkill /PID <PID> /F
