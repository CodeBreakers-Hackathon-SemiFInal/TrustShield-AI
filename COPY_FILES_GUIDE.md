# 🎯 EXACT FILES TO COPY - Step by Step Guide

## ✅ STEP-BY-STEP: Copy These Files to Your Computer

---

## 📁 PART 1: BACKEND FILES (3 files)

### File 1: `backend/server.py`
**Location in VS Code:** `/app/backend/server.py`
**Copy to:** `YourFolder/backend/server.py`
**Size:** ~400 lines
**What it does:** Main API server with AI detection logic

### File 2: `backend/requirements.txt`  
**Location in VS Code:** `/app/backend/requirements.txt`
**Copy to:** `YourFolder/backend/requirements.txt`
**Size:** ~27 lines
**What it does:** Lists Python packages to install

### File 3: `backend/.env`
**Location in VS Code:** `/app/backend/.env`
**Copy to:** `YourFolder/backend/.env`
**Content:**
```
MONGO_URL=mongodb://localhost:27017/
DB_NAME=trustshield
EMERGENT_LLM_KEY=sk-emergent-185368a407fB3D8511
```
**What it does:** Configuration for database and AI key

---

## 📱 PART 2: FRONTEND CONFIG FILES (3 files)

### File 4: `frontend/package.json`
**Location in VS Code:** `/app/frontend/package.json`
**Copy to:** `YourFolder/frontend/package.json`
**What it does:** Lists JavaScript packages

### File 5: `frontend/app.json`
**Location in VS Code:** `/app/frontend/app.json`
**Copy to:** `YourFolder/frontend/app.json`
**What it does:** Expo app configuration

### File 6: `frontend/.env`
**Location in VS Code:** `/app/frontend/.env`
**Copy to:** `YourFolder/frontend/.env`
**Content:**
```
EXPO_PUBLIC_BACKEND_URL=http://localhost:8001
```
**What it does:** Backend URL for API calls

---

## 📱 PART 3: FRONTEND APP SCREENS (6 files)

All these go in: `YourFolder/frontend/app/`

### File 7: `frontend/app/_layout.tsx`
**Location in VS Code:** `/app/frontend/app/_layout.tsx`
**Copy to:** `YourFolder/frontend/app/_layout.tsx`
**What it does:** Navigation setup

### File 8: `frontend/app/index.tsx`
**Location in VS Code:** `/app/frontend/app/index.tsx`
**Copy to:** `YourFolder/frontend/app/index.tsx`
**What it does:** Home screen with stats

### File 9: `frontend/app/message-detection.tsx`
**Location in VS Code:** `/app/frontend/app/message-detection.tsx`
**Copy to:** `YourFolder/frontend/app/message-detection.tsx`
**What it does:** Message scam detection screen

### File 10: `frontend/app/voice-detection.tsx`
**Location in VS Code:** `/app/frontend/app/voice-detection.tsx`
**Copy to:** `YourFolder/frontend/app/voice-detection.tsx`
**What it does:** Voice recording and analysis screen

### File 11: `frontend/app/result.tsx`
**Location in VS Code:** `/app/frontend/app/result.tsx`
**Copy to:** `YourFolder/frontend/app/result.tsx`
**What it does:** Shows detection results

### File 12: `frontend/app/history.tsx`
**Location in VS Code:** `/app/frontend/app/history.tsx`
**Copy to:** `YourFolder/frontend/app/history.tsx`
**What it does:** Detection history list

---

## 📚 PART 4: DOCUMENTATION (3 files) - OPTIONAL

### File 13: `PROJECT_DOCUMENTATION.md`
**Location in VS Code:** `/app/PROJECT_DOCUMENTATION.md`
**What it does:** Complete project documentation

### File 14: `SETUP_GUIDE.md`
**Location in VS Code:** `/app/SETUP_GUIDE.md`
**What it does:** Quick setup instructions

### File 15: `MANUAL_SETUP_GUIDE.md`
**Location in VS Code:** `/app/MANUAL_SETUP_GUIDE.md`
**What it does:** Detailed setup with troubleshooting

---

## 🎯 FOLDER STRUCTURE TO CREATE

Before copying files, create these folders:

```
📁 TrustShieldAI/          ← Create this anywhere (Desktop, Documents, etc.)
│
├── 📁 backend/            ← Create this folder
│   ├── 📄 server.py      ← Copy file here
│   ├── 📄 requirements.txt ← Copy file here
│   └── 📄 .env           ← Copy file here
│
└── 📁 frontend/           ← Create this folder
    ├── 📁 app/           ← Create this folder
    │   ├── 📄 _layout.tsx       ← Copy file here
    │   ├── 📄 index.tsx         ← Copy file here
    │   ├── 📄 message-detection.tsx ← Copy file here
    │   ├── 📄 voice-detection.tsx   ← Copy file here
    │   ├── 📄 result.tsx        ← Copy file here
    │   └── 📄 history.tsx       ← Copy file here
    │
    ├── 📁 assets/         ← Create empty folder
    │   └── 📁 images/    ← Create empty folder
    │
    ├── 📄 package.json   ← Copy file here
    ├── 📄 app.json       ← Copy file here
    └── 📄 .env           ← Copy file here
```

---

## 💻 HOW TO COPY FILES IN VS CODE

### Method 1: Copy-Paste (Easiest)

1. **Open file in VS Code** (click on it in file explorer)
2. **Select all text** (Ctrl+A on Windows/Linux, Cmd+A on Mac)
3. **Copy** (Ctrl+C or Cmd+C)
4. **Open your local VS Code**
5. **Create new file** with same name
6. **Paste** (Ctrl+V or Cmd+V)
7. **Save file**

