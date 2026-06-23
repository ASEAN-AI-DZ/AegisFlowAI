# 🌊 AegisFlow AI — GIS & AI Platform for Smart Urban Flood Management

<div align="center">
  <a href="https://aegis-flow-ai.vercel.app/"><img src="https://img.shields.io/badge/🚀_Website-AegisFlow-00C853?style=for-the-badge" alt="Website"/></a>
  <a href="https://asean-ai-dz.github.io/AegisFlowDocument/"><img src="https://img.shields.io/badge/📚_Documentation-AegisFlow-1976D2?style=for-the-badge" alt="Documentation"/></a>
  <a href="#"><img src="https://img.shields.io/badge/🎥_Demo-AegisFlow-EB907C?style=for-the-badge" alt="Demo"/></a>
  <a href="https://canva.link/948o6uh6oyeqwu7"><img src="https://img.shields.io/badge/📖_Slide-AegisFlow-F024EC?style=for-the-badge" alt="Slide"/></a>
  <br/>

  <a href="LICENSE">
    <img src="https://img.shields.io/badge/License-GPL%203.0-blue.svg" alt="License: GPL-3.0"/>
  </a>

  <br/>

  <a href="CONTRIBUTING.md">🤝 Contributing</a> •
  <a href="CHANGELOG.md">📜 Changelog</a>

</div>

![AegisFlow AI Banner](/static/banner.png)

> _"From damage reports to flood forecasts — AI becomes the digital shield that safeguards communities before disaster strikes."_

**AegisFlow AI** is a cutting-edge platform that fuses **Geographic Information Systems (GIS)** with **Artificial Intelligence (AI)** to fundamentally shift urban flood response from a reactive model to a **predictive and proactive** one. By modeling the city's entire road network as a dynamic weighted graph, the system continuously ingests data from water-level sensors, weather services, and crowdsourced citizen reports — enabling rapid evacuation planning, precise relief coordination, and data-driven decisions that save lives.

---

## 📋 The Challenge

### Background

As climate change intensifies and urbanization accelerates across major cities in the region, legacy flood response infrastructure is increasingly overwhelmed by a growing set of critical shortcomings.

**What cities face today:**

- Intense downpours and rising tides trigger recurring urban floods that bring entire road networks to a standstill.
- Key transit corridors get submerged without warning, putting lives at risk and blocking emergency vehicles when every minute counts.
- The vast majority of existing tools are limited to post-event monitoring — they lack the ability to forecast flood severity or guide people to safe routes ahead of time.
- Emergency response remains sluggish, with no systematic way to optimize rescue logistics or equip disaster authorities with real-time decision support.

---

## 🎯 Project Goals

### Short-term Goals

1. **Deploy a live interactive map** that tracks flood conditions across the city in real time.
2. **Implement AI-driven forecasting for:**
   - Identifying flood-prone hotspots using terrain profiles, historical rainfall patterns, and drainage infrastructure data.
   - Assessing environmental hazards by correlating weather feeds with IoT sensor streams.
3. **Enable intelligent routing:** Automatically blacklist submerged road segments and compute the safest alternative paths before citizens set out.
4. **Provide a command-and-control dashboard:** Give authorities a clear, visual interface to allocate rescue teams and relief supplies efficiently.

### Long-term Goals

- Become a foundational component of Smart City operations centers and national disaster management agencies — the go-to platform during monsoon and storm seasons.
- Broaden the system's reach into adjacent domains: landslide early warning, aging infrastructure risk scoring, and climate-resilient urban planning.

---

## 🌐 Understanding AegisFlow AI

### The Core Idea

Picture a navigation app like **Waze or Google Maps** — except this one is **purpose-built to keep you alive during a flood**. It is a routing intelligence that reacts instantly to rising water.

AegisFlow AI represents every street and intersection as a **graph network** (Nodes = junctions, Edges = road segments). Each Edge carries a dynamic weight that shifts in real time as rainfall data and water-level readings flow in.

The moment a severe storm event begins, the platform doesn't just show you where water has already accumulated — it **runs spatial projections for the next 1–3 hours** to answer urgent questions:

- Which arterial roads will floodwater encroach upon and render impassable?
- What is the fastest unobstructed route for an ambulance or fire engine to reach the nearest hospital?
- Which neighborhoods are at imminent risk of isolation and should receive rescue boats first?
- Where should emergency supply hubs be staged for maximum coverage?

---

## 👥 Who Is This For?

![Target Audience](/static/img/doituong.png)

### 👨‍💼 1. City Planners & Government Decision-Makers

