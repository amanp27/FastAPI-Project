# FastAPI-Project
A production-ready FastAPI service that serves a machine learning model via REST API.

## ✅ Project Overview

**FastAPI-Project** is a Python-based web service that exposes a trained machine learning model through a clean REST API. It is designed with real-world deployment in mind, featuring:

- ✅ **FastAPI** for high-performance async endpoints
- ✅ **JWT authentication** to protect model access
- ✅ **Redis caching** to accelerate repeated predictions
- ✅ **Prometheus-ready observability** for monitoring
- ✅ **Clean, modular architecture** (API, services, cache, core, etc.)

## 🧠 What It Does

The service provides endpoints to:

- Authenticate users and issue access tokens
- Accept input data and return ML model predictions
- Cache results for faster responses
- Expose metrics for performance tracking

## 📁 Key Files & Architecture

- `app/main.py` — FastAPI app setup + middleware
- `app/api/routes_auth.py` — Auth endpoints (token issuance)
- `app/api/routes_predict.py` — Prediction endpoints
- `app/services/model_service.py` — Model loading + inference logic
- `app/cache/redis_cache.py` — Redis caching layer
- `app/core/security.py` — JWT and security utilities
- `app/models/model.joblib` — Pre-trained model artifact
- `prometheus.yml` — Prometheus scrape config
- `Dockerfile` + `docker-compose.yml` — Containerized deployment

## 🚀 Quick Start (Run Locally)

### 1) Install dependencies
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 2) Run Redis (recommended)
```bash
docker run -d --name redis -p 6379:6379 redis:7
```

### 3) Start the API
```bash
uvicorn app.main:app --reload
```

✅ API available at: `http://localhost:8000`

## 🔐 Authentication

This project uses JWT authentication.

**Endpoint:**
- `POST /auth/token` → get access token (JWT)

**Usage:**
1. Call `/auth/token` with valid credentials
2. Use `Authorization: Bearer <token>` for protected routes

## 🧪 Example Prediction Request

**Endpoint:**
- `POST /predict`

**Sample Body (example structure):**
```json
{
	"feature_1": 4.5,
	"feature_2": 2.3,
	"feature_3": 1.7
}
```

**Sample Response:**
```json
{
	"prediction": 0.86,
	"cached": false
}
```

## 🧩 Architecture Highlights

### ✅ Clean Modular Design
- `app/api/` contains route definitions (thin controllers)
- `app/services/` contains business logic (model + inference)
- `app/cache/` manages caching and improves performance
- `app/core/` handles config, security, and dependencies

### ✅ Caching for Performance
- Repeat prediction requests are served from Redis cache to reduce latency and compute load.

### ✅ Observability Ready
- Prometheus config is included (`prometheus.yml`)
- Metrics can be exposed and scraped for performance dashboards

## 🧪 Testing (Recommended)

> (If tests exist, run `pytest`; otherwise, consider adding unit/integration tests.)

```bash
pytest
```

## 📦 Deployment (Docker)

### Build & Run
```bash
docker-compose up --build
```

🌐 The API will be available at `http://localhost:8000`

## ✅ Why This Project Stands Out

- **Enterprise-ready** pattern with modular separation
- **Performance-minded**: caching + async FastAPI
- **Security-first**: JWT authentication
- **Observability-ready**: Prometheus included
- **Straightforward extension**: add new models, endpoints, or auth providers with minimal effort

## 📌 Next Improvements (Optional Enhancements)

- Add **automated tests** (unit + integration)
- Add **OpenAPI docs enhancements** (schemas, examples)
- Add **CI/CD pipelines** for automated deployment
- Add **role-based access control** for more granular security

---

If you’d like, I can also add a clear “Getting Started” walkthrough for a technical recruiter or prepare a demo script showing the full request/response flow end-to-end.
