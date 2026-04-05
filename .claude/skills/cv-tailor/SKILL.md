---
name: cv
description: Tailors CV content from CV/base.md for a specific job vacancy. Use when the user wants to adapt their resume, generate targeted CV bullets, or customize their CV text for a job posting. Trigger phrases: "адаптируй резюме", "под вакансию", "tailored CV", "cv for job", "резюме под", "подготовь резюме".
argument-hint: <job vacancy description or URL>
allowed-tools: [Read, WebFetch, Write]
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
4 bullets. Each bullet must be **13–15 words** (count strictly). FAANG-level density — no fluff, no filler.
Structure: `[Action Verb] + [What you did] + [How] + [Impact/result]`
Example:
- Improved SQL agent accuracy from 63% to 100% via custom **MCP** server redesign
- Scaled internal AI assistant to **378 users**, **83 MAU**, and **~80% satisfaction** post-launch

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

### KEYWORDS
One paragraph of ATS-friendly comma-separated keywords. Pull from:
- Exact terms used in the vacancy (mirror their language)
- Relevant tech stack from base.md that matches the role domain
- Key patterns and methodologies (e.g. Infrastructure-as-Code, Event-Driven Architecture, Fault Tolerance)

Do not repeat keywords already prominent in CORE EXPERTISE — add complementary terms that cover the full vocabulary of the vacancy.

---

## Bullet Writing Rules (apply to ALL bullets: CORE IMPACT + EXPERIENCE)

Every bullet must meet ALL of the following:

1. **Word count**: 13–15 words exactly (count every word including articles and prepositions)
2. **Structure**: `[Action Verb] + [What] + [How] + [Impact/metric]`
3. **First word**: strong action verb — Led, Built, Designed, Improved, Reduced, Scaled, Drove, Architected, Launched, Delivered, Migrated, Optimized, Increased, Resolved, Established
4. **Measurable impact**: include %, scale, users, latency, cost, time, or count wherever possible
5. **No filler**: remove "in order to", "successfully", "responsible for", "helped", "worked on"
6. **No verb repetition**: vary the opening verb across bullets within the same role section
7. **Single line**: no sub-clauses that wrap into a second sentence

**Count check**: before finalizing each bullet, count its words. If outside 13–15, rewrite until it fits.

---

## Output Rules

- Do not invent facts — use only what exists in base.md
- Use bold for key metrics and technology names within bullets
- Write in English
- Keep total CV content to one page (be concise, cut weak bullets)
- Prioritize quantified achievements over generic descriptions
- Match vocabulary to the vacancy (mirror their terms where natural)

---

## RTF File Generation

After generating all CV content, write it to `CV/generated/[company]/[job-summary]-[current-date].rtf` using the Write tool.

Use this RTF template (fill in the generated content):

```
{\rtf1\ansi\ansicpg1252\cocoartf2822
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Arial-BoldMT;\f1\fswiss\fcharset0 ArialMT;}
{\colortbl;\red255\green255\blue255;\red80\green80\blue80;}
{\*\expandedcolortbl;;\csgenericrgb\c31373\c31373\c31373;}
\margl1440\margr1440\margb1080\margt1080\vieww22440\viewh18500\viewkind0
\pard\tx560\tx1120\tx1680\tx2240\tx2800\tx3360\tx3920\tx4480\tx5040\tx5600\tx6160\tx6720\pardirnatural\partightenfactor0

\f0\b\fs44 \cf0 Ruslan Sirazhetdinov
\f1\b0\fs36 \
\cf2 <HEADER TAGLINE>\cf0 \

\fs32 irusland@icloud.com | linkedin.com/in/irusland | github.com/irusland
\fs36 \
\

\f0\b CORE IMPACT
\f1\b0 \
\
-  <bullet: use \f0\b bold metric \f1\b0 inline for emphasis>\
-  <bullet>\
-  <bullet>\
-  <bullet>\
\

\f0\b EXPERIENCE
\f1\b0 \
\

\f0\b Tech Lead @ Aviasales
\f1\b0   |  2024\'96Present\
<ROLE 1 SUMMARY — one line>\
\

\f0\b <Subsection 1 Name>
\f1\b0 \
-  <bullet with \f0\b bold metrics \f1\b0 inline>\
-  <bullet>\
\

\f0\b <Subsection 2 Name>
\f1\b0 \
-  <bullet>\
-  <bullet>\
\

\f0\b Senior SDE @ Tinkoff AI Center
\f1\b0   |  2021\'962024\
<ROLE 2 SUMMARY — one line>\
\
-  <bullet with \f0\b bold metrics \f1\b0 inline>\
-  <bullet>\
-  <bullet>\
-  <bullet>\
-  <bullet>\
-  <bullet>\
-  <bullet>\
-  <bullet>\
\

\f0\b EDUCATION
\f1\b0 \
\

\f0\b Masters
\f1\b0   \'96 Moscow Institute of Physics and Technology (Honors Diploma) | GPA: 9.6/10 | MSc Applied Mathematics & CS\

\f0\b Bachelors
\f1\b0   \'96 Ural Federal University | GPA: 4.3/5 | BSc Fundamental Informatics & IT\
\

\f0\b CORE EXPERTISE
\f1\b0 \
\

\f0\b <Category 1>
\f1\b0 :  <skill>, <skill>, <skill>\

\f0\b <Category 2>
\f1\b0 :  <skill>, <skill>, <skill>\

\f0\b <Category 3>
\f1\b0 :  <skill>, <skill>, <skill>\

\f0\b <Category 4>
\f1\b0 :  <skill>, <skill>, <skill>\
\

\f0\b KEYWORDS
\f1\b0 \
\
<keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>, <keyword>\
}
```

RTF formatting rules:
- **Bold**: switch fonts — `\f0\b bold text \f1\b0` (not `{\b...\b0}`)
- **Line break**: `\` at end of line (not `\par`)
- **Blank line**: two consecutive `\` lines
- **En dash**: `\'96`
- **Gray color** for tagline only: `\cf2 ... \cf0`
- **Font sizes**: `\fs44` = name (22pt), `\fs36` = body/tagline (18pt), `\fs32` = contact (16pt)
- **Inline bold within bullet**: `-  text \f0\b metric \f1\b0 more text\`
- **Subsection headers**: `\f0\b Header Name\` then `\f1\b0 \`
- Replace `<...>` placeholders with actual generated content
- Save the file as `CV/generated/[company]/[job-summary]-[current-date].rtf`