- Evaluate the downstream effects of infrastructure investments before breaking ground.
- Test what-if scenarios with simulation tools to de-risk major decisions.
- Leverage live data dashboards for timely, evidence-based governance.

### 👷 2. Flood Engineers & Urban Infrastructure Experts

- Conduct granular flood-flow analysis and multi-variable risk assessments.
- Model the projected outcomes of drainage upgrades or barrier placements.
- Continuously refine flood mitigation infrastructure with empirical feedback.

### 🏛️ 3. Civil Society & Community Organizations

- Empower residents to submit flood reports and advocate for local improvements.
- Provide transparent, data-backed visualizations of socio-economic and environmental trade-offs.

### 📚 4. Academic Researchers & Students

- Tap into open datasets for urban hydrology and climate adaptation studies.
- Simulate complex flood dynamics within a controlled, reproducible environment.
- Benchmark hypotheses against real-world sensor readings and historical records.

---

## 🚀 Core Capabilities

![Core Capabilities](/static/img/chucnang.png)

### 1. **Live Flood Monitoring Radar**

- Instantly plots flood coordinates onto an interactive base map in real time.
- Continuously refreshed through citizen crowdsourcing and IoT water-level sensor feeds.
- Color-coded flood severity overlays across distinct geographic clusters for at-a-glance situational awareness.

### 2. **Predictive AI for Flood Risk**

- Leverages Machine Learning models to **project which zones face flood risk** in the near-term future.
- Cross-references live weather API feeds against topographic depression maps to pinpoint vulnerable lowlands.

### 3. **Operational Dashboard for Disaster Relief**

- **Vulnerability Scoring:** Assigns priority rankings to affected areas — zones with hospitals, schools, or elderly populations in deep floodwater are automatically flagged for first response.
- Renders visual summaries of incoming flood reports, estimated stranded populations, and flood propagation trajectories.

### 4. **Smart Routing & Evacuation Navigation (Safe Routing)**

- When streets become waterways, the AI engages its routing engine to sever deeply flooded nodes from the graph and calculate the **optimal safe path** for vehicles and pedestrians alike.
- **Evacuation advisories:** Surfaces the closest elevated shelters and community safe havens.
- Issues direct mobile alerts to citizens approaching hazardous flood zones.

---

## 🏗️ System Architecture

### Layered Overview

| Layer | Key Components | What It Does |
|-------|----------------|-------------|
| **Client Layer** | `Next.js 15 Web App`, `React Native Mobile App` | Delivers interactive Mapbox-powered dashboards, citizen flood-reporting interfaces, emergency views, and push-based realtime alerts. |
| **API & Orchestration Layer** | `Laravel 11+ Backend API`, `Queue Worker (Horizon)` | Manages authentication (Sanctum), dynamic role-based access (Spatie Permission), all map/incident/prediction endpoints, event orchestration, and cross-service coordination. |
| **AI & Simulation Layer** | `Python FastAPI Service`, `LSTM / GNN models` | Executes water-level forecasting, cascading flood-impact propagation analysis (BFS heuristic on graph), what-if urban planning simulations, and recommendation generation. |
| **Data Layer** | `PostgreSQL 16 + PostGIS 3.4`, `Redis 7` | Persists users, incidents, the full spatial road-network graph (nodes/edges/zones), time-series sensor readings (monthly partitions), application cache, and job queues. |
| **Messaging & Realtime Layer** | `MQTT (Mosquitto)`, `Kafka`, `Soketi WebSocket` | Receives IoT water-level telemetry via MQTT, pipes event streams between services through Kafka, and pushes live state updates to all connected clients via the Pusher-compatible WebSocket layer. |
| **External Integrations** | `Mapbox GL JS`, `Firebase FCM`, `OpenWeather API` | Provides base map tiles, geocoding and directions context, push notification delivery to mobile devices, and weather observation data. |

### End-to-End Data Flow

1. **IoT water-level sensors and meteorological feeds** transmit raw flood telemetry into the platform via the MQTT → Kafka → Laravel Consumer pipeline.
2. **Laravel Backend** validates, deduplicates, and enriches each data packet, computes derived metrics (water_level, speed, flow), writes to PostgreSQL/PostGIS, enqueues background jobs, and broadcasts state transitions through Soketi WebSocket.
3. **Python AI Service** consumes incident context, current sensor snapshots, and the network graph to run flood-spread predictions (LSTM for temporal water-level curves, GNN for spatial graph propagation), execute planning simulations, and produce actionable recommendations.
4. **Redis-backed queue workers** handle computationally intensive tasks (AI inference calls, batch notification dispatch) asynchronously, ensuring the real-time monitoring loop remains unblocked.
5. **Soketi WebSocket** streams map layer updates, incident state changes, flood warnings, and AI-generated recommendations directly to dashboard and mobile clients with sub-second latency.
6. **Operators, citizens, and emergency responders** all interact with a unified flood map through their respective role-tailored interfaces — enabling synchronized monitoring, coordinated evacuations, and efficient relief distribution.

