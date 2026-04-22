---
trigger: always_on
---

# GEMINI.md â€” AegisFlow AI Agent Rules

> Quy táº¯c AI Agent cho dá»± Ã¡n AegisFlow AI â€” Digital Twin quáº£n lÃ½ giao thÃ´ng Ä‘Ã´ thá»‹ thÃ´ng minh.

---

## CRITICAL: AGENT & SKILL PROTOCOL

> **Báº®T BUá»˜C:** Pháº£i Ä‘á»c agent file + skills TRÆ¯á»šC KHI viáº¿t code. ÄÃ¢y lÃ  luáº­t Æ°u tiÃªn cao nháº¥t.

### Modular Skill Loading

Agent activated â†’ Check frontmatter `skills:` â†’ Read SKILL.md â†’ Read specific sections.

- **Selective Reading:** Äá»c `SKILL.md` trÆ°á»›c, rá»“i chá»‰ Ä‘á»c sections phÃ¹ há»£p yÃªu cáº§u.
- **Rule Priority:** P0 (GEMINI.md) > P1 (Agent .md) > P2 (SKILL.md). Táº¥t cáº£ Ä‘á»u báº¯t buá»™c.

---

## ðŸ“¥ REQUEST CLASSIFIER

| Loáº¡i yÃªu cáº§u | Trigger Keywords | Active Tiers | Result |
|---------------|-----------------|--------------|--------|
| **Há»ŽI** | "what is", "how does", "giáº£i thÃ­ch" | TIER 0 | Text Response |
| **KHáº¢O SÃT** | "analyze", "overview", "xem cáº¥u trÃºc" | TIER 0 + Explorer | Session Intel |
| **CODE ÄÆ N GIáº¢N** | "fix", "sá»­a", "thÃªm" (single file) | TIER 0 + TIER 1 (lite) | Inline Edit |
| **CODE PHá»¨C Táº P** | "build", "táº¡o", "implement", "refactor" | TIER 0 + TIER 1 + Agent | `{task-slug}.md` Required |
| **DESIGN/UI** | "dashboard", "UI", "map", "layout" | TIER 0 + TIER 1 + Agent | `{task-slug}.md` Required |
| **SLASH CMD** | /create, /incident, /simulate | Command-specific flow | Variable |

---

## ðŸ¤– INTELLIGENT AGENT ROUTING (AUTO)

### AegisFlow AI Domain Routing

| Domain Keywords | Agent | Loáº¡i |
|----------------|-------|------|
| traffic, giao thÃ´ng, incident, sá»± cá»‘, water_level, flood_severity, reroute, graph, node, edge, actor | `traffic-engineer` | Domain |
| prediction, dá»± Ä‘oÃ¡n, model, LSTM, GNN, simulation, mÃ´ phá»ng, AI, ML, confidence, FastAPI, Python service | `ai-ml-engineer` | Domain |
| sensor, IoT, Kafka, MQTT, camera, pipeline, ingestion, weather, external API | `iot-integration-specialist` | Domain |
| mobile, react native, citizen app, emergency app, push notification | `mobile-developer` | Technical |
| API, endpoint, Laravel, controller, model, route, event, queue, broadcast, auth, middleware | `backend-specialist` | Technical |
| dashboard, map, Mapbox, component, React, UI, chart, layout, sidebar, panel, KPI, Next.js | `frontend-specialist` | Technical |
| database, schema, migration, query, PostGIS, spatial, index, table, Eloquent | `database-architect` | Technical |
| docker, deploy, container, Kafka setup, compose, CI/CD, production, server, infra | `devops-engineer` | Technical |
| security, auth, RBAC, vulnerability, permission | `security-auditor` | Technical |
| test, unit test, integration, E2E, coverage | `test-engineer` | Technical |
| orchestrate, coordinate, multi-agent, phá»©c táº¡p, full-stack | `orchestrator` | Meta |
| plan, breakdown, task, roadmap, phase | `project-planner` | Meta |
| debug, bug, error, root cause | `debugger` | Support |

### Response Format

```markdown
ðŸ¤– **Applying knowledge of `@[agent-name]`...**

[Tiáº¿p tá»¥c vá»›i response chuyÃªn biá»‡t]
```

### Agent Routing Checklist (Báº®T BUá»˜C)

| Step | Check | Náº¿u chÆ°a |
|------|-------|----------|
| 1 | XÃ¡c Ä‘á»‹nh Ä‘Ãºng agent cho domain? | â†’ Dá»ªNG. PhÃ¢n tÃ­ch domain. |
| 2 | ÄÃ£ Ä‘á»c agent `.md`? | â†’ Dá»ªNG. Má»Ÿ `.agent/agents/{agent}.md` |
| 3 | ÄÃ£ announce `ðŸ¤– Applying knowledge of @[agent]...`? | â†’ Dá»ªNG. ThÃªm announcement. |
| 4 | ÄÃ£ load skills tá»« frontmatter? | â†’ Dá»ªNG. Check `skills:` field. |

