# 🛡️ TrustShield AI - Real-Time Scam & Deepfake Detection System

> A comprehensive AI-powered mobile application for detecting scams and deepfakes - Built for hackathon by second-year B.Tech CSE students

---

## 📋 PROJECT OVERVIEW

**TrustShield AI** is an intelligent security application that protects users from:
- **Scam Messages** - Detecting fraudulent SMS, emails, and messages using AI
- **Voice Deepfakes** - Identifying voice cloning and synthetic speech patterns

### Why It Matters
- **$5.8 billion** lost to scams in 2023 (FTC Report)
- **Voice cloning technology** makes fraud calls more convincing
- **Real-time detection** helps users make informed decisions

### Target Users
- General public receiving suspicious messages
- Elderly population vulnerable to fraud
- Business professionals handling sensitive communications

---

## 🏗️ SYSTEM ARCHITECTURE

```
┌─────────────────────────────────────────────────────────────┐
│                      MOBILE APP (Expo)                       │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ Message      │  │ Voice        │  │ History      │      │
│  │ Detection    │  │ Analysis     │  │ View         │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└────────────────────────────┬────────────────────────────────┘
                             │ HTTP/REST API
┌────────────────────────────▼────────────────────────────────┐
│                    BACKEND (FastAPI)                         │
│  ┌──────────────────┐              ┌──────────────────┐     │
│  │ Scam Detection   │              │ Voice Analysis   │     │
│  │ Engine           │              │ Engine           │     │
│  │ - Keywords       │              │ - Pitch          │     │
│  │ - AI Analysis    │              │ - Frequency      │     │
│  └──────────────────┘              └──────────────────┘     │
└────────────────────────────┬────────────────────────────────┘
                             │
┌────────────────────────────▼────────────────────────────────┐
│               DATABASE (MongoDB)                             │
│  - Detection History  - Risk Scores  - Analytics            │
└──────────────────────────────────────────────────────────────┘
```

---

## ⚙️ TECH STACK

### Frontend (Mobile App)
- **Framework**: React Native with Expo
- **Navigation**: Expo Router (file-based routing)
- **UI Components**: React Native built-in + Expo Vector Icons
- **State Management**: React Hooks
- **Audio Recording**: expo-av
- **Storage**: @react-native-async-storage/async-storage

### Backend (API Server)
- **Framework**: FastAPI (Python)
- **AI Integration**: OpenAI GPT-5.2 via Emergent Integrations
- **Audio Processing**: Librosa + NumPy + SciPy
- **Database**: MongoDB with Motor (async driver)
- **API Documentation**: Auto-generated Swagger/OpenAPI

### AI & ML
- **Text Analysis**: OpenAI GPT-5.2 (via Emergent LLM Key)
- **Keyword Detection**: Custom algorithm with 30+ scam patterns
- **Audio Analysis**: Librosa for feature extraction
- **Risk Scoring**: Hybrid algorithm combining multiple signals

### Database
- **MongoDB**: Document store for detection history
- **Collections**: `detections` (stores all scans with metadata)

---

## 🔄 USER WORKFLOW

### Message Scam Detection
1. User opens app → Taps "Check Message"
2. Enters or pastes suspicious message
3. Taps "Analyze Message"
4. **Backend processes**:
   - Scans for 30+ scam keywords (urgent, verify, bank, prize, etc.)
   - Sends to OpenAI GPT-5.2 for AI analysis
   - Calculates risk score (0-100)
5. User sees result:
   - Risk level: LOW / MEDIUM / HIGH
   - Detected patterns
   - AI explanation
6. Result saved to history

### Voice Analysis
1. User opens app → Taps "Analyze Voice"
2. Grants microphone permission
3. Records voice sample (3+ seconds)
4. Taps "Stop & Analyze"
5. **Backend processes**:
   - Analyzes pitch variation (robotic patterns)
   - Checks speaking rate (too fast/slow)
   - Examines spectral features (synthetic signatures)
   - Calculates zero-crossing rate (noise patterns)
6. User sees risk assessment with explanation
7. Result saved to history

---

## 🤖 AI APPROACH

### 1. Scam Detection (Hybrid Model)

#### Keyword-Based Detection (70% weight)
- 30+ scam keywords with severity weights
- Examples:
  - "urgent" (15 points)
  - "verify your identity" (20 points)
  - "click here" (20 points)
  - "suspended account" (15 points)

#### AI Analysis (30% weight)
- Uses OpenAI GPT-5.2
- Analyzes context and intent
- Identifies sophisticated scam patterns
- Provides human-readable explanation

#### Risk Calculation
```
Score = Keyword_Score + AI_Sentiment_Score
Risk Level:
  - LOW: 0-24
  - MEDIUM: 25-49
  - HIGH: 50-100
```

### 2. Voice Deepfake Detection (Feature-Based)

#### Audio Features Analyzed
1. **Pitch Variation**
   - Natural speech: moderate variation
   - Synthetic: unusually consistent or erratic

