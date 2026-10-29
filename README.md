<div align="center">

# Hi, I'm Lakshay 👋

### Backend developer who ships, tests, and deploys real systems

**Python · FastAPI · PostgreSQL · Redis · Celery · Docker**

I build backends the way production demands: authenticated, tested, observable, and live on the internet. I also read my own code like an attacker, looking for the bug before someone else finds it.

<br>

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

</div>

---

## 🚀 What I've Built

Four backend projects, built end to end and tested.

<table>
<tr>
<td width="50%" valign="top">

### 🔗 [Integration Hub](https://github.com/lakshay-gahlawat/integration-hub)
**Full-stack API integration platform**

Connects GitHub and Slack through OAuth 2.0, receives their webhooks, and syncs data in the background.

- Rotating, revocable refresh tokens
- HMAC webhook verification that fails closed
- Idempotency enforced by a database constraint
- OAuth credentials encrypted at rest (Fernet/AES)
- 50+ tests, including a simulated concurrent webhook race

`FastAPI` `React` `TypeScript` `PostgreSQL` `Celery` `Redis`

[🚀 Live App](https://integration-hub-frontend-g4qf.onrender.com) · [⚙️ API Docs](https://integration-hub-69da.onrender.com/docs)

</td>
<td width="50%" valign="top">

### 📋 [Application Tracker API](https://github.com/lakshay-gahlawat/application-tracker-api)
**Job application tracker with analytics**

A production-style REST API with an enforced status workflow, reminders, and a cached analytics dashboard.

- JWT auth, admin role, and audit logs
- Redis caching and login rate limiting
- Celery reminders plus an APScheduler scheduler
- Request correlation IDs and structured logging
- Alembic migrations, CI with tests, Ruff, and Docker build

`FastAPI` `PostgreSQL` `Redis` `Celery` `GitHub Actions`

[⚙️ Live API Docs](https://application-tracker-api-3c8q.onrender.com/docs)

</td>
</tr>
<tr>
<td width="50%" valign="top">

### ⌛ [FastAPI Async AI Worker](https://github.com/lakshay-gahlawat/fastapi-ai-worker-backend)
**Async LLM pipeline**

The API accepts a job and returns `202` immediately. An ARQ worker calls the LLM and the client polls for a structured result.

- Non-blocking: slow LLM calls never hold a request
- Retries with exponential backoff, and quota errors are not retried
- Pydantic-validated JSON output (summary, action items, topics)
- Custom Redis-backed rate-limit middleware
- Graceful degradation: a clean `503` when Redis is down

`FastAPI` `ARQ` `Redis` `Groq/OpenAI` `Docker`

[🚀 Live Demo](https://fastapi-ai-worker-9tx1.onrender.com) · [⚙️ API Docs](https://fastapi-ai-worker-9tx1.onrender.com/docs)

</td>
<td width="50%" valign="top">

### 📎 [ClientFlow]([https://github.com/lakshay-gahlawat/fastapi-ai-worker-backend](https://github.com/lakshay-gahlawat/clientflow))
**B2B lead and client management SaaS**

A portfolio and case-study project built to show a complete, tested, production-shaped web application, from backend to frontend to billing.

- FastAPI backend with PostgreSQL
- React frontend
- Async background processing
- Stripe billing
- Fully tested, production-shaped architecture

`FastAPI` `PostgreSQL` `React` `Stripe`

[🚀 Live Demo]([https://fastapi-ai-worker-9tx1.onrender.com](https://clientflow-plum.vercel.app/login)) · [⚙️ API Docs]([https://fastapi-ai-worker-9tx1.onrender.com/docs](https://clientflow-xtst.onrender.com/docs))

</td>
</tr>
</table>

> ⏱️ Demos run on free-tier hosting, so the first request after a quiet period can take up to a minute while the service wakes up.

---

## 🐞 Bug Hunting Mindset

Most bugs aren't syntax errors. They're the case nobody tested: two requests at the same instant, a forged signature, one user reaching into another user's data. I design and test for those cases up front.

| Bug class | What I did about it | Where |
|---|---|---|
| **Race conditions** | Idempotency is enforced by a **database unique constraint**, and a test simulates real concurrent duplicate deliveries | Integration Hub |
| **Forged requests** | Webhook signatures are verified per provider and **fail closed** if no secret is configured | Integration Hub |
| **CSRF in OAuth** | State tokens are stored server-side in Redis and are single-use | Integration Hub |
| **Broken access control** | Every resource is scoped to its owner, with cross-user authorization tests | Integration Hub, Application Tracker |
| **Credential leaks** | Tokens are encrypted at rest and never returned in any API response | Integration Hub |
| **Token replay** | Refresh tokens rotate on every use and can be revoked | Integration Hub |
| **Brute force** | Login endpoints are rate limited | Application Tracker |
| **Silent failures** | Correlation IDs, structured logs, and a global exception handler | Application Tracker |
| **Invalid state** | Status transitions are enforced as a state machine, so you can't jump from `rejected` to `offer` | Application Tracker |
| **Dependency outages** | Redis down returns a clean `503` or fails open on purpose, never a crash | AI Worker |

**I also write down what's still wrong.** Integration Hub's README has a *Known Limitations* section, for example refresh-token reuse detection that doesn't yet revoke the whole token family. Knowing where your own system is weak is the first step to fixing it.

---

## 🧰 Tech Stack

| | |
|---|---|
| **Languages** | Python, TypeScript |
| **Backend** | FastAPI, SQLAlchemy 2.0, Pydantic, Alembic |
| **Data** | PostgreSQL, Redis |
| **Async & Queues** | Celery, ARQ, APScheduler |
| **Security** | JWT, OAuth 2.0, bcrypt, Fernet encryption, HMAC signatures, rate limiting |
| **Testing & Quality** | Pytest, respx, Ruff, GitHub Actions CI |
| **Infra** | Docker, Docker Compose, Render |
| **Frontend** | React, Tailwind CSS, Vite |
| **Payments** | Stripe |

---

## 📈 Currently Leveling Up

- Deployment and DevOps: moving from single-container deploys to split services
- Token-family revocation and deeper auth hardening
- Server-Sent Events and WebSockets to replace polling

---

## 📊 GitHub Stats

<div align="center">

[![Followers](https://img.shields.io/github/followers/lakshay-gahlawat?style=for-the-badge&logo=github&logoColor=white&label=Followers&color=181717)](https://github.com/lakshay-gahlawat?tab=followers)
[![Repositories](https://img.shields.io/badge/Repositories-View%20All-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/lakshay-gahlawat?tab=repositories)
[![Profile Views](https://komarev.com/ghpvc/?username=lakshay-gahlawat&label=Profile%20Views&style=for-the-badge&color=009688)](https://github.com/lakshay-gahlawat)

</div>

---

## 📫 Let's Connect

I'm open to backend developer roles, internships, and freelance work.

<div align="center">

[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:lakshaygahlawat65@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/lakshay-gahlawat/)
[![Portfolio](https://img.shields.io/badge/Portfolio-009688?style=for-the-badge&logo=vercel&logoColor=white)](https://lakshay-developer-portfolio.vercel.app/)

*If something in my repos is broken, open an issue. I like finding bugs, including my own.* 🐞

</div>
