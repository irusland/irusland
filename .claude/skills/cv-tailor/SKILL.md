---
name: cv
description: Tailors CV content from CV/base.md for a specific job vacancy. Use when the user wants to adapt their resume, generate targeted CV bullets, or customize their CV text for a job posting. Trigger phrases: "адаптируй резюме", "под вакансию", "tailored CV", "cv for job", "резюме под", "подготовь резюме".
argument-hint: <job vacancy description or URL>
allowed-tools: [Read, WebFetch]
---

# CV Tailor — Adapt resume for a specific job vacancy

The user wants to generate tailored content for their one-page CV.

## Input

Job vacancy description or URL: $ARGUMENTS

## Instructions

1. Read the full `CV/base.md` from the repository using the Read tool.
2. Parse the input:
   - If `$ARGUMENTS` starts with `http://` or `https://` — fetch the page with WebFetch and extract the job description text from it.
   - Otherwise — use `$ARGUMENTS` directly as the job description.
3. Carefully analyze the job vacancy text.
4. Identify:
   - Key requirements and tech stack from the vacancy
   - Role level (IC / TL / Staff / Principal / Manager)
   - Domain (AI/ML, Backend, Platform, Infrastructure, etc.)
   - Company size / product type (startup, scale-up, enterprise)
4. From `CV/base.md`, select only the most relevant achievements and metrics — those that best match the vacancy requirements.
5. Generate content for each section of the CV below.

---

## CV Structure to Fill

### HEADER TAGLINE
One line under the name. Format: `<Role Title> | <Domain 1> & <Domain 2> | <Value Prop>`
Example: `Tech Lead | AI/ML Platforms & Agentic Systems | Architecture, Strategy & Delivery`
Adapt the title and domains to match the vacancy language.

---

### CORE IMPACT
4 bullets. Short, metric-driven, no fluff. Each bullet = one bold result.
Format: `- <action verb> <what> <bold metric>`
Example:
- Built and scaled AI agent platform used by **400+ users** with **~80% satisfaction**
- Improved SQL generation accuracy **from 63% to 100%**

Select the 4 most impressive and relevant metrics from base.md for this vacancy.

---

### EXPERIENCE

#### Role 1: Tech Lead @ Aviasales (2024—Present)
One-line role summary (what you drove, the outcome).

Then **3–5 subsections**, each with 2–4 bullets. Choose subsections relevant to the vacancy:

Available subsections (pick most relevant):
- **Platform & Architecture** — scalable AI agent platform, MCP-based architecture, reusable foundations
- **Product Impact** — SQL 63→100%, 408 users / 83 MAU / ~80% satisfaction, anomaly detection 164 metrics / 11 teams, time-to-market 2x
- **Leadership & Execution** — cross-functional coordination, RFCs/ADRs, technical debt management
- **Platform Enablement & Operations** — monitoring, alerting, support processes, CI/CD improvements
- **Culture & Influence** — internal talks, knowledge sharing, AI/ML adoption

Total bullets for this role: **10–14** (scale down if IC role, keep if leadership/platform role).

#### Role 2: Senior SDE @ Tinkoff AI Center (2021—2024)
One-line role summary.

**4–8 bullets** depending on vacancy relevance. Draw from these areas in base.md:
- Conversational AI systems, high-load backend, fault tolerance
- TorchServe ML inference optimization (2x capacity, same hardware)
- Timeout reduction 3% → 0.05%
- SQL Agent (63%→100%), Salokot knowledge assistant (378 users), Anomaly Detection platform (164 metrics, 4 teams), Scena orchestration framework
- A/B testing, CI/CD, test coverage 0%→77%, development speed +28%
- Mentoring 2 engineers to mid-level

If vacancy is IC/technical → include more project-level bullets (SQL Agent, Salokot, inference).
If vacancy is leadership → emphasize delivery ownership and cross-functional work.

---

### EDUCATION
Keep as-is (do not modify):
- Masters, Moscow Institute of Physics and Technology — (Honors Diploma) GPA: 9.6/10 — MSc in Applied Mathematics and Computer Science
- Bachelors, Ural Federal University — GPA: 4.3/5 — BSc in Fundamental Informatics and Information Technologies

---

### CORE EXPERTISE
4 rows, two-column table. Left = category, Right = specific technologies/skills.
Select and reorder based on vacancy priority. Available categories and content from base.md:

- ML Platforms & Agentic Systems → LLM Agents, RAG, MCP, Production AI Systems, LangGraph, MLflow
- Backend & Distributed Systems → High-load services, event-driven architecture, gRPC, Kafka, FastAPI, Python
- Cloud & Infrastructure → Kubernetes, AWS/GCP, CI/CD, Docker, Observability (Prometheus/Grafana)
- Leadership & System Ownership → Architecture, strategy, delivery, cross-functional leadership
- Data & Analytics → Postgres, Redis, Elasticsearch, PySpark, dbt, Airflow
- ML Inference & Serving → TorchServe, PyTorch, Triton, KServe, A/B testing

Pick the 4 most relevant categories and trim keywords to match vacancy language.

---

## Output Rules

- Do not invent facts — use only what exists in base.md
- Use bold for key metrics and technology names within bullets
- Write in English
- Keep total CV content to one page (be concise, cut weak bullets)
- Prioritize quantified achievements over generic descriptions
- Match vocabulary to the vacancy (mirror their terms where natural)
