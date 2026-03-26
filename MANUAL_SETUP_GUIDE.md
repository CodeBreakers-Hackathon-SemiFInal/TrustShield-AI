# 📦 TrustShield AI - Complete Manual Setup Guide

## 🎯 What You'll Build
A complete mobile app with AI-powered scam detection that works on your local computer.

---

## 📋 STEP 1: Prerequisites Installation

### Install Required Software

#### 1.1 Install Python 3.11+
**Windows:**
- Download from: https://www.python.org/downloads/
- During installation, CHECK "Add Python to PATH"
- Verify: Open CMD and type `python --version`

**macOS:**
```bash
brew install python@3.11
```

**Linux:**
```bash
sudo apt update
sudo apt install python3.11 python3.11-pip
```

#### 1.2 Install Node.js 18+
**All Platforms:**
- Download from: https://nodejs.org/
- Install LTS version
- Verify: `node --version` and `npm --version`

#### 1.3 Install Yarn
```bash
npm install -g yarn
```
Verify: `yarn --version`

#### 1.4 Install MongoDB

**Windows:**
- Download from: https://www.mongodb.com/try/download/community
- Install MongoDB Community Server
- Start MongoDB: Run "MongoDB" from Start Menu

**macOS:**
```bash
brew tap mongodb/brew
brew install mongodb-community
brew services start mongodb-community
```

**Linux:**
```bash
sudo apt install mongodb
sudo systemctl start mongodb
sudo systemctl enable mongodb
```

Verify MongoDB is running:
```bash
# Should connect without error
mongosh
# Type 'exit' to quit
```

---

## 📁 STEP 2: Create Project Folder Structure

### 2.1 Create Main Folder
```bash
# On Windows (Command Prompt)
mkdir C:\TrustShieldAI
cd C:\TrustShieldAI

# On macOS/Linux (Terminal)
mkdir ~/TrustShieldAI
cd ~/TrustShieldAI
```

### 2.2 Create Subfolders
```bash
mkdir backend
mkdir frontend
```

Your structure should look like:
```
TrustShieldAI/
├── backend/
└── frontend/
```

---

## 🔧 STEP 3: Backend Setup

### 3.1 Create Backend Files

Navigate to backend folder:
```bash
cd backend
```

#### Create `.env` file:
Create a file named `.env` (yes, it starts with a dot) and paste:
```
MONGO_URL=mongodb://localhost:27017/
DB_NAME=trustshield
EMERGENT_LLM_KEY=sk-emergent-185368a407fB3D8511
```

#### Create `requirements.txt`:
Create a file named `requirements.txt` and paste:
```
fastapi==0.110.1
uvicorn==0.25.0
python-dotenv>=1.0.1
pymongo==4.5.0
motor==3.3.1
pydantic>=2.6.4
requests>=2.31.0
numpy>=1.26.0
librosa==0.11.0
soundfile
scipy
pydub
emergentintegrations==0.1.0
```

#### Create `server.py`:
I'll provide this in the next step - it's a large file.

### 3.2 Install Backend Dependencies

