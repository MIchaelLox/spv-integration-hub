# 🧠 SPV Integration Hub

## Overview
The **SPV Integration Hub** acts as the central nervous system of the SPV ecosystem.  
It connects the **Cost Simulator** and **MAPAQ Risk Intelligence** models into a unified, intelligent platform.

## Goals
- Route and manage all API traffic between services.
- Enforce authentication and access control.
- Merge outputs (financial + risk) into integrated business reports.
- Support deployment in Docker/Heroku and future cloud environments.

---

## Architecture

spv-integration-hub/
├── api/
│ ├── gateway.py # Main FastAPI router
│ ├── auth.py # JWT-based authentication
│ ├── logging_middleware.py
│ ├── report_generator.py # Merges cost + risk data into reports
│ └── clients/
│ ├── simulator_client.py
│ └── mapaq_client.py
├── db/
│ └── sessions.sqlite
├── tests/
│ ├── test_endpoints.py
│ └── test_report_merge.py
├── Dockerfile
├── requirements.txt
└── README.md


---

## API Endpoints

| Endpoint | Description | Source |
|-----------|--------------|--------|
| `POST /simulate` | Sends data to cost simulator | spv-simulator-advanced |
| `POST /predict` | Gets risk score from MAPAQ model | mapaq-risk-intelligence |
| `GET /report` | Combines cost + risk → JSON/PDF | report_generator |

---

## Authentication
- JWT tokens (`Authorization: Bearer <token>`)  
- `POST /login` returns a signed token valid for 1 h  
- Future: OAuth2 / Single Sign-On for external dashboards  

---

## Reports
- Combine cost simulation and predicted risk metrics.  
- Export to JSON, CSV, and PDF (via `reportlab`).
- Auto-attach timestamp and session ID.

---

## Phase 2 Development Tasks
1. Build REST gateway (FastAPI) with full routing.
2. Add JWT authentication and session validation.
3. Create unified `report_generator` for cost + risk merges.
4. Implement structured logging (JSON logs + rotating files).
5. Add pytest integration tests for API and report endpoints.
6. Build Docker/Heroku deployment configs.
7. Extend to microservice orchestration (Phase 3 preview).

---

## Technologies
Python 3.10+, FastAPI, Uvicorn, Requests, JWT, SQLite, Docker, pytest.