### Method 2: Download File

1. **Right-click on file** in VS Code file explorer
2. **Select "Download"** (if available)
3. **Save to correct folder** on your computer

---

## ⚡ QUICK COPY CHECKLIST

Use this to track what you've copied:

### Backend Files:
- [ ] `backend/server.py` (✅ Main API)
- [ ] `backend/requirements.txt` (✅ Dependencies)
- [ ] `backend/.env` (✅ Config)

### Frontend Config:
- [ ] `frontend/package.json` (✅ Dependencies)
- [ ] `frontend/app.json` (✅ Expo config)
- [ ] `frontend/.env` (✅ Backend URL)

### Frontend Screens:
- [ ] `frontend/app/_layout.tsx` (✅ Navigation)
- [ ] `frontend/app/index.tsx` (✅ Home screen)
- [ ] `frontend/app/message-detection.tsx` (✅ Message scan)
- [ ] `frontend/app/voice-detection.tsx` (✅ Voice scan)
- [ ] `frontend/app/result.tsx` (✅ Results)
- [ ] `frontend/app/history.tsx` (✅ History)

### Optional Docs:
- [ ] `PROJECT_DOCUMENTATION.md`
- [ ] `MANUAL_SETUP_GUIDE.md`
- [ ] `SETUP_GUIDE.md`

---

## 🚀 AFTER COPYING FILES

### Step 1: Verify File Structure
Open your `TrustShieldAI` folder and make sure structure matches the diagram above.

### Step 2: Open in VS Code
```bash
# Open VS Code in your project folder
cd TrustShieldAI
code .
```

### Step 3: Install Backend Dependencies
```bash
cd backend
pip install -r requirements.txt
```

### Step 4: Install Frontend Dependencies
```bash
cd frontend
yarn install
# or if you don't have yarn:
npm install
```

### Step 5: Start MongoDB
**Windows:**
- Open Services → Start MongoDB

**Mac:**
```bash
brew services start mongodb-community
```

**Linux:**
```bash
sudo systemctl start mongodb
```

### Step 6: Start Backend (Terminal 1)
```bash
cd backend
uvicorn server:app --host 0.0.0.0 --port 8001 --reload
```
Should see: `Application startup complete`

### Step 7: Start Frontend (Terminal 2 - New)
```bash
cd frontend
npx expo start
```
Should see: QR code and options

### Step 8: Open App
- Press `w` to open in web browser
- Or scan QR code with Expo Go app on phone

---

## 🎯 TEST IT WORKS

### Quick Test 1: Backend API
Open browser: `http://localhost:8001/docs`
You should see API documentation (Swagger UI)

### Quick Test 2: Message Detection
1. Open app
2. Tap "Check Message"
3. Enter: "URGENT: Your account has been suspended"
4. Should show HIGH RISK

### Quick Test 3: Stats
Home screen should show:
- Total Scans: 1 (after test above)
- High Risk: 1

---

## ❗ IMPORTANT NOTES

### About .env Files
- File name is literally `.env` (dot + env)
- NO .txt extension
- Windows users: Save as ".env" with quotes in filename dialog

### About node_modules
- Do NOT create or copy this folder
- It's created automatically by `yarn install`
- It's very large (~500 MB)

### About Assets Folder
- Can be empty for now
- App works fine without custom images
- Uses Expo default assets

---

## 🐛 COMMON ISSUES

### "pip: command not found"
**Solution:** Install Python from python.org

### "yarn: command not found"
**Solution:** `npm install -g yarn`

### "Cannot connect to MongoDB"
**Solution:** Start MongoDB service (see Step 5 above)

### "Module not found" errors
**Solution:** Run install commands again:
```bash
pip install -r requirements.txt
yarn install
```

### "Port 8001 already in use"
**Solution:** Kill the process or use different port:
```bash
uvicorn server:app --host 0.0.0.0 --port 8002 --reload
# Then update frontend/.env to: EXPO_PUBLIC_BACKEND_URL=http://localhost:8002
```

---

## ✅ SUCCESS CHECKLIST

You'll know it's working when:

- [ ] Backend terminal shows: "Application startup complete"
- [ ] Frontend terminal shows: QR code and Metro bundler running
- [ ] Browser opens and shows TrustShield AI home screen
- [ ] Home screen shows "Protection Stats" card
- [ ] Tapping "Check Message" opens message input screen
- [ ] Analyzing a message returns HIGH/MEDIUM/LOW risk result
- [ ] Stats update after each scan

---

## 🎉 YOU'RE READY FOR HACKATHON!

Once all checks pass:
1. ✅ All files copied correctly
2. ✅ Dependencies installed
3. ✅ MongoDB running
4. ✅ Backend API responding
5. ✅ Frontend app loading
6. ✅ Message detection working
7. ✅ Results displaying correctly

**Your TrustShield AI app is fully functional!** 🏆

---

## 📞 NEED HELP?

If stuck:
1. Check error message carefully
2. Verify all files are in correct folders
3. Make sure .env files exist (both backend and frontend)
4. Ensure MongoDB is running
5. Try running install commands again
6. Check that ports 8001 and 3000 are not in use

---

## 🎓 WHAT YOU'VE BUILT

- ✨ Real AI-powered scam detection
- ✨ Voice analysis with audio processing
- ✨ Professional mobile app (React Native)
- ✨ REST API backend (FastAPI)
- ✨ Database integration (MongoDB)
- ✨ Cross-platform (iOS, Android, Web)

**This is a complete, production-ready application!** 💪

Good luck with your hackathon presentation! 🚀
