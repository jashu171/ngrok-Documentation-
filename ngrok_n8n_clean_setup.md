# 🚀 Ngrok + n8n Setup Guide (Windows & macOS)

This guide helps you **install ngrok**, connect it to your account, and expose your **local n8n instance (`localhost:5678`)** to the internet.

---

## 📋 Prerequisites
- Installed **n8n** (via npm or desktop).
- Basic command-line knowledge (PowerShell on Windows, Terminal on macOS).
- [ngrok account](https://dashboard.ngrok.com/signup) (free plan works).

---

## 🔧 1. Install ngrok

### Windows
#### Option A — Using `winget`
```powershell
winget install ngrok.ngrok
```

#### Option B — Manual Download
1. Download from: [https://ngrok.com/download](https://ngrok.com/download)  
2. Unzip → move `ngrok.exe` to `C:\Windows\System32` (or add folder to PATH).

---

### macOS
#### Option A — Using Homebrew
```bash
brew install ngrok
```

#### Option B — Manual Download
1. Download from: [https://ngrok.com/download](https://ngrok.com/download)  
2. Unzip → move `ngrok` binary to `/usr/local/bin`.

---

## 🔑 2. Add ngrok Authtoken
Get the AuthToken 
After login to [ngrok dashboard](https://dashboard.ngrok.com/get-started/your-authtoken):

```bash
ngrok config add-authtoken <YOUR_AUTHTOKEN>
```

---

## ▶️ 3. Start n8n

If installed via npm:
```bash
n8n start
```

Your n8n instance runs at `http://localhost:5678`.

---

## 🌍 4. Expose n8n with ngrok
Run:
```bash
ngrok http 5678
```

This gives a public HTTPS URL like:
```
https://abcd-1234.ngrok.io → http://localhost:5678
```

---

## ⚙️ 5. Configure n8n Webhook URL

You must set n8n’s `WEBHOOK_URL` to the ngrok URL.

### macOS/Linux (bash)
```bash
export WEBHOOK_URL=https://abcd-1234.ngrok.io/
n8n start
```

### Windows (PowerShell)
```powershell
$env:WEBHOOK_URL="https://abcd-1234.ngrok.io/"
n8n start
```

### Windows (CMD)
```cmd
set WEBHOOK_URL=https://abcd-1234.ngrok.io/
n8n start
```

---

## ✅ 6. Test with a Webhook Node
1. Open `http://localhost:5678`  
2. Create a workflow → add **Webhook Node**.  
3. Copy the **production URL** (with ngrok domain).  
4. Trigger it with Postman or external service → you should see execution in n8n.

---

## 🛠️ Troubleshooting
- **Tunnel not starting?** Check if port `5678` is free.  
- **Webhook not firing?** Ensure you’re using the **ngrok URL** in external services.  
- **Persistent URL?** Use [ngrok reserved domains](https://ngrok.com/docs/secure-tunnels/domains).  

---

## ✅ Quick Checklist
- [ ] Install ngrok  
- [ ] Add authtoken  
- [ ] Start n8n (`localhost:5678`)  
- [ ] Run `ngrok http 5678`  
- [ ] Configure `WEBHOOK_URL` in n8n  
- [ ] Test webhook  
