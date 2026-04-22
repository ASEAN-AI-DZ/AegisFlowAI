# Business Logic â€” AegisFlow AI

> Nghiá»‡p vá»¥ cá»‘t lÃµi: chuyá»ƒn Ä‘á»•i tá»« **pháº£n á»©ng (reactive)** sang **dá»± Ä‘oÃ¡n & chá»§ Ä‘á»™ng (predictive & proactive)**

---

## 0. Táº§m nhÃ¬n: Reactive â†’ Proactive

### MÃ´ hÃ¬nh truyá»n thá»‘ng (Reactive)

```
Sá»± cá»‘ xáº£y ra â†’ PhÃ¡t hiá»‡n (cháº­m) â†’ Pháº£n á»©ng (muá»™n) â†’ Thiá»‡t háº¡i Ä‘Ã£ lan rá»™ng
```

Váº¥n Ä‘á»: Chá»‰ hÃ nh Ä‘á»™ng **SAU KHI** váº¥n Ä‘á» xáº£y ra. Ã™n táº¯c Ä‘Ã£ lan rá»™ng, cá»©u há»™ bá»‹ káº¹t, thiá»‡t háº¡i lá»›n.

### MÃ´ hÃ¬nh AegisFlow AI (Predictive & Proactive)

```
Dá»¯ liá»‡u realtime â†’ AI dá»± Ä‘oÃ¡n â†’ Äá» xuáº¥t chá»§ Ä‘á»™ng â†’ Can thiá»‡p Sá»šM â†’ NgÄƒn thiá»‡t háº¡i
```

### Chuá»—i Proactive Pipeline

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”    â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”    â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”    â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”    â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  MONITOR    â”‚â”€â”€â”€â–¶â”‚   DETECT     â”‚â”€â”€â”€â–¶â”‚   PREDICT    â”‚â”€â”€â”€â–¶â”‚  RECOMMEND   â”‚â”€â”€â”€â–¶â”‚   ACT       â”‚
â”‚ GiÃ¡m sÃ¡t    â”‚    â”‚ PhÃ¡t hiá»‡n    â”‚    â”‚ Dá»± Ä‘oÃ¡n      â”‚    â”‚ Äá» xuáº¥t      â”‚    â”‚ HÃ nh Ä‘á»™ng   â”‚
â”‚ realtime    â”‚    â”‚ chá»§ Ä‘á»™ng     â”‚    â”‚ tÆ°Æ¡ng lai    â”‚    â”‚ tá»‘i Æ°u       â”‚    â”‚ sá»›m         â”‚
â”‚             â”‚    â”‚              â”‚    â”‚              â”‚    â”‚              â”‚    â”‚             â”‚
â”‚ IoT/Sensor  â”‚    â”‚ Auto-detect  â”‚    â”‚ LSTM/GNN     â”‚    â”‚ Reroute      â”‚    â”‚ Broadcast   â”‚
â”‚ â†’ water_level   â”‚    â”‚ anomaly      â”‚    â”‚ 15/30/60min  â”‚    â”‚ Priority     â”‚    â”‚ Push alert  â”‚
â”‚ â†’ speed     â”‚    â”‚ water_level spikeâ”‚    â”‚ confidence%  â”‚    â”‚ Alert        â”‚    â”‚ Execute     â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜    â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜    â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜    â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜    â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
     â”‚                   â”‚                    â”‚                   â”‚                   â”‚
     â–¼                   â–¼                    â–¼                   â–¼                   â–¼
 ðŸŸ¢ Luá»“ng 1         ðŸŸ¡ Luá»“ng 2          ðŸ”µ Luá»“ng 3         ðŸŸ  Luá»“ng 4         ðŸ”´ Luá»“ng 5
