# 🚀 **Antriview — The Agentic AI Interview Partner**

**Submission for:** Eightfold AI Agent Building Assignment  
**Problem Statement:** Interview Practice Partner  
**Status:** Production Ready

---

## 1️⃣ **Executive Summary**

Antriview is a **multi-modal, adaptive AI platform** designed to simulate **high-pressure job interviews**.  
Unlike standard chatbots, Antriview operates as a **Goal-Driven Agentic System** with a **Voice-First architecture** and real-time **RAG (Retrieval Augmented Generation)**.  
The system follows a **structured interview protocol**, adapts its personality (**Technical** vs **HR**), and provides **brutally honest** but constructive feedback.

---

## 2️⃣ **Agentic Capabilities (🧠 The "Brain")**

To implement **Intelligent Agentic Behavior**, Antriview uses a cognitive OODA loop (**Observe, Orient, Decide, Act**) for each conversation turn.

### A. 🔄 **Finite State Machine (8-Phase Protocol)**

| Phase         | Description                                      |
|---------------|--------------------------------------------------|
| 🗣️ **Introduction** | Establish rapport, lower candidate anxiety         |
| 🧐 **Screening**    | Verify basic fit based on the Job Description      |
| 🛠️ **Adaptation**   | Switch strategy; provide hints if user struggles   |
| 📝 **Follow-Up**    | Dynamic probing based on specific answers          |
| 🔍 **Deep Dive**    | Drill into uploaded Resume skills                  |
| 🎭 **Scenario**     | Situational judgment test                          |
| 💬 **Feedback**     | Immediate, brief validation                        |
| 🎯 **Closing**      | End the session professionally                     |

---

### B. 🕸️ **Reasoning Loop (Chain-of-Thought)**

- **👀 Perception:** Observer Agent analyzes audio for hesitation/silence (>2s)
- **🔍 Retrieval:** RAG Engine fetches relevant details from ChromaDB
- **🤔 Decision:** Interviewer Agent decides next steps
- **🗣️ Execution:** Response synthesized to speech via Vapi.ai

---

### C. 🧑‍🤝‍🧑 **Multi-Agent Orchestration**

- 🕵️ **Observer Agent:** Monitors sentiment and engagement  
- 👔 **Interviewer Agent:** Manages questioning logic  
- ⚖️ **Evaluator Agent:** Performs post-interview gap analysis

---

## 3️⃣ **System Architecture**

- **🎨 Frontend:** Next.js for UI, camera, Clerk authentication, VAD visualization
- **🔊 Voice:** Vapi.ai manages audio (WebRTC), Deepgram transcription, 11Labs speech synthesis, interruption handling
- **🧠 Cognitive Layer:** Python FastAPI runs OODA agent loops, RAG, logic
- **💾 Persistence:** Firebase Firestore (profiles, history, feedback), Clerk (identity/session)

---

## 4️⃣ **Design Decisions & Trade-Offs**

| Area          | Reasoning/Trade-off                                                                         | Choice                           |
|---------------|---------------------------------------------------------------------------------------------|----------------------------------|
| **Hybrid Stack**        | Python superior for AI and RAG, JS for UI interactivity           | **Next.js + Python FastAPI**     |
| **Gemini 2.5 Flash Lite** | Sub-second response needed for voice; Gemini ~800ms avg         | **Gemini 2.5 Flash Lite (LLM)**  |
| **Vapi.ai**   | Barge-in handling, avoids WebRTC complexity                           | **Vapi.ai for speech**           |
| **Firestore** | Flexible, real-time for nested feedback                                | **Firebase Firestore**           |

---

## 5️⃣ **Tech Stack**

| 🧩 **Component**      | **Technology**               | **Purpose**                                  |
|----------------------|-----------------------------|----------------------------------------------|
| Frontend             | Next.js 14 (App Router)     | Reactive UI, camera, state management        |
| Styling              | Tailwind CSS + Lucide       | Modern, responsive design                    |
| Auth                 | Clerk                       | User/session management                      |
| Backend              | Python FastAPI              | Async API, agent orchestration               |
| Database             | Firebase Firestore          | History/analytics storage                    |
| Vector DB            | ChromaDB                    | RAG context retrieval                        |
| LLM                  | Google Gemini 2.5           | Reasoning, content generation                |
| Voice                | Vapi.ai                     | Speech-to-text/text-to-speech pipeline       |

---

## 6️⃣ **Setup Instructions**

### ⚙️ Prerequisites

- Node.js 18+
- Python 3.10+
- Google Cloud Project (Firebase)
- Vapi.ai Account (Public Key)
- Clerk Account (Publishable Keys)
- Google Gemini API Key

### 🧠 Backend Setup

cd backend

python -m venv venv

Windows: venv\Scripts\activate

Mac/Linux: source venv/bin/activate

pip install -r requirements.txt

- **Firebase:** Generate a private key, name it `serviceAccountKey.json`, place in `/backend`.
- **Environment:** Add your Gemini key to `.env` in `/backend`:
- GOOGLE_API_KEY=your_gemini_api_key_here
- **Start server:**
- python -m app.main

Runs at http://127.0.0.1:8000


### 💻 Frontend Setup

cd frontend

npm install

- **Environment:** Create `.env.local` in `/frontend`:
```
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_...
CLERK_SECRET_KEY=sk_test_...
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/
NEXT_PUBLIC_BACKEND_URL=http://127.0.0.1:8000
NEXT_PUBLIC_VAPI_PUBLIC_KEY=your_vapi_public_key
NEXT_PUBLIC_VAPI_ASSISTANT_ID=your_vapi_assistant_id
```
- **Start app:**

npm run dev

Runs at http://localhost:3000


---

## 7️⃣ **How to Use**

1. **🔓 Sign In:**  
 Go to `http://localhost:3000`, click **Get Started**, and authenticate.

2. **🛠️ Setup Session:**  
 - Paste your job description
 - Select interview style (Technical/HR)
 - Upload resume (PDF)

3. **🎙️ Begin Interview:**  
 - Click **Begin Interview**
 - Grant microphone & camera permissions
 - Wait for agent intro and respond when "Listening..." appears  
 - *Optionally switch to Chat Mode (type answers; AI still speaks)*

4. **📈 Get Feedback:**  
 Click **End & Feedback**, wait a few seconds, and view score, transcript, and advice.

5. **📊 Analytics:**  
 Use the **Dashboard** to track progress, scores, and session history.

---

**✨ Interview smarter, get honest feedback, and advance your career — with Antriview! ✨**
