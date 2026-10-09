# ClassConnectAI — AI-Powered Smart Education and Student Skill Development Platform

ClassConnectAI is a comprehensive full-stack web application engineered to bridge the gap between classroom announcements and measurable student skill mastery. It converts unstructured academic notices (in English and regional languages like Telugu) into structured, actionable tasks, identifies student concept gaps via diagnostic assessments, and provides personalized learning roadmaps with interactive AI-guided practice.

---

## 🚀 Key Features

### 1. 📢 Smart Classroom Assistant (CR Studio & Verification)
- **Multilingual Input Support**: Ingest raw notices via plain text, Telugu language messages, or OCR text snippets.
- **AI-Powered Structured Extraction**: Extracts Subject, Task Title, Task Instructions, Deadlines, and Resource Links into validated JSON.
- **CR Verification & Side-by-Side Review**: Class Representatives can review original text alongside extracted fields, edit details, confirm relative dates (e.g. "tomorrow" / "రేపు"), and approve before broadcasting.
- **Class-Restricted Student Feed**: Only approved notices are broadcasted to enrolled students with urgency countdown badges.

### 2. 🎯 AI Skill Gap Analyzer (DBMS Diagnostics)
- **5 Core Topics**: SQL Basics, SQL Joins, Keys & Constraints, Normalization, and Transactions.
- **Deterministic Backend Scoring**: Real-time evaluation of question accuracy and topic-wise mastery.
- **Skill Gap Classification**:
  - 🟢 **Strong** ($\ge 70\%$)
  - 🟡 **Moderate** ($50\% - 69\%$)
  - 🔴 **Needs Practice** ($< 50\%$)

### 3. 🗺️ Personalized Learning Roadmap
- **Dynamic Pathway Generation**: Based on diagnostic quiz gaps, creates tailored 3-step learning milestones (Conceptual Study $\rightarrow$ Application Practice $\rightarrow$ Diagnostic Reassessment).
- **Curated Learning Links**: Points students to faculty-approved tutorials (W3Schools, GeeksforGeeks).
- **Interactive Completion Tracking**: Check off completed roadmap tasks and track overall percentage progress.

### 4. 💡 Interactive Practice Arena & AI Feedback
- **Topic & Difficulty Filtering**: Practice beginner, intermediate, and advanced challenge questions.
- **Instant Objective Checking**: Immediate feedback on correctness.
- **✨ AI Concept Breakdown**: Empathetic AI explanations explaining the core concept in simple terms, accompanied by helpful hints without harsh tone.

### 5. 📈 Skill Improvement Tracker (Recharts Analytics)
- **Measured Improvement Delta**: Visualizes exact score change percentages between attempts (e.g., $40\% \rightarrow 70\% = \mathbf{+30.0\%}$ improvement).
- **Topic Mastery Visualizer**: Bar charts displaying accuracy per DBMS topic.
- **Assessment Attempt History**: Chronological log of scores and dates.
- **AI Next-Step Guidance**: Concrete recommendations based on current student data.

---

## 🛠️ Technology Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 18, Vite, CSS (Custom Design System), Lucide React, Recharts, Axios |
| **Backend** | Python 3.11, FastAPI, SQLAlchemy, Pydantic v2, PyJWT, Bcrypt, Uvicorn |
| **Database** | SQLite (zero-setup out-of-the-box) or MySQL via SQLAlchemy |
| **AI Integration** | Google Gemini API with robust rule-based deterministic fallback engine |

---

## ⚡ Quick Start & Run Instructions (Windows 11 / VS Code)

### 1. Backend Setup & Run

Open a terminal in the root directory:

```powershell
# Navigate to backend
cd backend

# Install dependencies
pip install -r requirements.txt

# Run the backend server (starts on http://127.0.0.1:8000)
python run.py
```
> The backend automatically creates SQLite database tables and seeds demo accounts, 25+ DBMS questions, and sample announcements on startup!

API Documentation will be available at: **[http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)**

---

### 2. Frontend Setup & Run

Open a second terminal in the root directory:

```powershell
# Navigate to frontend
cd frontend

# Install dependencies
npm.cmd install

# Start Vite development server (starts on http://localhost:5173)
npm.cmd run dev
```

