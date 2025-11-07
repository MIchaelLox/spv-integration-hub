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
