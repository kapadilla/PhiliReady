# PhiliReady

PhiliReady is a disaster response decision-support system built for the Philippines. It provides interactive hazard maps, real-time demand forecasting, and "What-If" simulation capabilities to help Local Government Units (LGUs) and response teams quantify and prepare for the relief demands of displaced populations.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Resources](#resources)
- [Tech Stack](#tech-stack)
- [Setup Instructions](#setup-instructions)
  - [Backend](#backend-setup)
  - [Frontend](#frontend-setup)
- [AI Disclosure](#ai-disclosure)

---

## Project Overview

PhiliReady translates international SPHERE humanitarian standards and PSA 2024 Census data into concrete, quantified relief demands (e.g., kilograms of rice, liters of water per city) — scaled by poverty incidence, hazard type, and displacement rates. It supports two user roles: **Admins** with full system access, and **LGU accounts** scoped to their assigned jurisdictions.

Key features include:
- Interactive choropleth demand heatmaps by municipality
- 7-day hazard-specific demand forecasting (typhoon and earthquake models)
- "What-If" simulator for overriding city parameters (population, poverty rate, coastal status)
- Real-time weather data integration via Open-Meteo
- Role-based access control with JWT authentication
- Admin panels for commodity pricing and user-jurisdiction assignment

---

## Resources

- Frontend Repository: https://github.com/jrmellpaz/PhiliReady.git
- Backend Repository: https://github.com/jrmellpaz/PhiliReady-API.git
- Video Demo: https://drive.google.com/drive/folders/1CloO4Y2NhK2YPoSXIm1cEpJ1nUxxNyWQ?usp=sharing

---

## Tech Stack

### Backend
| Layer | Technology |
|---|---|
| Framework | FastAPI (Python 3.11) |
| Database | PostgreSQL + SQLAlchemy 2.0 ORM |
| Data Processing | Pandas, NumPy |
| Authentication | JWT via `python-jose` + `passlib/bcrypt` |
| Weather Integration | Open-Meteo API via `httpx` |


### Frontend
| Layer | Technology |
|---|---|
| Framework | TanStack Start (React 19 + Vite) |
| Language | TypeScript |
| Routing | TanStack Router |
| Data Fetching | TanStack Query (React Query) |
| Styling | Tailwind CSS v4, Radix UI, `@silk-hq/components` |
| Maps | React Leaflet |
| Charts | Recharts |
| Forms & Validation | TanStack Form + Zod |

---

## Setup Instructions

### Backend Setup
Access the backend repository here: https://github.com/jrmellpaz/PhiliReady-API.git

#### Prerequisites
- Python 3.11+
- PostgreSQL (running locally or via a cloud provider)

#### Steps

1. **Clone the repository and navigate to the backend directory:**
   ```bash
   git clone <repository-url>
   cd philiready/backend
   ```

2. **Create and activate a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables:**

   Create a `.env` file in the backend root with the following:
   ```env
   DATABASE_URL=postgresql://<user>:<password>@<host>:<port>/<dbname>
   SECRET_KEY=<your-jwt-secret-key>
   ALGORITHM=HS256
   ACCESS_TOKEN_EXPIRE_MINUTES=60
   ```

5. **Seed the database:**
   ```bash
   python app/db/seed_data.py
   ```
   This populates the database with PSGC administrative boundaries, PSA 2024 demographic baselines, and default admin states.

6. **Run the development server:**
   ```bash
   uvicorn app.main:app --reload
   ```
   The API will be available at `http://localhost:8000`. Interactive API docs are at `http://localhost:8000/docs`.

---

### Frontend Setup
Access the frontend repository here: https://github.com/jrmellpaz/PhiliReady.git

#### Prerequisites
- Node.js 18+
- npm or pnpm

#### Steps

1. **Navigate to the frontend directory:**
   ```bash
   cd philiready/frontend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Configure environment variables:**

   Create a `.env` file in the frontend root:
   ```env
   VITE_API_BASE_URL=http://localhost:8000
   ```
   Update this to your deployed backend URL for production builds.

4. **Run the development server:**
   ```bash
   npm run dev
   ```
   The app will be available at `http://localhost:5173`.

5. **Build for production:**
   ```bash
   npm run build
   ```

---

## AI Disclosure

In accordance with hackathon requirements, the following AI tools were used during the development of PhiliReady:

| Tool | Usage |
|---|---|
| **Google Gemini 3.1 Pro** | Planning & brainstorming, writing and drafting code, debugging |
| **Anthropic Claude Opus 4.6** | Planning & brainstorming, writing and drafting code, debugging |
| **Groq Llama 3.1 8B Instant** | Webapp AI Integration for Assessment and Chatbot |

AI assistance was applied broadly across the project lifecycle — from early ideation and architecture planning to active implementation, troubleshooting, and writing the report. All AI-generated outputs were reviewed, validated, and integrated by team members, who retained full responsibility for the final design decisions, logic, and correctness of the system.
