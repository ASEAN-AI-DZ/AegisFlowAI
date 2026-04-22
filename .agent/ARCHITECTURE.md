# AegisFlow AI â€” Agent Architecture

> Cáº¥u hÃ¬nh AI Agent cho dá»± Ã¡n Digital Twin quáº£n lÃ½ giao thÃ´ng Ä‘Ã´ thá»‹ thÃ´ng minh.

---

## ðŸ“‹ Tá»•ng quan Dá»± Ã¡n

**AegisFlow AI** lÃ  ná»n táº£ng Digital Twin cho quáº£n lÃ½ giao thÃ´ng Ä‘Ã´ thá»‹ thÃ´ng minh:
- **GiÃ¡m sÃ¡t realtime** máº¡ng giao thÃ´ng qua IoT/sensor
- **Dá»± Ä‘oÃ¡n** táº¯c ngháº½n lan rá»™ng trÆ°á»›c khi xáº£y ra (LSTM/GNN)
- **Äá» xuáº¥t hÃ nh Ä‘á»™ng** cá»¥ thá»ƒ cho operator (reroute, priority route, alert)
- **MÃ´ phá»ng** tÃ¡c Ä‘á»™ng quy hoáº¡ch dÃ i háº¡n

### Tech Stack

| Layer | CÃ´ng nghá»‡ |
|-------|-----------|
| Backend | Laravel 11+ (PHP 8.3) |
| Frontend | Next.js 15 + Mapbox GL JS |
| AI/ML | Python FastAPI (LSTM/GNN) |
| Database | PostgreSQL 16 + PostGIS |
| Cache/Queue | Redis + Laravel Horizon |
| Message Broker | Kafka + MQTT |
| WebSocket | Soketi (Laravel Echo) |
| Container | Docker Compose |
| Mobile | React Native CLI (Phase 2) |

### Actors

| Actor | Phase | Vai trÃ² |
|-------|-------|---------|
| City Admin | 1 | Quáº£n trá»‹ toÃ n bá»™, cáº¥u hÃ¬nh há»‡ thá»‘ng |
| Disaster Operator | 1 | GiÃ¡m sÃ¡t realtime, xá»­ lÃ½ sá»± cá»‘ |
| Citizen | 2 | BÃ¡o cÃ¡o sá»± cá»‘, nháº­n cáº£nh bÃ¡o (mobile app) |
| Emergency Services | 2 | Tuyáº¿n Æ°u tiÃªn cá»©u há»™, navigation (mobile app) |

---

## ðŸ—ï¸ Cáº¥u trÃºc thÆ° má»¥c

```plaintext
.agent/
â”œâ”€â”€ ARCHITECTURE.md          # File nÃ y
â”œâ”€â”€ agents/                  # 21 Agent chuyÃªn biá»‡t
â”œâ”€â”€ skills/                  # 36 Skills (knowledge modules)
â”œâ”€â”€ workflows/               # 13 Slash Commands
â”œâ”€â”€ rules/                   # Global Rules (GEMINI.md)
â””â”€â”€ scripts/                 # Validation Scripts
```

---

## ðŸ¤– Agents (21)

### Domain Agents â€” ChuyÃªn biá»‡t AegisFlow AI (3)

| Agent | Focus | MÃ´ táº£ |
|-------|-------|-------|
| `traffic-engineer` | Giao thÃ´ng Ä‘Ã´ thá»‹ | Graph model, 5 luá»“ng nghiá»‡p vá»¥, actors, incident flow |
| `ai-ml-engineer` | AI/ML dá»± Ä‘oÃ¡n | LSTM/GNN model, FastAPI, prediction/simulation API |
| `iot-integration-specialist` | IoT pipeline | Kafka/MQTT, sensor data, anomaly detection |

### Technical Agents â€” Triá»ƒn khai ká»¹ thuáº­t (8)