```

### 4 GiÃ¡ trá»‹ so vá»›i Reactive

| GiÃ¡ trá»‹ | Reactive (CÅ©) | Proactive (AegisFlow AI) |
|---------|---------------|--------------------------|
| ðŸš¦ **Giáº£m Ã¹n táº¯c** | Biáº¿t táº¯c khi Ä‘Ã£ táº¯c | Dá»± Ä‘oÃ¡n trÆ°á»›c 15â€“60 phÃºt, can thiá»‡p sá»›m |
| ðŸš‘ **Kháº©n cáº¥p nhanh** | TÃ¬m Ä‘Æ°á»ng báº±ng kinh nghiá»‡m | AI tÃ­nh tuyáº¿n tá»‘i Æ°u trÃ¡nh táº¯c |
| ðŸ“Š **Quyáº¿t Ä‘á»‹nh data-driven** | Cáº£m tÃ­nh, bÃ¡o cÃ¡o cÅ© | Realtime data + AI prediction + simulation |
| ðŸ’° **Tiáº¿t kiá»‡m chi phÃ­** | Pháº£n á»©ng cháº­m â†’ thiá»‡t háº¡i lá»›n | Can thiá»‡p sá»›m â†’ ngÄƒn lan rá»™ng |

## 1. MÃ´ hÃ¬nh Máº¡ng Giao thÃ´ng (Graph Network)

AegisFlow AI mÃ´ hÃ¬nh máº¡ng giao thÃ´ng nhÆ° **Ä‘á»“ thá»‹ cÃ³ hÆ°á»›ng cÃ³ trá»ng sá»‘** (Weighted Directed Graph):

```
Node (NÃºt giao)                    Edge (Äoáº¡n Ä‘Æ°á»ng)
â”œâ”€â”€ NgÃ£ tÆ° (intersection)          â”œâ”€â”€ Ná»‘i 2 nodes
â”œâ”€â”€ BÃ¹ng binh (roundabout)         â”œâ”€â”€ CÃ³ chiá»u dÃ i, sá»‘ lÃ n, tá»‘c Ä‘á»™ giá»›i háº¡n
â”œâ”€â”€ NÃºt cao tá»‘c (highway_entry)    â”œâ”€â”€ Má»™t chiá»u / hai chiá»u
â”œâ”€â”€ Cáº§u (bridge)                   â”œâ”€â”€ Metrics realtime: water_level, speed, flow
â””â”€â”€ Äiá»ƒm cuá»‘i (terminal)           â””â”€â”€ Tráº¡ng thÃ¡i: normal â†’ gridlock
```

---

## 2. CÃ´ng thá»©c TÃ­nh toÃ¡n Traffic Metrics

### 2.1 water_level (Máº­t Ä‘á»™)

```
water_level = vehicle_count / (length_m Ã— lanes)

GiÃ¡ trá»‹: 0.0 (trá»‘ng) â†’ 1.0 (káº¹t cá»©ng)
Cáº­p nháº­t: Má»—i khi nháº­n sensor data má»›i
```

### 2.2 Speed Ratio (Tá»· lá»‡ tá»‘c Ä‘á»™)

```
speed_ratio = current_speed_kmh / speed_limit_kmh

< 0.3 = Ã™n táº¯c nghiÃªm trá»ng
> 0.7 = LÆ°u thÃ´ng bÃ¬nh thÆ°á»ng
```

### 2.3 Flow (LÆ°u lÆ°á»£ng)

```
flow = water_level Ã— current_speed_kmh

ÄÆ¡n vá»‹: xeÂ·km/h trÃªn má»—i Ä‘Æ¡n vá»‹ diá»‡n tÃ­ch
Khi water_level tÄƒng quÃ¡ má»©c â†’ speed giáº£m â†’ flow giáº£m (paradox)
```

### 2.4 Delay (Thá»i gian cháº­m trá»…)

```
delay_seconds = (length_m / current_speed_kmh) - (length_m / speed_limit_kmh)