**Windows (Command Prompt):**
```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

**macOS/Linux (Terminal):**
```bash
pip3 install -r requirements.txt
```

**Note:** This may take 5-10 minutes as it installs AI and audio processing libraries.

### 3.3 Verify Backend Installation

Test if packages installed correctly:
```bash
python -c "import fastapi, librosa, emergentintegrations; print('Backend packages OK!')"
```

---

## 📱 STEP 4: Frontend Setup

### 4.1 Navigate to Frontend Folder

```bash
# Go back to main folder first
cd ..
# Then go to frontend
cd frontend
```

### 4.2 Create Frontend Files

#### Create `.env` file:
```
EXPO_PUBLIC_BACKEND_URL=http://localhost:8001
```

#### Create `package.json`:
Create a file named `package.json` and paste:
```json
{
  "name": "trustshield-ai",
  "main": "expo-router/entry",
  "version": "1.0.0",
  "scripts": {
    "start": "expo start",
    "android": "expo start --android",
    "ios": "expo start --ios",
    "web": "expo start --web"
  },
  "dependencies": {
    "@expo/vector-icons": "^15.0.3",
    "@react-native-async-storage/async-storage": "^2.2.0",
    "expo": "^54.0.0",
    "expo-av": "~16.0.8",
    "expo-constants": "~18.0.13",
    "expo-file-system": "~19.0.21",
    "expo-router": "~6.0.22",
    "expo-splash-screen": "~31.0.13",
    "expo-status-bar": "~3.0.9",
    "react": "19.1.0",
    "react-native": "0.81.5",
    "react-native-safe-area-context": "~5.6.0"
  },
  "devDependencies": {
    "@babel/core": "^7.25.2",
    "typescript": "~5.9.3"
  },
  "private": true
}
```

#### Create `app.json`:
```json
{
  "expo": {
    "name": "TrustShield AI",
    "slug": "trustshield-ai",
    "version": "1.0.0",
    "orientation": "portrait",
    "icon": "./assets/images/icon.png",
    "scheme": "trustshield",
    "userInterfaceStyle": "dark",
    "ios": {
      "supportsTablet": true,
      "infoPlist": {
        "NSMicrophoneUsageDescription": "Record voice samples for deepfake detection"
      }
    },
    "android": {
      "adaptiveIcon": {
        "foregroundImage": "./assets/images/adaptive-icon.png",
        "backgroundColor": "#0a0e27"
      },
      "permissions": [
        "RECORD_AUDIO"
      ]
    },
    "web": {
      "bundler": "metro",
      "output": "static",
      "favicon": "./assets/images/favicon.png"
    },
    "plugins": [
      "expo-router"
    ]
  }
}
```

### 4.3 Install Frontend Dependencies

```bash
yarn install
```

**Note:** This may take 5-10 minutes. Be patient!

If `yarn install` fails, try:
```bash
npm install
```

---

## 📄 STEP 5: Get All Source Code Files

### 5.1 Backend Source Code

I'll provide you the complete `server.py` file - this is your backend API.

### 5.2 Frontend Source Code Files

You need to create these files in `frontend/app/` folder:

```
frontend/
├── app/
│   ├── _layout.tsx          (Navigation setup)
│   ├── index.tsx            (Home screen)
│   ├── message-detection.tsx
│   ├── voice-detection.tsx
│   ├── result.tsx
│   └── history.tsx
├── assets/
│   └── images/              (Can use default Expo images)
├── .env
├── app.json
└── package.json
```

---

## 🚀 STEP 6: Running the Application

### 6.1 Start MongoDB (if not running)

**Windows:**
- Open Services app → Find "MongoDB" → Start

**macOS:**
```bash
brew services start mongodb-community
```

**Linux:**
```bash
sudo systemctl start mongodb
```

### 6.2 Start Backend Server

Open **Terminal 1** (or CMD):
```bash
cd C:\TrustShieldAI\backend
# or on macOS/Linux: cd ~/TrustShieldAI/backend

# Run the server
uvicorn server:app --host 0.0.0.0 --port 8001 --reload
```

You should see:
```
INFO:     Uvicorn running on http://0.0.0.0:8001
INFO:     Application startup complete.
```

**Keep this terminal open!**

### 6.3 Test Backend

Open browser and go to:
```
http://localhost:8001/api/
```

You should see: `{"message":"TrustShield AI API","status":"active"}`

API Documentation:
```
http://localhost:8001/docs
```

### 6.4 Start Frontend App

Open **Terminal 2** (new terminal/CMD):
```bash
cd C:\TrustShieldAI\frontend
# or on macOS/Linux: cd ~/TrustShieldAI/frontend

