# Personal Finance Advisor Bot

An AI-powered personal finance management and advisory platform built to help individuals track income, log daily expenses, establish category budgets, plan savings milestones, and receive tailored financial insights powered by Google Gemini.

---

## Key Features

- **Dashboard & Cash Flow Overview**: Real-time breakdown of total monthly income, expenses, net savings, budget utilization, and recent transaction history.
- **Income & Expense Tracking**: Categorized ledger entries with custom dates, notes, and sources.
- **Dynamic Budgeting**: Set overall monthly spending caps and category-level limits with real-time overspending alerts.
- **Savings Goals & Milestones**: Track targets, set target deadlines, monitor progress percentages, and log incremental contributions.
- **AI Financial Health Audit**: In-depth financial health scoring (0–100, letter grades A–F), category overspending analysis, and customized 4-step action plans generated via Google Gemini.
- **Interactive Advisor Chat**: Chat interface with contextual awareness of the user's financial profile for personalized financial education and budgeting tips.
- **Monthly Financial Statements**: Generate and print clean, professional month-by-month summaries.
- **Multi-Currency Support**: Support for INR (₹), USD ($), EUR (€), GBP (£), JPY (¥), CAD (C$), AUD (A$), and KRW (₩).
- **Academic & College Project Ready**: Built-in architecture diagrams, viva exam Q&A guide, and exportable Python Flask backend reference files.

---

## Tech Stack

| Layer | Technology |
| :--- | :--- |
| **Frontend** | React 19, TypeScript, Tailwind CSS, Lucide Icons, Motion |
| **Backend** | Node.js, Express 4, TypeScript (`tsx` / `esbuild`) |
| **AI Integration** | Google Gemini API (`@google/genai`) using `gemini-2.5-flash` |
| **Styling** | Tailwind CSS with responsive light theme |
| **Build Tooling** | Vite 8, esbuild |

---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (version 18 or higher)
- `npm` (version 9 or higher)

### 1. Installation

Clone the repository or navigate to the project directory:

```bash
npm install
```

### 2. Environment Configuration

Copy the example environment file:

```bash
cp .env.example .env
```

Add your Gemini API Key in `.env`:

```env
GEMINI_API_KEY="your-gemini-api-key-here"
```

> **Note**: The application includes an intelligent rule-based fallback advisor. Even without a `GEMINI_API_KEY`, all budgeting, tracking, and advice features operate smoothly.

### 3. Running in Development Mode

Start the integrated full-stack server (Express + Vite) on port 3000:

```bash
npm run dev
```

Visit [http://localhost:3000](http://localhost:3000) in your browser.

### 4. Production Build & Execution

Compile both the client-side single-page app and the bundled server:

```bash
npm run build
npm start
```

---

## REST API Overview

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/api/auth/register` | Create a new user account |
| `POST` | `/api/auth/login` | Authenticate and obtain session token |
| `GET` | `/api/auth/me` | Fetch authenticated user profile |
| `GET` | `/api/overview` | Fetch summary statistics and monthly metrics |
| `GET` / `POST` | `/api/income` | List or record income items |
| `DELETE` | `/api/income/:id` | Remove an income entry |
| `GET` / `POST` | `/api/expenses` | List or record expense items |
| `DELETE` | `/api/expenses/:id` | Remove an expense entry |
| `GET` / `POST` | `/api/budgets` | Retrieve or set monthly budget limits |
| `GET` / `POST` | `/api/savings` | List or create savings targets |
| `PUT` | `/api/savings/:id` | Update goal progress or deposit contribution |
| `POST` | `/api/ai/analyze` | Request a Gemini financial health assessment |
| `GET` / `POST` | `/api/ai/chat` | Retrieve history or send prompt to AI Advisor |
| `GET` / `POST` | `/api/reports` | Retrieve or generate a monthly statement |

---

## Project Structure

```
├── index.html                  # HTML entry point with metadata and SEO
├── metadata.json               # AI Studio project capability manifest
├── package.json                # Dependencies and build scripts
├── server.ts                   # Express server and API route handlers
├── server/
│   ├── db.ts                   # User data ledger, sessions, and sample data
│   ├── gemini.ts               # Gemini 2.5 Flash client & fallback logic
│   └── pythonProjectFiles.ts   # Python Flask reference source files
├── src/
│   ├── main.tsx                # Client application root mount
│   ├── App.tsx                 # Core application shell and state provider
│   ├── api.ts                  # Client HTTP service layer
│   ├── types.ts                # TypeScript data interfaces
│   ├── index.css               # Global Tailwind styles
│   └── components/
│       ├── Navbar.tsx          # Navigation header and active tab switcher
│       ├── DashboardView.tsx   # Visual KPI cards and analytics summary
│       ├── IncomeView.tsx      # Income ledger and entry modal
│       ├── ExpenseView.tsx     # Expense tracker with categories
│       ├── BudgetView.tsx      # Budget setting and threshold monitoring
│       ├── SavingsView.tsx     # Milestone targets and contribution drawer
│       ├── AdvisorView.tsx     # AI Audit scorecard and conversational chat
│       ├── ReportsView.tsx     # Statement generation and printable reports
│       ├── ProfileView.tsx     # Currency preferences and user settings
│       ├── AuthModal.tsx       # Sign-in and demo user authentication
│       └── ProjectDocsModal.tsx# Academic Viva Q&A, system design, and Python code
├── tsconfig.json               # TypeScript compiler options
└── vite.config.ts              # Vite & Tailwind configuration
```

---

## Academic Viva & Defense Highlights

- **Rule-Based vs. Generative AI**: Combines mathematical budget checks (calculating variances and overspending percentages) with LLM natural language reasoning for behavioral coaching.
- **Security & Privacy**: Client never receives direct Gemini API credentials; all LLM invocations and authentication validations occur securely server-side.
- **Graceful Degradation**: If network interruptions occur or API quotas are exhausted, the platform automatically falls back to an internal rule-based heuristic engine without throwing runtime errors.