Ã— 3.6 Ä‘á»ƒ chuyá»ƒn km/h â†’ m/s
Ã nghÄ©a: Máº¥t thÃªm bao nhiÃªu giÃ¢y so vá»›i bÃ¬nh thÆ°á»ng
```

---

## 3. flood_severity Level Classification

Há»‡ thá»‘ng tá»± Ä‘á»™ng phÃ¢n loáº¡i má»©c táº¯c ngháº½n dá»±a trÃªn water_level + speed_ratio:

| Level | water_level | Speed Ratio | MÃ u map | Ã nghÄ©a |
|-------|---------|-------------|---------|----------|
| **NONE** | < 0.3 | > 0.7 | ðŸŸ¢ Xanh | LÆ°u thÃ´ng tá»‘t |
| **LIGHT** | 0.3 â€“ 0.5 | 0.5 â€“ 0.7 | ðŸŸ¡ VÃ ng | HÆ¡i Ä‘Ã´ng |
| **MODERATE** | 0.5 â€“ 0.7 | 0.3 â€“ 0.5 | ðŸŸ  Cam | Cháº­m rÃµ rá»‡t |
| **HEAVY** | 0.7 â€“ 0.9 | 0.1 â€“ 0.3 | ðŸ”´ Äá» | Táº¯c ngháº½n |
| **GRIDLOCK** | > 0.9 | < 0.1 | âš« Äá» Ä‘áº­m | Káº¹t cá»©ng |

**Quy táº¯c xÃ¡c Ä‘á»‹nh:**
```
if water_level < 0.3 AND speed_ratio > 0.7 â†’ NONE
elif water_level < 0.5 OR speed_ratio > 0.5 â†’ LIGHT  
elif water_level < 0.7 OR speed_ratio > 0.3 â†’ MODERATE
elif water_level < 0.9 OR speed_ratio > 0.1 â†’ HEAVY
else â†’ GRIDLOCK
```

**áº¢nh hÆ°á»Ÿng thá»i tiáº¿t:**
```
if weather = "rain"  â†’ effective_speed_limit Ã— 0.8  (giáº£m 20%)
if weather = "storm" â†’ effective_speed_limit Ã— 0.6  (giáº£m 40%)
if weather = "fog"   â†’ effective_speed_limit Ã— 0.7  (giáº£m 30%)
```

---

## 4. NÄƒm Luá»“ng Nghiá»‡p vá»¥ ChÃ­nh

### Luá»“ng 1: Thu tháº­p & Cáº­p nháº­t Realtime

**Trigger:** Sensor gá»­i data má»—i 10â€“60 giÃ¢y

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”     â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”     â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ IoT Sensor  â”‚â”€â”€â”€â”€â–¶â”‚  MQTT /  â”‚â”€â”€â”€â”€â–¶â”‚  Kafka Topic     â”‚
â”‚ Camera/Radarâ”‚     â”‚  HTTP    â”‚     â”‚ traffic.sensor   â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜     â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜     â””â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
                                              â”‚
                                    â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â–¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
                                    â”‚  Laravel Consumer   â”‚
                                    â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â” â”‚
                                    â”‚  â”‚ 1. Validate    â”‚ â”‚
                                    â”‚  â”‚ 2. Deduplicate â”‚ â”‚
                                    â”‚  â”‚ 3. Enrich      â”‚ â”‚
                                    â”‚  â”‚ 4. Anomaly     â”‚ â”‚
                                    â”‚  â”‚    check       â”‚ â”‚
                                    â”‚  â”‚ 5. Calculate   â”‚ â”‚
                                    â”‚  â”‚    metrics     â”‚ â”‚
                                    â”‚  â”‚ 6. Auto-detect â”‚ â”‚
                                    â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”˜ â”‚
                                    â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
                                               â”‚
                              â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
                              â–¼                â–¼                â–¼
                   â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”   â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”   â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
                   â”‚ Update DB    â”‚   â”‚ Broadcast    â”‚   â”‚ Check     â”‚
                   â”‚ edge metrics â”‚   â”‚ WebSocket    â”‚   â”‚ auto-     â”‚
                   â”‚ + readings   â”‚   â”‚ â†’ Dashboard  â”‚   â”‚ detect    â”‚
                   â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜   â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜   â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Business Rules:**

| Step | Rule | HÃ nh Ä‘á»™ng khi vi pháº¡m |
|------|------|----------------------|
| Validate | speed â‰¥ 0, count â‰¥ 0, speed â‰¤ 200 | Reject, log warning |
| Deduplicate | Kiá»ƒm tra `message_id` Ä‘Ã£ xá»­ lÃ½ | Skip, khÃ´ng process láº¡i |
| Enrich | Gáº¯n `edge_id` tá»« `sensor_id` | Reject náº¿u sensor khÃ´ng tá»“n táº¡i |
| Anomaly | GiÃ¡ trá»‹ thay Ä‘á»•i > 50% trong 1 phÃºt | Flag `is_anomaly = true`, váº«n process |
| Sensor offline | KhÃ´ng nháº­n data > 3 phÃºt | Mark sensor `offline`, giáº£m confidence |

---

### Luá»“ng 2: PhÃ¡t hiá»‡n & Xá»­ lÃ½ Sá»± cá»‘ (Incident)

**3 nguá»“n táº¡o sá»± cá»‘:**

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ 1. Auto-detect  â”‚â”€â”€ water_level tÄƒng > 0.3 trong 5 phÃºt
â”‚    (Há»‡ thá»‘ng)   â”‚â”€â”€ speed giáº£m > 50%
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚ 2. Operator     â”‚â”€â”€ Táº¡o thá»§ cÃ´ng tá»« dashboard
â”‚    (Thá»§ cÃ´ng)    â”‚â”€â”€ Chá»n vá»‹ trÃ­ + edges trÃªn map
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚ 3. Citizen      â”‚â”€â”€ BÃ¡o cÃ¡o qua mobile app
â”‚    (NgÆ°á»i dÃ¢n)   â”‚â”€â”€ Gá»­i áº£nh + GPS location
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
         â”‚
         â–¼
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚              INCIDENT CREATED            â”‚
â”‚  Event: IncidentCreated                  â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚  1. LÆ°u vÃ o DB (status = 'open')        â”‚
â”‚  2. XÃ¡c Ä‘á»‹nh affected_edge_ids          â”‚
â”‚  3. Classify severity (auto)            â”‚
â”‚  4. Dispatch Job: CallAIPrediction      â”‚
â”‚  5. Notify assigned operator            â”‚
â”‚  6. Broadcast â†’ Dashboard map           â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Auto-detection Rules:**

```
Rule 1: water_level Spike
  IF edge.water_level tÄƒng > 0.3 trong 5 phÃºt
  AND edge.speed giáº£m > 50%
  â†’ Táº¡o incident (type=flood_severity, source=auto_detected)

