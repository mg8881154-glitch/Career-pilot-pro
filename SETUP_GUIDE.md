# CareerPilot - Local Setup Guide

## ✅ Current Status

| Service | Status | URL |
|---------|--------|-----|
| Frontend (React/Vite) | ✅ Running | http://localhost:5173 |
| Backend (Node/Express) | ✅ Running | http://localhost:5000 |

---

## 🔑 Features & Required Keys

### 1. MongoDB (Database) — REQUIRED for most features
Without MongoDB, login/signup, resumes, job tracker, etc. will NOT work.

**Option A — MongoDB Atlas (Free, Recommended):**
1. Go to https://www.mongodb.com/atlas/database
2. Create free account → Create free cluster (M0)
3. Click "Connect" → "Drivers" → copy connection string
4. Edit `backend/.env`:
   ```
   MONGODB_URI=mongodb+srv://<user>:<password>@cluster0.xxxxx.mongodb.net/careerpilot
   ```

**Option B — Local MongoDB:**
1. Download from https://www.mongodb.com/try/download/community
2. Install and start MongoDB service
3. `backend/.env` already has: `MONGODB_URI=mongodb://localhost:27017/careerpilot`

---

### 2. AI Features (Gemini, Groq, OpenAI) — REQUIRED for resume/interview AI

**Gemini (Free tier available):**
1. Go to https://aistudio.google.com/app/apikey
2. Click "Create API Key"
3. Edit `backend/.env`: `GEMINI_API_KEY=your-key-here`

**Groq (Free, very fast):**
1. Go to https://console.groq.com/keys
2. Create API key
3. Edit `backend/.env`: `GROQ_API_KEY=your-key-here`

---

### 3. Firebase — REQUIRED for Auth & Community features
1. Go to https://console.firebase.google.com
2. Create project → Project Settings → Service Accounts
3. Click "Generate new private key" → download JSON file
4. Copy JSON file to `backend/` folder (e.g., `serviceAccount.json`)
5. Edit `backend/.env`:
   ```
   FIREBASE_PROJECT_ID=your-project-id
   FIREBASE_STORAGE_BUCKET=your-project-id.appspot.com
   FIREBASE_SERVICE_ACCOUNT_PATH=serviceAccount.json
   ```

---

### 4. Redis — Optional (needed for job queues & weekly digest)
1. Go to https://app.redislabs.com (Redis Cloud free tier: 30MB)
2. Create free database → copy connection string
3. Edit `backend/.env`:
   ```
   REDIS_URL=redis://:<password>@<host>:<port>
   ```

---

### 5. Email (SMTP) — Optional (needed for email notifications)
For Gmail:
1. Enable 2FA at https://myaccount.google.com
2. Go to https://myaccount.google.com/apppasswords
3. Generate app password for "Mail"
4. Edit `backend/.env`:
   ```
   EMAIL_USER=your-email@gmail.com
   EMAIL_PASS=your-16-char-app-password
   ```

---

### 6. RapidAPI (Job Search) — Optional
1. Go to https://rapidapi.com/letscrape-6bRBa3QguO5/api/jsearch
2. Subscribe to free tier → copy API key
3. Edit `backend/.env`: `RAPID_API_KEY=your-key-here`

---

## 🚀 Running the Project

Open two terminal windows:

**Terminal 1 — Backend:**
```bash
cd backend
npm run dev
```

**Terminal 2 — Frontend:**
```bash
cd frontend
npm run dev
```

Then open http://localhost:5173 in your browser.

---

## ❓ Troubleshooting

| Problem | Fix |
|---------|-----|
| Login/Signup not working | Set up Firebase + MongoDB |
| AI features not working | Set GEMINI_API_KEY or GROQ_API_KEY |
| Job search not working | Set RAPID_API_KEY |
| Emails not sending | Set EMAIL_USER + EMAIL_PASS |
| Community features broken | Set up Firebase properly |
