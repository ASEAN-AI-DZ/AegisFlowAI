---
description: Workflow mÃ´ phá»ng ká»‹ch báº£n giao thÃ´ng. Äá»‹nh nghÄ©a scenario, cháº¡y simulation, so sÃ¡nh before/after, táº¡o bÃ¡o cÃ¡o tÃ¡c Ä‘á»™ng.
---

# /simulate â€” MÃ´ phá»ng Giao thÃ´ng

## Workflow

### BÆ°á»›c 1: Äá»‹nh nghÄ©a ká»‹ch báº£n

Há»i user:
- **TÃªn ká»‹ch báº£n**: VD: "Má»Ÿ Ä‘Æ°á»ng Nguyá»…n VÄƒn A"
- **Thay Ä‘á»•i**:
  - ThÃªm node/edge má»›i (má»Ÿ Ä‘Æ°á»ng)
  - Sá»­a edge (thÃªm lane, thay Ä‘á»•i speed limit)
  - XÃ³a/Ä‘Ã³ng edge (Ä‘Ã³ng Ä‘Æ°á»ng sá»­a chá»¯a)
  - Äá»•i chiá»u (má»™t chiá»u â†’ hai chiá»u)
- **Thá»i gian mÃ´ phá»ng**: VD: 24 giá», 96 time steps

### BÆ°á»›c 2: Validate ká»‹ch báº£n

Sá»­ dá»¥ng `traffic-engineer` Ä‘á»ƒ validate:
- Ká»‹ch báº£n há»£p logic khÃ´ng? (node/edge tá»“n táº¡i?)
- Thay Ä‘á»•i cÃ³ vi pháº¡m constraints nÃ o khÃ´ng?
- Metrics nÃ o cáº§n so sÃ¡nh?

### BÆ°á»›c 3: Gá»i Simulation API

Sá»­ dá»¥ng `ai-ml-engineer`:
```
POST python-ai:8001/simulate
{
  "scenario_name": "...",
  "changes": [...],
  "simulation_duration_hours": 24,
  "time_steps": 96
}
```

### BÆ°á»›c 4: PhÃ¢n tÃ­ch káº¿t quáº£

So sÃ¡nh baseline vs simulated:
- Avg water_level giáº£m X%?
- Avg delay giáº£m Y%?
- Sá»‘ edge congested giáº£m Z%?

### BÆ°á»›c 5: Táº¡o bÃ¡o cÃ¡o

Táº¡o impact report cho Urban Planner:
- Summary: cáº£i thiá»‡n hay xáº¥u Ä‘i?
- Chi tiáº¿t per-edge changes
- Recommendations

## Agents Involved

| Step | Agent |
|------|-------|
| Validate scenario | `traffic-engineer` |
| Simulation API | `ai-ml-engineer` |
| Backend support | `backend-specialist` |
| Report UI | `frontend-specialist` |

## Expected Output

- Simulation completed
- Before/After comparison table
- Impact report with % improvement
- Visual comparison trÃªn map (optional)


