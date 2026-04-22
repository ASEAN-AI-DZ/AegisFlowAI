# PLAN â€” Phase 1: Core Backend + Dashboard

> ðŸ¤– **Applying knowledge of `@project-planner`**

## Overview

Triá»ƒn khai Phase 1 AegisFlow AI â€” xÃ¢y dá»±ng ná»n táº£ng Backend API + Dashboard cho **City Admin** vÃ  **Disaster Operator**. ÄÃ¢y lÃ  phase Ä‘áº§u tiÃªn trong lá»™ trÃ¬nh reactive â†’ proactive.

## Actors (Phase 1)

| Actor | Vai trÃ² | TÆ°Æ¡ng tÃ¡c |
|-------|---------|-----------|
| **City Admin** | Quáº£n trá»‹ há»‡ thá»‘ng, cáº¥u hÃ¬nh | Dashboard admin |
| **Disaster Operator** | GiÃ¡m sÃ¡t map, xá»­ lÃ½ sá»± cá»‘ | Dashboard map + incident panel |

## Tech Stack (Phase 1)

| Layer | CÃ´ng nghá»‡ |
|-------|-----------|
| Backend | Laravel 11+ (PHP 8.3) |
| Frontend | Next.js 15 + Mapbox GL JS |
| AI Service | Python FastAPI (stub) |
| Database | PostgreSQL 16 + PostGIS |
| Cache/Queue | Redis |
| WebSocket | Soketi |
| Container | Docker Compose |

---

## Task Breakdown

### âš™ï¸ P0 â€” Háº¡ táº§ng (KhÃ´ng cÃ³ dependencies)

#### Task 0.1: Init Laravel Backend
- **Agent:** `backend-specialist`
- **Skills:** `api-patterns`
- **Priority:** P0
- **Dependencies:** â€”
- **INPUT:** composer, PHP 8.3
- **OUTPUT:** `backend/` â€” Laravel 11 project structure, `.env` config
- **VERIFY:** `php artisan serve` cháº¡y thÃ nh cÃ´ng, tráº£ vá» welcome page

#### Task 0.2: Init Next.js Frontend
- **Agent:** `frontend-specialist`
- **Skills:** `react-best-practices`, `frontend-design`
- **Priority:** P0
- **Dependencies:** â€”
- **INPUT:** Node.js, npx
- **OUTPUT:** `frontend/` â€” Next.js 15 App Router project
- **VERIFY:** `npm run dev` â†’ http://localhost:3000

#### Task 0.3: Init Python AI Service
- **Agent:** `ai-ml-engineer`
- **Skills:** `python-patterns`
- **Priority:** P0
- **Dependencies:** â€”
- **INPUT:** Python 3.11+
- **OUTPUT:** `ai-service/` â€” FastAPI skeleton + `/health` endpoint
- **VERIFY:** `uvicorn app.main:app` â†’ http://localhost:8001/health

#### Task 0.4: Docker Compose hoÃ n chá»‰nh
- **Agent:** `devops-engineer`
- **Skills:** `deployment-procedures`
- **Priority:** P0
- **Dependencies:** Task 0.1, 0.2, 0.3
- **INPUT:** docker-compose.yml hiá»‡n táº¡i
- **OUTPUT:** Dockerfile cho má»—i service, Compose cháº¡y full stack
- **VERIFY:** `docker compose up -d` â†’ táº¥t cáº£ services healthy

---

### ðŸ—„ï¸ P1 â€” Database Schema (Pháº£i cÃ³ trÆ°á»›c API)

#### Task 1.1: CÃ i packages + Viáº¿t migrations
- **Agent:** `database-architect`
- **Skills:** `database-design`
- **Priority:** P1
- **Dependencies:** Task 0.1
- **INPUT:** `docs/database.md` (14 tables, FK dependencies)
- **OUTPUT:** 15 migration files theo thá»© tá»± + PostGIS extension enable
- **VERIFY:** `php artisan migrate` thÃ nh cÃ´ng, kiá»ƒm tra `\dt` trong psql

#### Task 1.2: Seed Roles, Permissions, Sample Data
- **Agent:** `database-architect` + `traffic-engineer`
- **Skills:** `database-design`
- **Priority:** P1
- **Dependencies:** Task 1.1
- **INPUT:** `docs/database.md` Section 3 (Roles/Permissions) + `docs/business-logic.md`
- **OUTPUT:**
  - `RolePermissionSeeder` â€” 6 roles + 31 permissions
  - `GraphSeeder` â€” Máº«u 10 nodes + 15 edges + 3 zones (SÃ i GÃ²n)
  - `UserSeeder` â€” Admin + Operator + Demo users
- **VERIFY:** `php artisan db:seed`, kiá»ƒm tra `roles`, `permissions`, `nodes`, `edges` cÃ³ data

---

### ðŸ”Œ P2 â€” Laravel API Core

#### Task 2.1: Auth API (Sanctum)
- **Agent:** `backend-specialist`
- **Skills:** `api-patterns`
- **Priority:** P2
- **Dependencies:** Task 1.1
- **INPUT:** users table + Sanctum
- **OUTPUT:**
  - `POST /api/auth/login` â†’ token
  - `POST /api/auth/register`
  - `GET /api/auth/me` â†’ user + roles + permissions
  - `POST /api/auth/logout`