---

## 📊 Technology Stack

| Component | Technology | Port | Purpose |
|-----------|-----------|:----:|---------|
| Frontend | Next.js 15 + Mapbox GL JS | 3000 | Operator & Admin dashboard with interactive flood maps |
| Mobile | React Native CLI | — | Citizen reporting + Emergency responder app (Phase 2) |
| Backend | Laravel 11+ (PHP 8.3) | 8000 | REST API, domain events, background job orchestration |
| AI Service | Python FastAPI | 8001 | Flood prediction engine, impact simulation |
| Database | PostgreSQL 16 + PostGIS 3.4 | 5432 | Primary datastore with spatial query capabilities |
| Cache / Queue | Redis 7 | 6379 | Application cache + async job queue broker |
| Message Broker | Apache Kafka | 9092 | High-throughput IoT data ingestion pipeline |
| IoT Protocol | Mosquitto (MQTT) | 1883 | Lightweight sensor communication protocol |
| WebSocket | Soketi | 6001 | Realtime event broadcasting (Pusher-compatible) |

---

## 🌟 AegisFlow AI vs. The Status Quo

| Dimension | ❌ Conventional Maps & Tools | ✅ AegisFlow AI |
|-----------|------------------------------|-----------------|
| **Strategy** | Tracks congestion only — displays roads as "clear" even when submerged | Graph-aware exclusion — automatically removes flooded edges and reroutes |
| **Timing** | Reactive — people discover flooding only after driving into it | Predictive — broadcasts flood-avoidance paths **before** water arrives |
| **Resource Allocation** | Ad-hoc rescue coordination driven by gut feeling | Algorithmic vulnerability assessment that auto-prioritizes high-risk zones |
| **Information Latency** | Hours behind — depends on news outlets or manual reporting | Near-instant — IoT + citizen crowdsource + WebSocket push (**< 10s delay**) |
| **Geospatial Intelligence** | Minimal or nonexistent spatial computation | Full PostGIS spatial queries + graph-based flood propagation modeling |
| **Citizen Safety** | High risk — stranded vehicles, blocked evacuation paths | Maximized safety — every citizen gets a verified safe route home |

---

## ⚙️ Getting Started

### Quick Start with Docker (Recommended)

1. **Clone the repository and set up configuration:**
   ```bash
   git clone https://github.com/ASEAN-AI-DZ/AegisFlowAI.git
   cd AegisFlowAI
   cp docs/.env.example .env
   ```
   *Edit `.env` to add your Mapbox access token (`MAPBOX_TOKEN`).*

2. **Launch all services & initialize the database:**
   ```bash
   docker compose up -d --build
   docker exec -it aegisflow-laravel php artisan migrate --seed
   ```

3. **Access the platform services:**

   | Service | URL | Description |
   |---------|-----|-------------|
   | **Frontend** | http://localhost:3000 | Next.js Dashboard |
   | **Backend API** | http://localhost:8000/api | Laravel REST API |
   | **AI Service** | http://localhost:8001/docs | FastAPI Swagger UI |
   | **WebSocket** | ws://localhost:6001 | Soketi Realtime |

### Demo Credentials
```
Email:    admin@aegisflow.local
Password: password
```

> 📖 **Looking for a manual local setup?** 
> For full instructions on setting up each component manually, database administration commands, running test suites, or customizing configuration, please refer to the [Setup & Execution Guide (docs/RUNNING.md)](docs/RUNNING.md).


---

## 📞 Contact & Contributing

### Get in Touch

- **GitHub Repository:** https://github.com/ASEAN-AI-DZ/AegisFlowAI
- **Documentation Portal:** [AegisFlow AI Docs](https://asean-ai-dz.github.io/AegisFlowDocument/)

### How to Contribute

- Fork the repo → create a feature branch → submit a Pull Request.
- Found a bug? [Open an Issue](https://github.com/ASEAN-AI-DZ/AegisFlowAI/issues) with a clear description and reproduction steps.
- Have an idea? Join the Discussions tab to propose enhancements or help refine the AI models.

---

## 📄 License

This project is released under the **GNU General Public License v3.0**. See the [LICENSE](LICENSE) file for full terms.

---

_**Crafted with ❤️ for safe, resilient, and climate-ready cities**_

_"AegisFlow AI — Clearing the flow, shielding lives."_