Rule 2: Speed Drop
  IF edge.current_speed < 5 km/h
  AND edge.current_water_level > 0.8
  AND kÃ©o dÃ i > 3 phÃºt
  â†’ Táº¡o incident (type=flood_severity, severity=high)

Rule 3: Sensor Anomaly Cluster
  IF â‰¥ 3 sensors trÃªn cÃ¹ng khu vá»±c ghi nháº­n anomaly cÃ¹ng lÃºc
  â†’ Táº¡o incident (type=other, source=auto_detected)
  â†’ Flag cho operator review
```

---

### Luá»“ng 3: Dá»± Ä‘oÃ¡n AI (Prediction)

**Trigger:** Incident created â†’ Job gá»i Python AI

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚               PREDICTION FLOW                 â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                              â”‚
â”‚  Laravel                    Python AI        â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”              â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”     â”‚
â”‚  â”‚CallAI    â”‚  HTTP POST   â”‚/predict  â”‚     â”‚
â”‚  â”‚Predictionâ”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â–¶â”‚          â”‚     â”‚
â”‚  â”‚Job       â”‚  {           â”‚ 1. Load  â”‚     â”‚
â”‚  â”‚          â”‚   incident,  â”‚    graph  â”‚     â”‚
â”‚  â”‚          â”‚   edges,     â”‚ 2. LSTM   â”‚     â”‚
â”‚  â”‚          â”‚   severity   â”‚    predictâ”‚     â”‚
â”‚  â”‚          â”‚  }           â”‚ 3. GNN    â”‚     â”‚
â”‚  â”‚          â”‚              â”‚    spread â”‚     â”‚
â”‚  â”‚          â”‚â—€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚ 4. Score  â”‚     â”‚
â”‚  â”‚          â”‚  predictions â”‚    conf.  â”‚     â”‚
â”‚  â””â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”˜              â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜     â”‚
â”‚       â”‚                                      â”‚
â”‚       â–¼                                      â”‚
â”‚  Save predictions â†’ DB                       â”‚
â”‚  Event: PredictionReceived                   â”‚
â”‚  â†’ GenerateRecommendation                    â”‚
â”‚  â†’ BroadcastToFrontend                       â”‚
â”‚  â†’ NotifyOperator                            â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Prediction Output per Edge:**

| Field | Ã nghÄ©a | VÃ­ dá»¥ |
|-------|---------|-------|
| `edge_id` | Edge nÃ o bá»‹ áº£nh hÆ°á»Ÿng | 48 |
| `time_horizon_minutes` | Dá»± Ä‘oÃ¡n sau bao lÃ¢u | 15, 30, 60 |
| `predicted_water_level` | Máº­t Ä‘á»™ dá»± Ä‘oÃ¡n | 0.85 |
| `predicted_delay_s` | Thá»i gian cháº­m trá»… (giÃ¢y) | 180 |
| `confidence` | Äá»™ tin cáº­y | 0.78 |
| `severity` | Má»©c nghiÃªm trá»ng | high |

**Confidence Score Calculation:**

```
confidence = base_confidence Ã— recency_factor Ã— data_quality_factor