Open **[http://localhost:5173](http://localhost:5173)** in your browser!

---

## 🔑 Pre-Seeded Demonstration Accounts (1-Click Switcher)

The application includes built-in **1-Click Quick Demo Login** buttons on the Login page and top navigation bar:

| Role | Email | Password | Access & Capabilities |
|---|---|---|---|
| **🎓 Student** | `student@classconnect.ai` | `student123` | Classroom Feed, Diagnostic Quizzes, Personalized Roadmap, Practice Arena, Analytics |
| **🛡️ Class Rep (CR)** | `cr@classconnect.ai` | `cr123` | Notice Submission Studio, AI Extraction, Side-by-Side Verification, Approve/Reject |
| **👨‍🏫 Faculty** | `faculty@classconnect.ai` | `faculty123` | Department Overview, DBMS Question Bank Manager (Add/Delete), Student Roster |

---

## 🧪 End-to-End Demonstration Workflow

1. **CR Ingestion & Verification**:
   - Log in as **Class Representative (`cr@classconnect.ai`)**.
   - Go to **Notice Studio (CR)**.
   - Click **"🇮🇳 Load Telugu Demo"** (or paste any notice text).
   - Click **"Extract Structured Task with AI"**.
   - Review the side-by-side extracted fields (Subject, Title, Description, Translation, Deadline). Notice the relative date confirmation banner!
   - Click **"Approve & Publish to Students"**.

2. **Student Feed & Diagnostic Quiz**:
   - Switch to **Student (`student@classconnect.ai`)**.
   - View the newly published task on the Dashboard.
   - Click **"Diagnostic Quiz"** and complete the 10-question DBMS assessment.
   - View your score and topic-wise skill breakdown (SQL Basics, SQL Joins, Keys, Normalization, Transactions).

3. **Personalized Roadmap & Practice**:
   - On the results page, click **"Generate Personalized Learning Roadmap"**.
   - Follow the step-by-step milestones targeted at your weak topics and check off completed tasks.
   - Go to **Practice Arena**, choose your weak topic, submit an answer, and click **"✨ Explain Concept with AI Tutor"** for friendly concept breakdowns.

4. **Reassessment & Improvement Tracker**:
   - Retake the diagnostic assessment and score higher.
   - Navigate to **Skill Analytics** to view the Recharts LineChart displaying your score progression and the **+30% Improvement Delta**!

---

## 📂 Project Structure

```
portfolio/
├── backend/
│   ├── app/
│   │   ├── __init__.py
│   │   ├── main.py              # FastAPI app & CORS
│   │   ├── database.py          # SQLAlchemy SQLite / MySQL
│   │   ├── models.py            # 9 Relational database models
│   │   ├── schemas.py           # Pydantic request & response models
│   │   ├── auth.py              # Native Bcrypt & JWT security
│   │   ├── ai_service.py        # Gemini API & intelligent NLP engine
│   │   ├── seed.py              # 25+ DBMS questions & initial demo state
│   │   └── routers/
│   │       ├── auth.py          # Authentication & class management
│   │       ├── announcements.py # CR workflow & student feeds
│   │       ├── ai.py            # AI notice extraction & explanation
│   │       ├── quiz.py          # Diagnostic quiz scoring
│   │       ├── skills.py        # Roadmaps, practice & progress tracking
│   │       └── admin.py         # Faculty portal & question bank
│   ├── tests/
│   │   └── test_api.py          # Comprehensive test suite
│   ├── requirements.txt
│   ├── .env.example
│   ├── .env
│   └── run.py
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Navbar.jsx       # Header with 1-click role switcher
│   │   │   ├── Sidebar.jsx      # Role-aware navigation sidebar
│   │   │   ├── Badge.jsx        # Status & difficulty badges
│   │   │   ├── Modal.jsx        # Reusable modal dialog
│   │   │   └── LoadingSpinner.jsx
│   │   ├── context/
│   │   │   └── AuthContext.jsx  # JWT state & demo account coordinator
│   │   ├── pages/
│   │   │   ├── AuthPage.jsx            # Login & Register
│   │   │   ├── StudentDashboard.jsx    # Student overview
│   │   │   ├── CRDashboard.jsx         # CR Notice studio & verifier
│   │   │   ├── AnnouncementsPage.jsx   # Classroom tasks feed
│   │   │   ├── DiagnosticQuizPage.jsx  # DBMS quiz runner
│   │   │   ├── QuizResultPage.jsx      # Skill gap results
│   │   │   ├── LearningRoadmapPage.jsx # Tailored learning roadmap
│   │   │   ├── PracticePage.jsx        # Interactive practice & AI tutor
│   │   │   ├── ProgressTrackerPage.jsx # Recharts analytics & score delta
│   │   │   └── FacultyDashboard.jsx    # Faculty admin portal
│   │   ├── api.js               # Axios instance with interceptors
│   │   ├── App.css              # Custom styling
│   │   ├── index.css            # Design tokens & typography
│   │   ├── App.jsx              # Main layout & router
│   │   └── main.jsx
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
└── README.md
```