| Agent | Focus | Skills |
|-------|-------|--------|
| `backend-specialist` | Laravel API | api-patterns, database-design |
| `frontend-specialist` | Next.js + Mapbox | react-best-practices, frontend-design, tailwind-patterns |
| `mobile-developer` | React Native (Citizen/Emergency) | mobile-design |
| `database-architect` | PostgreSQL + PostGIS | database-design |
| `orchestrator` | Phá»‘i há»£p Ä‘a agent | parallel-agents, behavioral-modes, plan-writing |
| `devops-engineer` | Docker, Kafka, deploy | deployment-procedures, server-management |
| `security-auditor` | Security, RBAC | vulnerability-scanner, red-team-tactics |
| `test-engineer` | Testing | testing-patterns, tdd-workflow, webapp-testing |

### Support Agents (10)

| Agent | Focus |
|-------|-------|
| `project-planner` | Láº­p káº¿ hoáº¡ch, phÃ¢n tÃ¡ch task |
| `debugger` | Root cause analysis |
| `performance-optimizer` | Tá»‘i Æ°u hiá»‡u nÄƒng |
| `penetration-tester` | Offensive security |
| `documentation-writer` | Táº¡o tÃ i liá»‡u |
| `product-manager` | Requirements, user stories |
| `product-owner` | Strategy, backlog |
| `qa-automation-engineer` | E2E testing, CI |
| `code-archaeologist` | Legacy refactoring |
| `explorer-agent` | KhÃ¡m phÃ¡ codebase |

---

## ðŸ“Š Agent Routing â€” AegisFlow AI

| Náº¿u task liÃªn quan Ä‘áº¿n... | Agent chÃ­nh |
|--------------------------|-------------|
| Business logic giao thÃ´ng, incident, graph | `traffic-engineer` |
| Laravel API, Events, Queue, Broadcasting | `backend-specialist` |
| Next.js, Mapbox, Dashboard, Charts | `frontend-specialist` |
| PostgreSQL, PostGIS, Schema, Migrations | `database-architect` |
| Python, AI model, Prediction, Simulation | `ai-ml-engineer` |
| Kafka, MQTT, Sensor, External API | `iot-integration-specialist` |
| React Native, mobile app, Citizen/Emergency | `mobile-developer` |
| Docker, Deploy, Infra | `devops-engineer` |
| Security, Auth, RBAC | `security-auditor` |
| Tests | `test-engineer` |
| Multi-domain (> 2 agents) | `orchestrator` |
| Task breakdown, Planning | `project-planner` |
| Debug, Root cause | `debugger` |

---

## ðŸ”„ Workflows (13)

| Command | MÃ´ táº£ |
|---------|-------|
| `/brainstorm` | KhÃ¡m phÃ¡ Socratic |
| `/create` | Táº¡o feature má»›i |
| `/debug` | Debug issues |
| `/deploy` | Deploy á»©ng dá»¥ng |
| `/enhance` | Cáº£i thiá»‡n code |
| `/incident` | **[Má»šI]** Xá»­ lÃ½ sá»± cá»‘ giao thÃ´ng |
| `/orchestrate` | Phá»‘i há»£p Ä‘a agent |
| `/plan` | PhÃ¢n tÃ¡ch task |
| `/preview` | Preview server |
| `/simulate` | **[Má»šI]** MÃ´ phá»ng giao thÃ´ng |
| `/status` | Kiá»ƒm tra tráº¡ng thÃ¡i |
| `/test` | Cháº¡y tests |
| `/ui-ux-pro-max` | Thiáº¿t káº¿ UI |

---

## ðŸŽ¯ Quick Reference

| Cáº§n | Agent | Skills |
|-----|-------|--------|
| Incident flow | `traffic-engineer` + `orchestrator` | domain knowledge |
| API endpoint | `backend-specialist` | api-patterns |
| Map + Dashboard | `frontend-specialist` | react-best-practices, frontend-design |
| Database schema | `database-architect` | database-design |
| AI prediction | `ai-ml-engineer` | python-patterns |
| Sensor pipeline | `iot-integration-specialist` | api-patterns |
| Docker setup | `devops-engineer` | deployment-procedures |
| Security audit | `security-auditor` | vulnerability-scanner |
| Unit tests | `test-engineer` | testing-patterns |
| Full feature | `orchestrator` | parallel-agents |