base_confidence:      Model accuracy tá»« validation set (MAE, RMSE)
recency_factor:       1.0 náº¿u data < 5 phÃºt, giáº£m 0.05/phÃºt sau Ä‘Ã³
data_quality_factor:  avg(data_quality) cá»§a sensors trÃªn edge
                      Náº¿u sensor offline â†’ factor = 0.3

VÃ­ dá»¥: 0.82 Ã— 0.95 Ã— 0.90 = 0.70 (confidence = 70%)
```

**Fallback khi AI Service lá»—i:**

| TÃ¬nh huá»‘ng | Action |
|------------|--------|
| AI timeout > 5s | DÃ¹ng cached prediction gáº§n nháº¥t |
| AI service down | Rule-based: if water_level > 0.7 â†’ predict flood_severity sáº½ lan rá»™ng |
| KhÃ´ng Ä‘á»§ data | Tráº£ confidence = 0.0 kÃ¨m warning |
| Model lá»—i | Log error, notify admin, khÃ´ng táº¡o prediction |

---

### Luá»“ng 4: Äá» xuáº¥t & Ra quyáº¿t Ä‘á»‹nh (Recommendation)

**Trigger:** Prediction completed â†’ Generate recommendation

```
Prediction Results
        â”‚
        â–¼
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚          RECOMMENDATION ENGINE                 â”‚
â”‚                                                â”‚
â”‚  Input: predictions[]                          â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”      â”‚
â”‚  â”‚ Filter: severity >= medium          â”‚      â”‚
â”‚  â”‚ AND confidence >= 0.5               â”‚      â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜      â”‚
â”‚                 â”‚                              â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â–¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”      â”‚
â”‚  â”‚ Type Selection:                     â”‚      â”‚
â”‚  â”‚                                     â”‚      â”‚
â”‚  â”‚ IF incident.severity = CRITICAL     â”‚      â”‚
â”‚  â”‚   â†’ priority_route + alert          â”‚      â”‚
â”‚  â”‚                                     â”‚      â”‚
â”‚  â”‚ IF incident.severity = HIGH         â”‚      â”‚
â”‚  â”‚   â†’ reroute + alert                 â”‚      â”‚
â”‚  â”‚                                     â”‚      â”‚
â”‚  â”‚ IF incident.severity = MEDIUM       â”‚      â”‚
â”‚  â”‚   â†’ reroute (suggestion only)       â”‚      â”‚
â”‚  â”‚                                     â”‚      â”‚
â”‚  â”‚ IF incident.severity = LOW          â”‚      â”‚
â”‚  â”‚   â†’ monitor only (no recommendation)â”‚      â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜      â”‚
â”‚                 â”‚                              â”‚
â”‚                 â–¼                              â”‚
â”‚  Save recommendation (status = 'pending')     â”‚
â”‚  Notify operator â†’ Dashboard                  â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
        â”‚
        â–¼
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚   OPERATOR DECISION       â”‚
â”‚                           â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â” â”‚
â”‚  â”‚ APPROVE â”‚  â”‚ REJECT â”‚ â”‚
â”‚  â””â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”˜  â””â”€â”€â”€â”¬â”€â”€â”€â”€â”˜ â”‚
â”‚       â”‚           â”‚      â”‚
â”‚       â–¼           â–¼      â”‚
â”‚  Execute:    Log reason   â”‚
â”‚  - Broadcast  (audit)    â”‚
â”‚    reroute               â”‚
â”‚  - Push alert            â”‚
â”‚    to citizen            â”‚
â”‚  - Update                â”‚
â”‚    traffic               â”‚
â”‚    signals               â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**4 loáº¡i Recommendation:**