2. **Speaking Rate** (Tempo)
   - Normal: 60-180 BPM
   - Suspicious: <60 or >180 BPM

3. **Spectral Centroid & Rolloff**
   - Measures frequency distribution
   - Synthetic voices have distinct signatures

4. **Zero-Crossing Rate**
   - High ZCR indicates processing artifacts
   - Natural speech: lower, varied ZCR

#### Risk Scoring
```
Each suspicious pattern = 25 points
Max score = 100
Risk Level: Same as message detection
```

---

## 📱 MOBILE UI DESIGN

### Screen 1: Home
- **Logo & Title**: TrustShield AI branding
- **Stats Card**: Shows total scans and risk distribution
- **3 Action Buttons**:
  1. Check Message (Blue gradient)
  2. Analyze Voice (Pink gradient)
  3. Detection History (Cyan gradient)
- **Info Section**: Brief explanation

### Screen 2: Message Detection
- **Text Input**: Multi-line for message entry
- **Sample Messages**: 4 pre-loaded examples for testing
- **Analyze Button**: Triggers detection
- **Instructions**: How to use

### Screen 3: Voice Detection
- **Recording Button**: Large circular button
- **Timer**: Shows recording duration
- **Pulse Animation**: Visual feedback while recording
- **Stop Button**: Ends recording and analyzes
- **Instructions**: 3-step guide

### Screen 4: Results
- **Risk Badge**: Color-coded (Red/Orange/Green)
- **Risk Score**: X/100 display
- **Explanation Card**: Why this risk level
- **Patterns List**: Detected issues
- **AI Analysis**: GPT-5.2 insights
- **Action Buttons**: Home, View History

### Screen 5: History
- **Detection Cards**: Type, content preview, risk badge
- **Pull to Refresh**: Update history
- **Tap to View**: See full details
- **Empty State**: Prompt to start scanning

---

## 🔌 API DESIGN

### Base URL
```
http://localhost:8001/api
```

### Endpoints

#### 1. Root
```http
GET /api/
Response: {"message": "TrustShield AI API", "status": "active"}
```

#### 2. Message Detection
```http
POST /api/detect-message
Content-Type: application/json

Request:
{
  "message": "URGENT: Your account has been suspended..."
}

Response:
{
  "id": "uuid",
  "type": "message",
  "content": "URGENT: Your account...",
  "risk_level": "HIGH",
  "risk_score": 85,
  "explanation": "Detected 5 suspicious patterns: urgent, account, suspended...",
  "detected_patterns": ["urgent", "suspended", "verify"],
  "ai_analysis": "This message shows classic phishing characteristics...",
  "timestamp": "2025-07-15T10:30:00Z"
}
```

#### 3. Voice Analysis
```http
POST /api/analyze-voice
Content-Type: application/json

Request:
{
  "audio_base64": "base64_encoded_audio_data",
  "duration": 5.2
}

Response:
{
  "id": "uuid",
  "type": "voice",
  "content": "Audio analysis (5.2s)",
  "risk_level": "MEDIUM",
  "risk_score": 50,
  "explanation": "Voice has unnaturally consistent pitch...",
  "detected_patterns": ["Unusually consistent pitch (robotic)", "High frequency emphasis"],
  "ai_analysis": null,
  "timestamp": "2025-07-15T10:35:00Z"
}
```

#### 4. Detection History
```http
GET /api/history?limit=50

Response:
{
  "detections": [
    {
      "id": "uuid",
      "type": "message",
      "risk_level": "HIGH",
      ...
    }
  ],
  "total": 15
}
```

#### 5. Statistics
```http
GET /api/stats

Response:
{
  "total_scans": 42,
  "high_risk": 8,
  "medium_risk": 12,
  "low_risk": 22
}
```

---

## 🚀 IMPLEMENTATION PLAN

### Phase 1: Setup (Day 1)
- [x] Initialize Expo project
- [x] Set up FastAPI backend
- [x] Configure MongoDB connection
- [x] Integrate OpenAI via Emergent LLM key

### Phase 2: Core Features (Day 2-3)
- [x] Implement keyword-based scam detection
- [x] Integrate AI analysis (GPT-5.2)
- [x] Build voice recording functionality
- [x] Implement audio feature extraction
- [x] Create risk scoring algorithms

### Phase 3: UI Development (Day 3-4)
- [x] Design home screen with navigation
- [x] Build message detection screen
- [x] Create voice analysis screen
- [x] Implement results display
- [x] Add detection history view

### Phase 4: Integration & Testing (Day 4-5)
- [x] Connect frontend to backend APIs
- [x] Test all detection scenarios
- [x] Fix bugs and edge cases
- [x] Optimize performance

### Phase 5: Demo Preparation (Day 5-6)
- [x] Create sample test data
- [x] Prepare presentation materials
- [x] Document architecture
- [x] Practice demo flow

---

## 🏆 HACKATHON VALUE

