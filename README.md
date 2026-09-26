# PrepAI — AI-Powered Interview Preparation Platform

PrepAI is a full-stack MERN application that helps engineering candidates prepare for technical and behavioral interviews. It combines an AI interview coach, a LeetCode-style coding practice environment, resume analysis, and timed contests in one platform.

## Features

- **AI Mock Interviews** — Multi-turn interview engine with stateful conversation history that adapts questions to the target company, role, and round type, then scores answers against a STAR-framework rubric (clarity, depth, relevance, and more).
- **Coding Practice** — Monaco-based code editor with 150+ dynamically generated problems across 15+ topics, in-browser code execution, and a submission history.
- **Contests** — Timed coding contests with leaderboards and submission tracking.
- **Resume Tools** — Resume upload and parsing (PDF) with AI-generated analysis and tailored interview questions.
- **Authentication** — Email/password login plus Google OAuth, backed by stateless JWT sessions.
- **Dashboard & Analytics** — Per-user progress tracking, interview history, and streaks.
<img width="2778" height="1415" alt="image" src="https://github.com/user-attachments/assets/689c10d8-f648-4cab-a952-8c7f804fb96b" />

## Tech Stack

**Frontend:** React 19, TypeScript, Vite, Tailwind CSS, Zustand, React Router, Monaco Editor, Recharts, Framer Motion

**Backend:** Node.js, Express, TypeScript, MongoDB (Mongoose)

**AI / Auth:** Groq (LLaMA-family models) for the interview engine and scoring, Google OAuth for sign-in

## Project Structure

```
PrepAI/
├── client/          # React + Vite frontend
│   └── src/
├── server/          # Express + TypeScript backend
│   └── src/
│       ├── models/      # Mongoose schemas (User, Interview, Problem, Submission, Contest)
│       ├── routes/      # API routes (auth, user, interview, problems, resume, contests)
│       ├── services/    # AI (Groq) and code execution services
│       └── middleware/  # Auth middleware
└── package.json     # Root scripts to run client + server together
```

## Prerequisites

- Node.js (v18+ recommended)
- MongoDB instance (local or hosted, e.g. MongoDB Atlas)
- A [Groq API key](https://console.groq.com/)
- A Google OAuth Client ID ([Google Cloud Console](https://console.cloud.google.com/))

## Getting Started

1. **Clone the repository and install dependencies**

   ```bash
   git clone <repo-url>
   cd PrepAI
   npm run install:all
   ```

2. **Configure environment variables**

   Create a `.env` file inside `server/`:

   ```env
   PORT=3001
   MONGODB_URI=mongodb://127.0.0.1:27017/prepai
   CLIENT_URL=http://localhost:5173
   JWT_SECRET=your_jwt_secret
   GOOGLE_CLIENT_ID=your_google_oauth_client_id
   GROQ_API_KEY=your_groq_api_key
   GROQ_MODEL=your_preferred_groq_model   # optional
   ```

   Create a `.env` file inside `client/`:

   ```env
   VITE_API_URL=http://localhost:3001
   VITE_GOOGLE_CLIENT_ID=your_google_oauth_client_id
   ```

3. **Run the app in development**

   From the project root, this starts both the client and server concurrently:

   ```bash
   npm run dev
   ```

   - Client: http://localhost:5173
   - Server: http://localhost:3001

4. **(Optional) Seed the problems database**

   ```bash
   cd server
   npm run seed:problems
   ```

## Building for Production

```bash
# Server
cd server
npm run build
npm start

# Client
cd client
npm run build
```

## Author

**Rigzin Wangmo**