| Type | Äiá»u kiá»‡n | Ná»™i dung |
|------|-----------|----------|
| **reroute** | Edges bá»‹ táº¯c, cÃ³ Ä‘Æ°á»ng thay tháº¿ | alternative_edges[], estimated_time_saved_s |
| **priority_route** | Emergency request hoáº·c severity=CRITICAL | from_node â†’ to_node, route_edges[] |
| **alert** | Cáº§n cáº£nh bÃ¡o citizen | message, target_zones[], channels[] |
| **signal_control** | CÃ³ thá»ƒ thay Ä‘á»•i Ä‘Ã¨n (tÆ°Æ¡ng lai) | intersection_id, suggested_timing |

---

### Luá»“ng 5: MÃ´ phá»ng Quy hoáº¡ch (Simulation)

**Trigger:** Urban Planner táº¡o scenario

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚                 SIMULATION FLOW                     â”‚
â”œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤
â”‚                                                    â”‚
â”‚  Step 1: Define Scenario                           â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”         â”‚
â”‚  â”‚ changes = [                          â”‚         â”‚
â”‚  â”‚   { action: "add_edge",      ... },  â”‚         â”‚
â”‚  â”‚   { action: "modify_edge",   ... },  â”‚         â”‚
â”‚  â”‚   { action: "remove_edge",   ... },  â”‚         â”‚
â”‚  â”‚   { action: "modify_node",   ... }   â”‚         â”‚
â”‚  â”‚ ]                                    â”‚         â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜         â”‚
â”‚                                                    â”‚
â”‚  Step 2: Validate                                  â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”         â”‚
â”‚  â”‚ - Nodes tá»“n táº¡i?                    â”‚         â”‚
â”‚  â”‚ - Edges há»£p lá»‡ (source â‰  target)?   â”‚         â”‚
â”‚  â”‚ - Graph váº«n connected sau thay Ä‘á»•i? â”‚         â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜         â”‚
â”‚                                                    â”‚
â”‚  Step 3: Run Simulation (Python)                   â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”         â”‚
â”‚  â”‚ - Clone graph hiá»‡n táº¡i               â”‚         â”‚
â”‚  â”‚ - Apply changes                      â”‚         â”‚
â”‚  â”‚ - Simulate 24h traffic patterns      â”‚         â”‚
â”‚  â”‚ - Calculate metrics táº¡i má»—i timestep â”‚         â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜         â”‚
â”‚                                                    â”‚
â”‚  Step 4: Compare                                   â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”         â”‚
â”‚  â”‚ Baseline      vs    Simulated        â”‚         â”‚
â”‚  â”‚ avg_water_level         avg_water_level      â”‚         â”‚
â”‚  â”‚ avg_delay           avg_delay        â”‚         â”‚
â”‚  â”‚ congested_edges     congested_edges  â”‚         â”‚
â”‚  â”‚                                      â”‚         â”‚
â”‚  â”‚ â†’ improvement_pct for each metric    â”‚         â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜         â”‚
â”‚                                                    â”‚
â”‚  Step 5: Impact Report                             â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”         â”‚
â”‚  â”‚ - water_level giáº£m X%                    â”‚         â”‚
â”‚  â”‚ - Delay giáº£m Y%                      â”‚         â”‚
â”‚  â”‚ - Congested edges giáº£m Z%            â”‚         â”‚
â”‚  â”‚ - Top 5 edges improved               â”‚         â”‚
â”‚  â”‚ - Top 5 edges worsened               â”‚         â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜         â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

---

## 5. Incident Severity Logic

### Classification Rules

| Level | Äiá»u kiá»‡n | Auto/Manual | Pháº£n á»©ng há»‡ thá»‘ng |
|-------|-----------|-------------|-------------------|
| **LOW** | Va cháº¡m nhá», 1 lane blocked, water_level < 0.5 | Manual | ThÃ´ng bÃ¡o operator |
| **MEDIUM** | Tai náº¡n, 2+ lanes blocked, water_level 0.5â€“0.7 | Cáº£ hai | Predict + recommend reroute |
| **HIGH** | Tai náº¡n nghiÃªm trá»ng, Ä‘Æ°á»ng blocked, water_level > 0.7 | Cáº£ hai | Auto-predict + urgent notification |
| **CRITICAL** | ThiÃªn tai, ngáº­p, sáº­p cáº§u, Ä‘Æ°á»ng hoÃ n toÃ n blocked | Manual | Emergency mode + priority route + alert all citizens |

