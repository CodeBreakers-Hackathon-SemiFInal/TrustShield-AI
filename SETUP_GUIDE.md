# 🚀 TrustShield AI - Quick Setup Guide

## Prerequisites
- Node.js 18+ and Yarn
- Python 3.11+
- MongoDB running locally
- Expo Go app (for mobile testing)

## Installation Steps

### 1. Backend Setup
```bash
cd /app/backend

# Install dependencies
pip install -r requirements.txt

# Verify .env file exists with:
# MONGO_URL=mongodb://localhost:27017/
# DB_NAME=trustshield
# EMERGENT_LLM_KEY=sk-emergent-185368a407fB3D8511

# Start backend server
uvicorn server:app --host 0.0.0.0 --port 8001 --reload
```

Backend will be available at: `http://localhost:8001`
API documentation: `http://localhost:8001/docs`

### 2. Frontend Setup
```bash
cd /app/frontend

# Install dependencies
yarn install

# Verify .env file has EXPO_PUBLIC_BACKEND_URL set

# Start Expo development server
yarn start
```

### 3. Testing the App

#### On Web Browser
- Open the URL shown in terminal (usually http://localhost:3000)
- Test all features in browser

#### On Mobile Device (Recommended)
1. Install **Expo Go** app from App Store/Play Store
2. Scan the QR code shown in terminal
3. App will load on your device
4. Grant microphone permissions when prompted

## Testing Scenarios

### Message Detection Tests

#### Test 1: HIGH RISK Scam
```
URGENT: Your bank account has been suspended. Click here to verify your identity immediately or risk permanent closure.
```
**Expected**: Risk Score 85-100, HIGH RISK

#### Test 2: MEDIUM RISK
```
Congratulations! You have won $1,000,000 in the lottery. Claim your prize now by providing your credit card details.
```
**Expected**: Risk Score 30-60, MEDIUM RISK

#### Test 3: LOW RISK (Safe)
```
Hi, are we still meeting for lunch at 2pm today?
```
**Expected**: Risk Score 0-15, LOW RISK

### Voice Analysis Test
1. Tap "Analyze Voice"
2. Allow microphone permission
3. Record 3-5 seconds of voice
4. Tap "Stop & Analyze"
5. View risk assessment

## API Testing with curl

```bash
# Test root endpoint
curl http://localhost:8001/api/

# Test message detection
curl -X POST http://localhost:8001/api/detect-message \
  -H "Content-Type: application/json" \
  -d '{"message": "URGENT: Your account has been suspended. Click here to verify."}'

# Get statistics
curl http://localhost:8001/api/stats

# Get history
curl http://localhost:8001/api/history
```

## Common Issues & Solutions

### Issue: "Cannot connect to backend"
**Solution**: Ensure backend is running on port 8001

### Issue: "Microphone permission denied"
**Solution**: Go to device settings and enable microphone for Expo Go

### Issue: "MongoDB connection error"
**Solution**: Ensure MongoDB is running: `sudo systemctl start mongod`

### Issue: "Expo not loading"
**Solution**: Clear cache and restart: `expo start -c`

## Architecture Overview

```
Mobile App (Expo) ←→ Backend API (FastAPI) ←→ MongoDB
                          ↓
                    OpenAI GPT-5.2
                    (via Emergent LLM Key)
```

## Features Implemented

✅ Message scam detection (AI + Keywords)
✅ Voice deepfake analysis (Audio features)
✅ Risk scoring (0-100 scale)
✅ Detection history with persistence
✅ Statistics dashboard
✅ Beautiful mobile UI with animations
✅ Cross-platform (iOS, Android, Web)

## Technologies Used

- **Frontend**: React Native, Expo Router
- **Backend**: FastAPI, Python
- **Database**: MongoDB
- **AI**: OpenAI GPT-5.2
- **Audio**: Librosa, expo-av
- **Deployment**: Can be deployed to Expo EAS, Vercel, Railway

## Hackathon Presentation Tips

1. **Start with Problem**: Show fraud statistics
2. **Demo Message Detection**: Use HIGH risk sample
3. **Demo Voice Analysis**: Record live
4. **Show Architecture**: Use diagram from documentation
5. **Highlight Tech**: AI integration, audio processing
6. **Explain Impact**: Real-world use cases
7. **Discuss Future**: ML models, browser extension

## Development Notes

- AI analysis uses OpenAI GPT-5.2 (real API calls, not mocked)
- Keyword detection has 30+ scam patterns
- Voice analysis uses 4 audio features
- All detections saved to MongoDB
- Mobile-first design with responsive UI

## Support

For issues or questions:
- Check `/app/PROJECT_DOCUMENTATION.md` for detailed info
- Review API docs at `http://localhost:8001/docs`
- Test backend endpoints with Swagger UI

---

**Ready to Demo!** 🎉

The app is fully functional and ready for hackathon presentation. All features are working:
- ✅ Backend API tested and verified
- ✅ AI integration operational
- ✅ Database connectivity confirmed
- ✅ Mobile UI complete
- ✅ Audio processing functional

Good luck with your hackathon! 🏆
