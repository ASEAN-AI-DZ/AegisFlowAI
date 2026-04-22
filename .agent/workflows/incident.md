---
description: Workflow xá»­ lÃ½ sá»± cá»‘ giao thÃ´ng. Táº¡o incident, trigger prediction, generate recommendation, notify operator.
---

# /incident â€” Xá»­ lÃ½ Sá»± cá»‘ Giao thÃ´ng

## Workflow

### BÆ°á»›c 1: Thu tháº­p thÃ´ng tin sá»± cá»‘

Há»i user hoáº·c láº¥y tá»« context:
- **Loáº¡i sá»± cá»‘**: accident | flood_severity | road_work | flood | other
- **Má»©c nghiÃªm trá»ng**: low | medium | high | critical
- **Vá»‹ trÃ­**: Edge IDs hoáº·c tÃªn Ä‘Æ°á»ng
- **Nguá»“n**: citizen_report | operator | auto_detected

### BÆ°á»›c 2: Táº¡o Incident trong há»‡ thá»‘ng

Sá»­ dá»¥ng `traffic-engineer` Ä‘á»ƒ validate business logic:
- Incident record há»£p lá»‡?
- Severity Ä‘Ãºng theo classification rules?
- Affected edges xÃ¡c Ä‘á»‹nh Ä‘Ãºng?

Sá»­ dá»¥ng `backend-specialist` Ä‘á»ƒ táº¡o API endpoint/logic:
```
POST /api/incidents
```

### BÆ°á»›c 3: Trigger Prediction

Sá»­ dá»¥ng `ai-ml-engineer` Ä‘á»ƒ gá»i Python AI:
```
POST python-ai:8001/predict
{
  "incident_id": ...,
  "affected_edges": [...],
  "severity": "..."
}
```

### BÆ°á»›c 4: Generate Recommendation

Tá»« prediction â†’ táº¡o recommendation:
- Reroute suggestions
- Priority route (náº¿u emergency)
- Alert cho citizen

Sá»­ dá»¥ng `backend-specialist` Ä‘á»ƒ lÆ°u recommendation + broadcast.

### BÆ°á»›c 5: Notify Operator

- Push notification qua WebSocket â†’ Frontend
- Operator approve/reject recommendation
- Náº¿u approved â†’ execute (broadcast changes)

## Agents Involved

| Step | Agent |
|------|-------|
| Validate logic | `traffic-engineer` |
| API + Events | `backend-specialist` |
| AI Prediction | `ai-ml-engineer` |
| Dashboard UI | `frontend-specialist` |

## Expected Output

- Incident created + saved to DB
- Prediction generated with confidence scores
- Recommendations presented to operator
- Realtime update on traffic map