### Auto-escalation Rules

```
IF incident severity = LOW
  AND after 30 minutes water_level trÃªn affected edges > 0.7
  â†’ Escalate to MEDIUM (auto)
  â†’ Trigger new prediction

IF incident severity = MEDIUM
  AND prediction shows flood_severity spreading to > 5 edges
  AND confidence > 0.6
  â†’ Escalate to HIGH (auto)
  â†’ Urgent notification to all operators

IF incident severity = HIGH
  AND no operator response within 10 minutes
  â†’ Alert City Admin
  â†’ Auto-create priority route recommendation
```

### Incident Lifecycle

```
OPEN â†’ INVESTIGATING â†’ RESOLVED â†’ CLOSED

â”Œâ”€â”€â”€â”€â”€â”€â”   Operator     â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”   Operator    â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”   Auto/Manual  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚ OPEN â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â–¶â”‚INVESTIGATING â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â–¶â”‚ RESOLVED â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â–¶â”‚ CLOSED â”‚
â””â”€â”€â”€â”€â”€â”€â”˜   picks up     â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜   confirms    â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜   after 24h    â””â”€â”€â”€â”€â”€â”€â”€â”€â”˜
                              â”‚                             â”‚
                              â”‚ Re-open if                  â”‚
                              â”‚ water_level spikes again        â”‚
                              â—„â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

---

## 6. Priority Route Logic

Khi Emergency Services yÃªu cáº§u tuyáº¿n Æ°u tiÃªn:

```
Input: from_node (vá»‹ trÃ­ hiá»‡n táº¡i), to_node (Ä‘Ã­ch)

Step 1: Dijkstra shortest path trÃªn graph
   weight = length_m / current_speed_kmh  (thá»i gian travel)

Step 2: Filter tuyáº¿n
   Loáº¡i bá» edges: status = 'closed' hoáº·c 'blocked'

Step 3: Kiá»ƒm tra flood_severity
   IF any edge on route cÃ³ water_level > 0.7:
      â†’ TÃ¬m alternative route (trÃ¡nh edge Ä‘Ã³)
      â†’ So sÃ¡nh: alternative faster? â†’ Chá»n alternative

Step 4: Náº¿u táº¥t cáº£ routes Ä‘á»u congested:
   â†’ Äá» xuáº¥t "can thiá»‡p": thÃ´ng bÃ¡o cÃ¡c xe phÃ­a trÆ°á»›c dáº¡t sang
   â†’ Broadcast tuyáº¿n Æ°u tiÃªn lÃªn map â†’ vehicles tháº¥y vÃ  trÃ¡nh

Step 5: Output
   - route_edges: [10, 11, 12, 15]
   - estimated_time_minutes: 8
   - Broadcast trÃªn map (hiá»ƒn thá»‹ route + icon emergency)
```

---

## 7. Notification Logic

### Khi nÃ o gá»­i notification

| Event | Recipients | Channel | Priority |
|-------|-----------|---------|----------|
| Incident CRITICAL | All operators + Admin | Push + WebSocket | ðŸ”´ Urgent |
| Incident HIGH | Assigned operator + Admin | Push + WebSocket | ðŸŸ  High |
| Incident MEDIUM | Assigned operator | WebSocket | ðŸŸ¡ Normal |
| Prediction ready | Assigned operator | WebSocket | ðŸŸ¡ Normal |
| Recommendation pending | Operators with permission | WebSocket | ðŸŸ¡ Normal |
| Recommendation approved | Affected citizens (by zone) | Push | ðŸŸ¢ Info |
| Sensor offline > 10 min | Admin | Push | ðŸŸ  High |
| AI Service down | Admin | Push + Email | ðŸ”´ Urgent |

### Push Notification cho Citizen (Phase 2)

```
Trigger: Recommendation approved (type = alert)
Filter:  Citizens trong target_zones
Content: {
  title: "âš ï¸ Cáº£nh bÃ¡o giao thÃ´ng",
  body: "Ã™n táº¯c nghiÃªm trá»ng trÃªn Äiá»‡n BiÃªn Phá»§. Vui lÃ²ng chá»n Ä‘Æ°á»ng khÃ¡c.",
  data: { incident_id, affected_edges, alternative_routes }
}
```

---

## 8. Edge Status State Machine

```
                    sensor data OK
           â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
           â”‚                            â”‚
           â–¼                            â”‚
       â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”   water_level > 0.7   â”Œâ”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”
       â”‚ NORMAL â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â–¶â”‚CONGESTED â”‚
       â””â”€â”€â”€â”¬â”€â”€â”€â”€â”˜                   â””â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”˜
           â”‚                             â”‚
    incidentâ”‚created                incidentâ”‚resolved
    (blocked)â”‚                      water_level drops
           â”‚                             â”‚
           â–¼                             â–¼
       â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”   incident         â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”
       â”‚BLOCKED â”‚   resolved         â”‚ NORMAL â”‚
       â””â”€â”€â”€â”¬â”€â”€â”€â”€â”˜â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â–¶â””â”€â”€â”€â”€â”€â”€â”€â”€â”˜
           â”‚
    admin closes road
           â”‚
           â–¼
       â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”   admin re-opens
       â”‚ CLOSED â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â–¶ NORMAL
       â””â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