---

## TIER 0: QUY Táº®C TOÃ€N Cá»¤C

### ðŸŒ NgÃ´n ngá»¯

- Khi user viáº¿t tiáº¿ng Viá»‡t â†’ **Tráº£ lá»i tiáº¿ng Viá»‡t**
- Code comments/variables â†’ **English**

### ðŸ§¹ Clean Code

**Táº¤T Cáº¢ code pháº£i follow `@[skills/clean-code]`. KhÃ´ng ngoáº¡i lá»‡.**

### ðŸ“¦ Package Manager

- **Frontend (Next.js):** LuÃ´n dÃ¹ng `yarn`. KHÃ”NG dÃ¹ng `npm`.
- **Backend (Laravel):** DÃ¹ng `composer`.
- **AI Service (Python):** DÃ¹ng `pip`.

### ðŸ“ File Dependency Awareness

**TrÆ°á»›c khi sá»­a file:**
1. Kiá»ƒm tra file phá»¥ thuá»™c
2. XÃ¡c Ä‘á»‹nh files bá»‹ áº£nh hÆ°á»Ÿng
3. Cáº­p nháº­t Táº¤T Cáº¢ files liÃªn quan

### ðŸ—ºï¸ System Map

> ðŸ”´ **Báº®T BUá»˜C:** Äá»c `ARCHITECTURE.md` Ä‘á»ƒ hiá»ƒu AegisFlow AI agents, skills, tech stack.

### ðŸ§  Read â†’ Understand â†’ Apply

```
âŒ SAI: Äá»c agent file â†’ Code ngay
âœ… ÄÃšNG: Äá»c â†’ Hiá»ƒu Táº I SAO â†’ Ãp dá»¥ng NGUYÃŠN Táº®C â†’ Code
```

---

## TIER 1: QUY Táº®C CODE

### ðŸ“± Project Type Routing â€” AegisFlow AI

| Component | Primary Agent | Skills |
|-----------|--------------|--------|
| **Laravel Backend** | `backend-specialist` | api-patterns, database-design |
| **Next.js Frontend** | `frontend-specialist` | react-best-practices, frontend-design |
| **Python AI Service** | `ai-ml-engineer` | python-patterns |
| **Data Pipeline** | `iot-integration-specialist` | api-patterns |
| **Database** | `database-architect` | database-design |
| **Infrastructure** | `devops-engineer` | deployment-procedures |
| **Mobile App** | `mobile-developer` | mobile-design |

### ðŸ›‘ Socratic Gate

| Loáº¡i yÃªu cáº§u | HÃ nh Ä‘á»™ng |
|---------------|-----------|
| **Feature má»›i** | Há»ŽI tá»‘i thiá»ƒu 3 cÃ¢u há»i chiáº¿n lÆ°á»£c |
| **Sá»­a code / Fix bug** | XÃ¡c nháº­n hiá»ƒu + há»i impact |
| **MÆ¡ há»“** | Há»i Purpose, Actor, Scope |
| **Full Orchestration** | Dá»ªNG cho Ä‘áº¿n khi user confirm plan |

### ðŸ Final Checklist

| Script | Skill | Khi nÃ o |
|--------|-------|---------|
| `security_scan.py` | vulnerability-scanner | Má»i deploy |
| `lint_runner.py` | lint-and-validate | Má»i code change |
| `test_runner.py` | testing-patterns | Sau logic change |
| `schema_validator.py` | database-design | Sau DB change |
| `playwright_runner.py` | webapp-testing | TrÆ°á»›c deploy |

### ðŸŽ­ Mode Mapping

| Mode | Agent | Behavior |
|------|-------|----------|
| **plan** | `project-planner` | 4-phase. KHÃ”NG code trÆ°á»›c Phase 4. |
| **ask** | â€” | Há»i Ä‘á»ƒ hiá»ƒu. |
| **edit** | `orchestrator` | Check `{task-slug}.md` trÆ°á»›c. |

---

## ðŸ“ QUICK REFERENCE

### Agents AegisFlow AI

- **Domain**: `traffic-engineer`, `ai-ml-engineer`, `iot-integration-specialist`
- **Technical**: `backend-specialist` (Laravel), `frontend-specialist` (Next.js), `mobile-developer` (React Native), `database-architect` (PostGIS), `devops-engineer` (Docker), `security-auditor`, `test-engineer`
- **Meta**: `orchestrator`, `project-planner`, `debugger`

### Key Commands

- `/incident` â€” Xá»­ lÃ½ sá»± cá»‘ giao thÃ´ng
- `/simulate` â€” MÃ´ phá»ng ká»‹ch báº£n
- `/plan` â€” Láº­p káº¿ hoáº¡ch feature
- `/orchestrate` â€” Phá»‘i há»£p Ä‘a agent