- **VERIFY:** Login â†’ nháº­n token â†’ gá»i `/me` â†’ tráº£ user info

#### Task 2.2: Graph API (Nodes + Edges)
- **Agent:** `backend-specialist` + `traffic-engineer`
- **Skills:** `api-patterns`
- **Priority:** P2
- **Dependencies:** Task 1.2
- **INPUT:** nodes, edges tables + PostGIS
- **OUTPUT:**
  - `GET /api/edges/geojson` â†’ GeoJSON cho Mapbox
  - `GET /api/nodes` â†’ Node list + filter by zone
  - `GET /api/edges?flood_severity=heavy` â†’ Filter táº¯c
  - `GET /api/edges/nearby?lat=...&lng=...&radius=2000`
- **VERIFY:** GeoJSON response render Ä‘Æ°á»£c trÃªn Mapbox

#### Task 2.3: Incident CRUD + Auto-detect Logic
- **Agent:** `backend-specialist` + `traffic-engineer`
- **Skills:** `api-patterns`
- **Priority:** P2
- **Dependencies:** Task 2.2
- **INPUT:** `docs/business-logic.md` Luá»“ng 2 (Incident)
- **OUTPUT:**
  - `POST /api/incidents` â€” Táº¡o sá»± cá»‘ (operator/citizen)
  - `GET /api/incidents` â€” List + filter status/severity
  - `PATCH /api/incidents/{id}` â€” Update status
  - Auto-detect service: water_level spike â†’ táº¡o incident tá»± Ä‘á»™ng
  - Event: `IncidentCreated` â†’ dispatch `CallAIPrediction` job
- **VERIFY:** Táº¡o incident â†’ event fired â†’ job dispatched

#### Task 2.4: Prediction + Recommendation API
- **Agent:** `backend-specialist` + `ai-ml-engineer`
- **Skills:** `api-patterns`
- **Priority:** P2
- **Dependencies:** Task 2.3, Task 3.1 (AI stub)
- **INPUT:** `docs/business-logic.md` Luá»“ng 3 + 4
- **OUTPUT:**
  - `CallAIPrediction` job â†’ gá»i Python `/predict`
  - Save predictions + prediction_edges vÃ o DB
  - Auto-generate recommendations
  - `GET /api/predictions?incident_id=...`
  - `GET /api/recommendations`
  - `PATCH /api/recommendations/{id}/approve`
- **VERIFY:** Incident â†’ prediction â†’ recommendation â†’ approve flow hoÃ n chá»‰nh

#### Task 2.5: WebSocket Broadcasting (Soketi)
- **Agent:** `backend-specialist`
- **Skills:** `api-patterns`
- **Priority:** P2
- **Dependencies:** Task 2.2
- **INPUT:** Soketi config
- **OUTPUT:**
  - Broadcasting `EdgeMetricsUpdated` â†’ map realtime
  - Broadcasting `IncidentCreated` â†’ dashboard alert
  - Broadcasting `PredictionReceived` â†’ overlay predictions
- **VERIFY:** Frontend nháº­n WebSocket events khi data thay Ä‘á»•i

---

### ðŸ¤– P3 â€” Python AI Service

#### Task 3.1: FastAPI endpoints (mock)
- **Agent:** `ai-ml-engineer`
- **Skills:** `python-patterns`
- **Priority:** P2 (song song vá»›i P2)
- **Dependencies:** Task 0.3
- **INPUT:** `docs/business-logic.md` Luá»“ng 3 + 5
- **OUTPUT:**
  - `POST /predict` â€” Nháº­n incident data â†’ tráº£ mock predictions
  - `POST /simulate` â€” Nháº­n scenario â†’ tráº£ mock comparison
  - Response format Ä‘Ãºng contract vá»›i Laravel
- **VERIFY:** Laravel gá»i Ä‘Æ°á»£c `/predict`, parse response thÃ nh cÃ´ng

---

### ðŸ–¥ï¸ P3 â€” Next.js Dashboard

#### Task 3.2: Layout + Auth UI
- **Agent:** `frontend-specialist`
- **Skills:** `react-best-practices`, `frontend-design`
- **Priority:** P3
- **Dependencies:** Task 2.1
- **INPUT:** Dashboard design cho Disaster Operator
- **OUTPUT:**
  - Layout: Sidebar (navigation) + Main (content) + Header (user info)
  - Login page â†’ Sanctum token â†’ redirect dashboard
  - Protected routes (middleware auth)
- **VERIFY:** Login â†’ redirect â†’ sidebar navigation hoáº¡t Ä‘á»™ng

#### Task 3.3: Mapbox Traffic Map
- **Agent:** `frontend-specialist`
- **Skills:** `react-best-practices`, `frontend-design`
- **Priority:** P3
- **Dependencies:** Task 2.2, Task 3.2
- **INPUT:** GeoJSON API + Mapbox GL JS
- **OUTPUT:**
  - Map hiá»ƒn thá»‹ edges (flood_severity colors: xanh/vÃ ng/cam/Ä‘á»)
  - Nodes markers (ngÃ£ tÆ°, bÃ¹ng binh)
  - Click edge â†’ popup info (water_level, speed, status)
  - Realtime update tá»« WebSocket