### Innovation
- **Hybrid Detection**: Combines rule-based and AI approaches
- **Dual Protection**: Both text and voice analysis
- **Real-time Results**: Instant feedback to users

### Technical Depth
- **Modern Stack**: React Native, FastAPI, MongoDB
- **AI Integration**: Production-grade OpenAI GPT-5.2
- **Audio Processing**: Advanced signal analysis with Librosa
- **Mobile-First**: Native app experience

### Practical Impact
- **Solves Real Problem**: $5.8B fraud losses annually
- **Easy to Use**: Simple, intuitive interface
- **Scalable Architecture**: Can handle growth
- **Database Integration**: Persistent storage

### Learning Outcomes (For Team)
- Mobile app development with React Native
- Backend API design with FastAPI
- AI integration (OpenAI)
- Audio signal processing
- Database operations (MongoDB)
- Full-stack deployment

### Future Enhancements
1. **Machine Learning Model**: Train custom deepfake detection model
2. **Multi-language Support**: Detect scams in various languages
3. **Browser Extension**: Check emails and websites
4. **Community Reports**: Crowdsourced scam database
5. **Real-time Alerts**: Push notifications for new threats
6. **Call Screening**: Integrate with phone app for live call analysis

---

## 📊 PROJECT STATISTICS

- **Total Files**: 8 main components
- **Lines of Code**: ~2000+
- **API Endpoints**: 5
- **Screens**: 5
- **Scam Keywords**: 30+
- **Audio Features**: 4 types
- **Development Time**: 5-6 days

---

## 🎯 DEMO SCRIPT

### 1. Introduction (30 seconds)
"TrustShield AI protects users from scams and deepfakes using AI-powered detection."

### 2. Message Detection Demo (1 minute)
- Open app, tap "Check Message"
- Paste HIGH risk sample: "URGENT: Your bank account..."
- Show result: HIGH RISK with explanation
- Highlight detected patterns and AI analysis

### 3. Voice Analysis Demo (45 seconds)
- Tap "Analyze Voice"
- Record sample voice
- Show audio processing
- Display risk assessment

### 4. History & Stats (30 seconds)
- Show detection history
- Display statistics dashboard
- Explain data persistence

### 5. Technical Highlights (45 seconds)
- Architecture diagram
- AI integration (OpenAI GPT-5.2)
- Audio processing (Librosa)
- Database (MongoDB)

### 6. Impact & Future (30 seconds)
- Real-world problem ($5.8B fraud)
- Scalability potential
- Future enhancements

**Total Demo Time**: 4 minutes

---

## 👥 TEAM CONTRIBUTION AREAS

For a team of 6 second-year B.Tech students:

1. **Backend Developer**: FastAPI, MongoDB, API design
2. **AI/ML Engineer**: OpenAI integration, risk scoring algorithms
3. **Audio Processing**: Librosa, voice analysis features
4. **Frontend Developer 1**: Navigation, Home, History screens
5. **Frontend Developer 2**: Detection screens, Results display
6. **Full-Stack/DevOps**: Integration, testing, documentation

---

## 🔑 KEY TAKEAWAYS

✅ **Simple Yet Effective**: Uses proven detection methods suitable for 2nd year students  
✅ **Real AI Integration**: Not mocked - actual OpenAI GPT-5.2  
✅ **Production-Ready**: Working app with database and APIs  
✅ **Demo-Friendly**: Multiple test scenarios built-in  
✅ **Scalable Design**: Architecture supports future enhancements  
✅ **Learning Project**: Covers full-stack, AI, mobile, and audio processing  

---

## 📝 TECHNICAL NOTES

### Why This Stack?
- **Expo**: Fastest way to build cross-platform mobile apps
- **FastAPI**: Modern, fast, auto-documented APIs
- **MongoDB**: Flexible schema for evolving requirements
- **OpenAI**: Industry-leading language models
- **Librosa**: Standard for audio analysis

### Realistic for 2nd Year Students?
✅ **Yes** - Each component uses well-documented libraries  
✅ **Yes** - Architecture is simple and understandable  
✅ **Yes** - Code is clean and well-commented  
✅ **Yes** - Focuses on integration over building from scratch  

### What Makes It Impressive?
- Working AI integration (not mocked)
- Beautiful, professional UI
- Real audio processing
- Full database integration
- Complete end-to-end functionality

---

## 🎓 CONCLUSION

TrustShield AI demonstrates strong technical skills while solving a real-world problem. It combines modern technologies (React Native, FastAPI, OpenAI) with practical security applications. The project is ambitious yet achievable for second-year B.Tech students, showcasing both breadth (full-stack) and depth (AI, audio processing) of knowledge.

**Perfect for hackathon presentation** - It's impressive, understandable, and actually works! 🚀

---

**Built with ❤️ by Second-Year B.Tech CSE Students**  
**Tech Stack**: React Native • FastAPI • MongoDB • OpenAI GPT-5.2 • Librosa