# Start Expo
npx expo start
```

You should see:
```
Metro waiting on exp://192.168.x.x:8081
```

### 6.5 View the App

**Option 1: Web Browser (Easiest)**
- Press `w` in the terminal
- Browser will open automatically
- Test the app in browser

**Option 2: Mobile Device (Recommended)**
1. Install "Expo Go" app from App Store/Play Store
2. Scan the QR code shown in terminal
3. App loads on your phone
4. Grant microphone permission when asked

**Option 3: Android Emulator**
- Press `a` in the terminal
- Requires Android Studio

**Option 4: iOS Simulator (macOS only)**
- Press `i` in the terminal
- Requires Xcode

---

## ✅ STEP 7: Testing the App

### Test 1: Message Detection
1. Open app
2. Tap "Check Message"
3. Enter: `URGENT: Your bank account has been suspended. Click here to verify.`
4. Tap "Analyze Message"
5. Should show: **HIGH RISK** with 85-100 score

### Test 2: Voice Analysis
1. Tap "Analyze Voice"
2. Grant microphone permission
3. Tap record button
4. Speak for 3-5 seconds
5. Tap "Stop & Analyze"
6. Should show risk assessment

### Test 3: View History
1. Tap "Detection History"
2. Should show your previous scans
3. Tap any card to view details

---

## 🐛 Common Issues & Solutions

### Issue 1: "Module not found" errors

**Solution:**
```bash
# Backend
cd backend
pip install -r requirements.txt

# Frontend  
cd frontend
yarn install
# or
npm install
```

### Issue 2: "MongoDB connection refused"

**Solution:**
```bash
# Check if MongoDB is running
mongosh

# If error, start MongoDB:
# Windows: Services → MongoDB → Start
# macOS: brew services start mongodb-community
# Linux: sudo systemctl start mongodb
```

### Issue 3: "Port 8001 already in use"

**Solution:**
```bash
# Kill process on port 8001
# Windows:
netstat -ano | findstr :8001
taskkill /PID <PID_NUMBER> /F

# macOS/Linux:
lsof -ti:8001 | xargs kill -9
```

### Issue 4: "Cannot connect to backend" in app

**Solution:**
1. Verify backend is running: http://localhost:8001/api/
2. Check `frontend/.env` has: `EXPO_PUBLIC_BACKEND_URL=http://localhost:8001`
3. Restart frontend: Press `r` in terminal

### Issue 5: "Expo Go can't connect"

**Solution:**
1. Make sure phone and computer are on same WiFi
2. Try using tunnel: `npx expo start --tunnel`
3. Or use web browser instead (press `w`)

### Issue 6: Python command not found

**Windows Solution:**
```bash
# Use 'python' instead of 'python3'
python --version
```

**macOS/Linux Solution:**
```bash
# Use 'python3'
python3 --version
```

---

## 📝 Quick Reference Commands

### Starting Everything (Daily Use)

**Terminal 1 - Backend:**
```bash
cd backend
uvicorn server:app --host 0.0.0.0 --port 8001 --reload
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npx expo start
```

**That's it!** Keep both terminals open while using the app.

### Stopping Everything

- Press `Ctrl+C` in both terminals
- Close terminals

---

## 📂 Files Checklist

Make sure you have ALL these files:

### Backend Files:
- [ ] `backend/.env`
- [ ] `backend/requirements.txt`
- [ ] `backend/server.py`

### Frontend Files:
- [ ] `frontend/.env`
- [ ] `frontend/package.json`
- [ ] `frontend/app.json`
- [ ] `frontend/app/_layout.tsx`
- [ ] `frontend/app/index.tsx`
- [ ] `frontend/app/message-detection.tsx`
- [ ] `frontend/app/voice-detection.tsx`
- [ ] `frontend/app/result.tsx`
- [ ] `frontend/app/history.tsx`

---

## 🎯 Next Steps

1. Follow this guide step by step
2. Don't skip any steps
3. If you get errors, check "Common Issues" section
4. Test all features before your hackathon
5. Prepare your demo using the sample messages

---

## 📞 Need Help?

If something doesn't work:
1. Check error message carefully
2. Look in "Common Issues" section above
3. Make sure MongoDB is running
4. Verify both backend and frontend are running
5. Check browser console (F12) for frontend errors
6. Check backend terminal for API errors

---

## 🎉 Success Indicators

You'll know it's working when:
- ✅ Backend shows: "Application startup complete"
- ✅ Browser opens: http://localhost:8001/docs (API docs)
- ✅ Frontend shows: QR code and options
- ✅ App loads and shows home screen
- ✅ Message detection returns results
- ✅ Stats update after each scan

---

**Good luck with your hackathon! 🏆**

You're building a real AI-powered security app - that's impressive! 💪