**Transition Rules:**
- `NORMAL â†’ CONGESTED`: Tá»± Ä‘á»™ng khi water_level > 0.7 AND speed_ratio < 0.3
- `CONGESTED â†’ NORMAL`: Tá»± Ä‘á»™ng khi water_level < 0.5 AND speed_ratio > 0.5
- `NORMAL/CONGESTED â†’ BLOCKED`: Khi incident xÃ¡c nháº­n Ä‘Æ°á»ng bá»‹ blocked
- `BLOCKED â†’ NORMAL`: Operator resolve incident
- `* â†’ CLOSED`: Admin Ä‘Ã³ng Ä‘Æ°á»ng thá»§ cÃ´ng
- `CLOSED â†’ NORMAL`: Admin má»Ÿ láº¡i

---

## 9. Activity Logging Rules

### Nhá»¯ng hÃ nh Ä‘á»™ng PHáº¢I log

| Action | Log Name | Description |
|--------|----------|-------------|
| Incident created | incident | "Created incident #{id}: {title}" |
| Incident status changed | incident | "Updated status: {old} â†’ {new}" |
| Incident severity changed | incident | "Escalated severity: {old} â†’ {new}" |
| Incident assigned | incident | "Assigned to operator #{user_id}" |
| Recommendation approved | recommendation | "Approved recommendation #{id}" |
| Recommendation rejected | recommendation | "Rejected: {reason}" |
| Recommendation executed | recommendation | "Executed reroute/alert/priority" |
| User role changed | user | "Role changed: {old_roles} â†’ {new_roles}" |
| Sensor status changed | sensor | "Sensor {code}: {old_status} â†’ {new_status}" |
| Edge manually closed/opened | edge | "Edge #{id} {action} by admin" |
| Simulation run | simulation | "Ran simulation: {scenario_name}" |

### Log format (Laravel Activity Log)

```json
{
  "log_name": "incident",
  "description": "updated",
  "subject_type": "App\\Models\\Incident",
  "subject_id": 42,
  "causer_id": 5,
  "event": "updated",
  "properties": {
    "old": { "status": "open", "severity": "medium" },
    "new": { "status": "investigating", "severity": "high" }
  }
}
```

---

## 10. TÃ³m táº¯t Logic chÃ­nh

| # | Logic | Input | Output | Trigger |
|---|-------|-------|--------|---------|
| 1 | TÃ­nh metrics | Sensor data | water_level, speed, flow, flood_severity_level | Má»—i 10-60s |
| 2 | Auto-detect | water_level spike / speed drop | New incident | Realtime check |
| 3 | Prediction | Incident + graph | predicted water_level/delay per edge | Incident created |
| 4 | Recommendation | Prediction results | reroute / priority / alert | Prediction done |
| 5 | Escalation | Time + water_level change | Severity upgrade | Periodic check |
| 6 | Priority route | From/To nodes | Optimal route avoiding flood_severity | Emergency request |
| 7 | Simulation | Scenario changes | Before/After comparison | Planner request |
| 8 | Notification | System events | Push / WebSocket / Email | Event-driven |



