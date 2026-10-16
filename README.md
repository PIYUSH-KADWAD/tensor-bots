# Tensor Bots — AI Multi-Agent Studio

Tensor Bots is an autonomous multi-agent engineering team (Manager, Researcher, Planner, Developer, Reviewer) built with **LangGraph** (Python 3.12) and a modern **React / Vite** frontend. It demonstrates state graphs, parallel fan-out/fan-in, real-time event streaming via Server-Sent Events (SSE), sandboxed file creation tools, and iterative review cycles.

---

## Architecture & Agent Flow

- **Project Manager:** Parses user input, determines project scope, and triggers downstream agents.
- **Researcher & Planner:** Analyzes architecture constraints and formulates UI/UX blueprints in parallel.
- **Developer:** Implements application logic across `index.html`, `styles.css`, and `app.js` inside sandboxed workspaces.
- **Reviewer (QA):** Inspects generated code, checks acceptance criteria, and triggers revision loops if fixes are needed.

---

## Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/PIYUSH-KADWAD/tensor-bots.git
cd tensor-bots
```

### 2. Backend Setup

**Windows (PowerShell):**
```powershell
cd backend
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

**macOS / Linux:**
```bash
cd backend
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 3. Environment Configuration
Create your local environment file:
```bash
cp .env.example .env
```

Open `backend/.env` and configure your settings:
```env
# Set to 1 for offline mock mode, or 0 to use live Groq models
MOCK_LLM=0

# Groq API Configuration
GROQ_API_KEY=your_actual_groq_api_key_here
GROQ_MODEL=llama-3.3-70b-versatile
LLM_PROVIDER=groq

# Graph iteration limit
MAX_REVIEW_ROUNDS=2
```

Start the FastAPI backend server:
```powershell
uvicorn app.main:app --reload --port 8000
```

### 4. Frontend Setup
In a new terminal window:
```powershell
cd frontend
npm install
npm run dev
```

Open `http://localhost:5173` in your browser.