- **VERIFY:** Map render edges vá»›i Ä‘Ãºng mÃ u flood_severity, click popup hoáº¡t Ä‘á»™ng

#### Task 3.4: Incident Panel
- **Agent:** `frontend-specialist`
- **Skills:** `react-best-practices`
- **Priority:** P3
- **Dependencies:** Task 2.3, Task 3.2
- **INPUT:** Incident API
- **OUTPUT:**
  - List incidents (filter status/severity)
  - Create incident form (chá»n vá»‹ trÃ­ trÃªn map)
  - Incident detail â†’ predictions â†’ recommendations
  - Approve/reject recommendation
- **VERIFY:** Táº¡o incident â†’ xem predictions â†’ approve recommendation

---

### ðŸ”— P4 â€” Integration (Full Flow)

#### Task 4.1: End-to-End Incident Flow
- **Agent:** `orchestrator`
- **Skills:** `parallel-agents`
- **Priority:** P4
- **Dependencies:** Táº¤T Cáº¢ tasks trÃªn
- **INPUT:** Full system
- **OUTPUT:** Proactive pipeline hoÃ n chá»‰nh:
  1. Sensor data â†’ edge metrics update
  2. water_level spike â†’ auto-detect incident
  3. Incident â†’ AI predict â†’ recommendations
  4. Operator approve â†’ broadcast alert
- **VERIFY:** Demo full flow tá»« sensor â†’ map update â†’ incident â†’ predict â†’ recommend â†’ approve

---

### âœ… P5 â€” Verification

#### Task 5.1: Testing + Security
- **Agent:** `test-engineer` + `security-auditor`
- **Skills:** `testing-patterns`, `vulnerability-scanner`
- **Priority:** P5
- **Dependencies:** Task 4.1
- **INPUT:** Working code
- **OUTPUT:**
  - Unit tests cho core models (Edge, Incident, Prediction)
  - Feature tests cho API endpoints
  - Security scan (auth, RBAC, SQL injection)
- **VERIFY:** Tests pass, no critical vulnerabilities

---

## Dependencies Graph

```
P0: Init Services (song song)
 â”œâ”€â”€ Task 0.1: Laravel â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
 â”œâ”€â”€ Task 0.2: Next.js          â”‚
 â”œâ”€â”€ Task 0.3: Python           â”‚
 â””â”€â”€ Task 0.4: Docker â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
                                â”‚
P1: Database â—„â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
 â”œâ”€â”€ Task 1.1: Migrations â”€â”€â”€â”€â”€â”€â”
 â””â”€â”€ Task 1.2: Seeders â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
                                â”‚
P2: API + AI (song song) â—„â”€â”€â”€â”€â”€â”€â”˜
 â”œâ”€â”€ Task 2.1: Auth â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
 â”œâ”€â”€ Task 2.2: Graph API â”€â”€â”€â”€â”€â”€â”€â”¤
 â”œâ”€â”€ Task 2.3: Incident API â”€â”€â”€â”€â”¤
 â”œâ”€â”€ Task 2.4: Prediction API â”€â”€â”¤
 â”œâ”€â”€ Task 2.5: WebSocket â”€â”€â”€â”€â”€â”€â”€â”¤
 â””â”€â”€ Task 3.1: AI Mock â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
                                â”‚
P3: Dashboard â—„â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
 â”œâ”€â”€ Task 3.2: Layout + Auth â”€â”€â”€â”
 â”œâ”€â”€ Task 3.3: Mapbox Map â”€â”€â”€â”€â”€â”€â”¤
 â””â”€â”€ Task 3.4: Incident Panel â”€â”€â”¤
                                â”‚
P4: Integration â—„â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
 â””â”€â”€ Task 4.1: E2E Flow â”€â”€â”€â”€â”€â”€â”€â”€â”
                                â”‚
P5: Verify â—„â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
 â””â”€â”€ Task 5.1: Tests + Security
```

---

## Thá»© tá»± Triá»ƒn khai Äá» xuáº¥t

| Äá»£t | Tasks | Thá»i gian Æ°á»›c tÃ­nh |
|------|-------|--------------------|
| **Äá»£t 1** | 0.1 + 0.2 + 0.3 (init song song) | 1 session |
| **Äá»£t 2** | 1.1 + 1.2 (database) | 1 session |
| **Äá»£t 3** | 2.1 + 2.2 + 3.1 (Auth + Graph + AI mock) | 2 sessions |
| **Äá»£t 4** | 2.3 + 2.4 + 2.5 (Incident + Prediction + WS) | 2 sessions |
| **Äá»£t 5** | 3.2 + 3.3 + 3.4 (Dashboard) | 2â€“3 sessions |
| **Äá»£t 6** | 4.1 + 5.1 (Integration + Testing) | 1â€“2 sessions |



