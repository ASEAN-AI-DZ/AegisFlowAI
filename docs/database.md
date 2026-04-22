# Database Schema â€” AegisFlow AI

> PostgreSQL 16 + PostGIS 3.4 | ORM: Laravel Eloquent | Auth: Spatie Permission

---

## 1. ERD (Entity-Relationship Diagram)

```
                     â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
                     â”‚          SPATIE PERMISSION LAYER           â”‚
                     â”‚ â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â” â”‚
                     â”‚ â”‚permissions â”‚  â”‚  roles                â”‚ â”‚
                     â”‚ â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚  â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚ â”‚
                     â”‚ â”‚ id         â”‚  â”‚ id                    â”‚ â”‚
                     â”‚ â”‚ name       â”‚â—„â”€â”‚ name                  â”‚ â”‚
                     â”‚ â”‚ guard_name â”‚  â”‚ guard_name            â”‚ â”‚
                     â”‚ â””â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”˜  â””â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜ â”‚
                     â”‚       â”‚                â”‚                  â”‚
                     â”‚ â”Œâ”€â”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”€â”€â” â”Œâ”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â” â”‚
                     â”‚ â”‚role_has_      â”‚ â”‚model_has_roles     â”‚ â”‚
                     â”‚ â”‚ permissions   â”‚ â”‚model_has_permissionsâ”‚ â”‚
                     â”‚ â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜ â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜ â”‚
                     â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
                                                 â”‚ model_id
                                                 â–¼
                           â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
                           â”‚    users      â”‚
                           â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚
                           â”‚ id           â”‚
                           â”‚ name         â”‚
                           â”‚ email        â”‚
                           â”‚ password     â”‚
                           â”‚ created_at   â”‚
                           â”‚ updated_at   â”‚
                           â””â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”˜
                                  â”‚
              â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¼â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
              â”‚ reported_by       â”‚ assigned_to        â”‚ approved_by
              â–¼                   â–¼                    â–¼
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”          â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”     â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚   zones      â”‚          â”‚  incidents   â”‚     â”‚recommendations â”‚
â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚          â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚     â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚
â”‚ id           â”‚          â”‚ id           â”‚     â”‚ id             â”‚
â”‚ name         â”‚          â”‚ title        â”‚     â”‚ prediction_id  â”‚
â”‚ boundary     â”‚â—„â”€â”       â”‚ type         â”‚     â”‚ type           â”‚
â”‚ (POLYGON)    â”‚  â”‚       â”‚ severity     â”‚     â”‚ status         â”‚
â”‚ created_at   â”‚  â”‚       â”‚ location (PT)â”‚     â”‚ approved_by    â”‚
â”‚ updated_at   â”‚  â”‚       â”‚ deleted_at   â”‚     â”‚ created_at     â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜  â”‚       â””â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”˜     â”‚ updated_at     â”‚
                  â”‚              â”‚              â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
                  â”‚              â”‚ incident_id          â–²
                  â”‚              â–¼                      â”‚
                  â”‚       â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”             â”‚
                  â”‚       â”‚ predictions  â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
                  â”‚       â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚ prediction_id
                  â”‚       â”‚ id           â”‚
                  â”‚       â”‚ incident_id  â”‚
                  â”‚       â”‚ model_versionâ”‚
                  â”‚       â”‚ created_at   â”‚
                  â”‚       â””â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”˜
                  â”‚              â”‚ prediction_id
                  â”‚              â–¼
                  â”‚       â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
                  â”‚       â”‚prediction_edgesâ”‚
                  â”‚       â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚
                  â”‚       â”‚ prediction_idâ”€â”€â”‚â”€â”€â–¶ predictions
                  â”‚       â”‚ edge_idâ”€â”€â”€â”€â”€â”€â”€â”€â”‚â”€â”€â–¶ edges
                  â”‚       â”‚ predicted_     â”‚
                  â”‚       â”‚   water_level      â”‚
                  â”‚       â”‚ confidence     â”‚
                  â”‚       â”‚ created_at     â”‚
                  â”‚       â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
                  â”‚
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”     â”‚
â”‚  nodes   â”‚     â”‚        â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”     â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚     â”‚        â”‚    edges     â”‚     â”‚   sensors    â”‚
â”‚ id       â”‚     â”‚        â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚     â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚
â”‚ name     â”‚     â”‚        â”‚ id           â”‚     â”‚ id           â”‚
â”‚ type     â”‚     â”‚        â”‚ name         â”‚     â”‚ sensor_code  â”‚
â”‚ location â”‚     â”‚        â”‚ source_nodeâ”€â”€â”‚â”€â”€â–¶  â”‚ edge_idâ”€â”€â”€â”€â”€â”€â”‚â”€â”€â–¶ edges
â”‚ (POINT)  â”‚     â”‚        â”‚ target_nodeâ”€â”€â”‚â”€â”€â–¶  â”‚ type         â”‚
â”‚ zone_idâ”€â”€â”‚â”€â”€â”€â”€â”€â”˜        â”‚ geometry     â”‚     â”‚ status       â”‚
â”‚ created_atâ”‚â—„â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚ (LINESTRING) â”‚     â”‚ created_at   â”‚
â”‚ updated_atâ”‚ src / tgt   â”‚ current_     â”‚     â”‚ updated_at   â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜              â”‚   water_level    â”‚     â””â”€â”€â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”€â”€â”˜
                          â”‚ flood_severity   â”‚            â”‚ sensor_id
                          â”‚ created_at   â”‚            â–¼
                          â”‚ updated_at   â”‚     â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
                          â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜     â”‚ sensor_readings  â”‚
                                               â”‚ (PARTITIONED)    â”‚
                â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”               â”‚ edge_id, sensor_idâ”‚
                â”‚activity_logs â”‚               â”‚ recorded_at      â”‚
                â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚               â”‚ vehicle_count    â”‚
                â”‚ causer_id    â”‚               â”‚ avg_speed_kmh    â”‚
                â”‚ subject_type â”‚               â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
                â”‚ description  â”‚
                â”‚ properties   â”‚       â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
                â”‚ created_at   â”‚       â”‚  notifications   â”‚
                â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜       â”‚â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”‚
                                       â”‚ user_id          â”‚
                                       â”‚ type             â”‚
                                       â”‚ data (JSONB)     â”‚
                                       â”‚ read_at          â”‚
                                       â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

---

## 2. Danh sÃ¡ch Tables (14 tables)

| # | Table | MÃ´ táº£ | Spatial | SoftDelete | Timestamps |
|---|-------|-------|---------|------------|------------|
| 1 | `users` | NgÆ°á»i dÃ¹ng | âŒ | âœ… | âœ… |
| 2 | `zones` | VÃ¹ng Ä‘Ã´ thá»‹ | âœ… Polygon | âŒ | âœ… |
| 3 | `nodes` | NÃºt giao thÃ´ng | âœ… Point | âœ… | âœ… |
| 4 | `edges` | Äoáº¡n Ä‘Æ°á»ng | âœ… LineString | âœ… | âœ… |
| 5 | `sensors` | Thiáº¿t bá»‹ cáº£m biáº¿n | âŒ | âœ… | âœ… |
| 6 | `sensor_readings` | Dá»¯ liá»‡u time-series | âŒ | âŒ | âŒ (cÃ³ `recorded_at`) |
| 7 | `incidents` | Sá»± cá»‘ giao thÃ´ng | âœ… Point | âœ… | âœ… |
| 8 | `predictions` | Káº¿t quáº£ dá»± Ä‘oÃ¡n | âŒ | âŒ | âœ… |
| 9 | `prediction_edges` | Dá»± Ä‘oÃ¡n per-edge | âŒ | âŒ | âœ… |
| 10 | `recommendations` | Äá» xuáº¥t hÃ nh Ä‘á»™ng | âŒ | âœ… | âœ… |
| 11 | `activity_logs` | Audit trail (Spatie) | âŒ | âŒ | âœ… |
| 12 | `notifications` | Push/email (Laravel) | âŒ | âŒ | âœ… |
| 13 | `roles` + `permissions` | PhÃ¢n quyá»n Ä‘á»™ng (Spatie) | âŒ | âŒ | âœ… |
| 14 | `personal_access_tokens` | API tokens (Sanctum) | âŒ | âŒ | âœ… |

---

## 3. PhÃ¢n quyá»n Äá»™ng (Spatie Permission)

> Package: `spatie/laravel-permission` â€” PhÃ¢n quyá»n Ä‘á»™ng, quáº£n lÃ½ qua database, khÃ´ng hardcode.

### Roles (Vai trÃ²)

| Role | MÃ´ táº£ | Phase |
|------|-------|-------|
| `super_admin` | Full access, bypass má»i permission | 1 |
| `city_admin` | Quáº£n trá»‹ dashboard, cáº¥u hÃ¬nh há»‡ thá»‘ng | 1 |
| `disaster_operator` | GiÃ¡m sÃ¡t map, xá»­ lÃ½ sá»± cá»‘ | 1 |
| `urban_planner` | Cháº¡y simulation, xem bÃ¡o cÃ¡o | 1 |
| `emergency` | Request priority route | 2 |
| `citizen` | BÃ¡o cÃ¡o sá»± cá»‘, nháº­n cáº£nh bÃ¡o | 2 |

### Permissions (Quyá»n háº¡n)

| Module | Permission | Roles máº·c Ä‘á»‹nh |
|--------|-----------|-----------------|
| **Dashboard** | `dashboard.view` | admin, operator, planner |
| **Dashboard** | `dashboard.configure` | admin |
| **Map** | `map.view` | admin, operator, planner, emergency |
| **Map** | `map.edit-layers` | admin, operator |
| **Incidents** | `incidents.view` | admin, operator, emergency |
| **Incidents** | `incidents.create` | admin, operator, citizen |
| **Incidents** | `incidents.update` | admin, operator |
| **Incidents** | `incidents.delete` | admin |
| **Incidents** | `incidents.assign` | admin, operator |
| **Predictions** | `predictions.view` | admin, operator, emergency |
| **Predictions** | `predictions.trigger` | admin, operator |
| **Recommendations** | `recommendations.view` | admin, operator |
| **Recommendations** | `recommendations.approve` | admin, operator |
| **Recommendations** | `recommendations.reject` | admin, operator |
| **Simulation** | `simulation.run` | admin, planner |
| **Simulation** | `simulation.view-results` | admin, planner |
| **Reports** | `reports.view` | admin, planner |
| **Reports** | `reports.export` | admin |
| **Users** | `users.view` | admin |
| **Users** | `users.create` | admin |
| **Users** | `users.update` | admin |
| **Users** | `users.delete` | admin |
| **Users** | `users.assign-roles` | admin |
| **Sensors** | `sensors.view` | admin, operator |
| **Sensors** | `sensors.manage` | admin |
| **System** | `system.settings` | admin |
| **System** | `system.logs` | admin |
| **Priority Route** | `priority-route.request` | admin, emergency |
| **Notifications** | `notifications.send` | admin, operator |
| **Citizen** | `citizen-reports.create` | citizen |
| **Citizen** | `citizen-reports.view-own` | citizen |

### Spatie Tables (tá»± Ä‘á»™ng táº¡o bá»Ÿi package)

```
permissions              roles                model_has_permissions
â”œâ”€â”€ id                   â”œâ”€â”€ id               â”œâ”€â”€ permission_id (FK)
â”œâ”€â”€ name                 â”œâ”€â”€ name             â”œâ”€â”€ model_type
â”œâ”€â”€ guard_name           â”œâ”€â”€ guard_name       â””â”€â”€ model_id
â”œâ”€â”€ created_at           â”œâ”€â”€ created_at
â””â”€â”€ updated_at           â””â”€â”€ updated_at       model_has_roles
                                              â”œâ”€â”€ role_id (FK)
role_has_permissions                          â”œâ”€â”€ model_type
â”œâ”€â”€ permission_id (FK)                        â””â”€â”€ model_id
â””â”€â”€ role_id (FK)
```

**Æ¯u Ä‘iá»ƒm phÃ¢n quyá»n Ä‘á»™ng:**
- âœ… ThÃªm/sá»­a/xÃ³a role & permission qua Dashboard (khÃ´ng cáº§n deploy)
- âœ… GÃ¡n nhiá»u roles cho 1 user
- âœ… Permission káº¿ thá»«a (role cÃ³ permissions â†’ user cÃ³ role â†’ user cÃ³ permissions)
- âœ… Middleware báº£o vá»‡ route: `->middleware('permission:incidents.create')`
- âœ… Policy káº¿t há»£p: `Gate::allows('incidents.update')` trong code

---

## 4. Schema Chi tiáº¿t

### 4.1 users

| Column | Type | Constraints | MÃ´ táº£ |
|--------|------|-------------|-------|
| `id` | BIGSERIAL | PK | |
| `name` | VARCHAR(255) | NOT NULL | TÃªn hiá»ƒn thá»‹ |
| `email` | VARCHAR(255) | UNIQUE, NOT NULL | Email Ä‘Äƒng nháº­p |
| `email_verified_at` | TIMESTAMP | NULLABLE | |
| `password` | VARCHAR(255) | NOT NULL | Hashed (bcrypt) |
| `phone` | VARCHAR(20) | NULLABLE | Sá»‘ Ä‘iá»‡n thoáº¡i |
| `avatar` | VARCHAR(500) | NULLABLE | URL avatar |
| `is_active` | BOOLEAN | DEFAULT true | TÃ i khoáº£n active? |
| `last_login_at` | TIMESTAMP | NULLABLE | Láº§n Ä‘Äƒng nháº­p cuá»‘i |
| `remember_token` | VARCHAR(100) | NULLABLE | |
| `created_at` | TIMESTAMP | NOT NULL | |
| `updated_at` | TIMESTAMP | NOT NULL | |
| `deleted_at` | TIMESTAMP | NULLABLE | Soft delete |

---

### 4.2 zones

| Column | Type | Constraints | MÃ´ táº£ |
|--------|------|-------------|-------|
| `id` | BIGSERIAL | PK | |
| `name` | VARCHAR(255) | NOT NULL | TÃªn vÃ¹ng |
| `code` | VARCHAR(50) | UNIQUE | MÃ£ vÃ¹ng |
| `type` | VARCHAR(50) | DEFAULT 'district' | district / ward / special_zone |
| `boundary` | GEOMETRY(Polygon, 4326) | NOT NULL | PostGIS polygon |
| `metadata` | JSONB | DEFAULT '{}' | ThÃ´ng tin bá»• sung |
| `created_at` | TIMESTAMP | NOT NULL | |
| `updated_at` | TIMESTAMP | NOT NULL | |

**Indexes:** `GIST(boundary)`

---

### 4.3 nodes

| Column | Type | Constraints | MÃ´ táº£ |
|--------|------|-------------|-------|
| `id` | BIGSERIAL | PK | |
| `name` | VARCHAR(255) | NOT NULL | VD: "NgÃ£ tÆ° HÃ ng Xanh" |
| `type` | VARCHAR(50) | NOT NULL, DEFAULT 'intersection' | intersection / roundabout / highway_entry / bridge / terminal |
| `location` | GEOMETRY(Point, 4326) | NOT NULL | Tá»a Ä‘á»™ PostGIS |
| `zone_id` | BIGINT | FK â†’ zones(id), NULLABLE | |
| `has_traffic_light` | BOOLEAN | DEFAULT false | |
| `metadata` | JSONB | DEFAULT '{}' | |
| `status` | VARCHAR(20) | DEFAULT 'active' | active / inactive / under_construction |
| `created_at` | TIMESTAMP | NOT NULL | |
| `updated_at` | TIMESTAMP | NOT NULL | |
| `deleted_at` | TIMESTAMP | NULLABLE | Soft delete |

**Indexes:** `GIST(location)`, `btree(zone_id)`, `btree(type)`

---

### 4.4 edges

| Column | Type | Constraints | MÃ´ táº£ |
|--------|------|-------------|-------|
| `id` | BIGSERIAL | PK | |
| `name` | VARCHAR(255) | NOT NULL | TÃªn Ä‘Æ°á»ng |
| `source_node_id` | BIGINT | FK â†’ nodes(id), NOT NULL | Node báº¯t Ä‘áº§u |
| `target_node_id` | BIGINT | FK â†’ nodes(id), NOT NULL | Node káº¿t thÃºc |
| `geometry` | GEOMETRY(LineString, 4326) | NOT NULL | HÃ¬nh dáº¡ng Ä‘Æ°á»ng |
| `length_m` | DECIMAL(10,2) | NOT NULL | Chiá»u dÃ i (mÃ©t) |
| `lanes` | SMALLINT | NOT NULL, DEFAULT 2 | Sá»‘ lÃ n xe |
| `speed_limit_kmh` | SMALLINT | NOT NULL, DEFAULT 50 | Giá»›i háº¡n tá»‘c Ä‘á»™ |
| `direction` | VARCHAR(10) | DEFAULT 'two_way' | one_way / two_way |
| `road_type` | VARCHAR(50) | DEFAULT 'urban' | highway / urban / residential / service |
| â€” | â€” | â€” | **âš¡ Realtime Metrics** |
| `current_water_level` | DECIMAL(5,4) | DEFAULT 0.0 | 0.0 â†’ 1.0 |
| `current_speed_kmh` | DECIMAL(6,2) | DEFAULT 0.0 | |
| `current_flow` | DECIMAL(8,2) | DEFAULT 0.0 | |
| `flood_severity_level` | VARCHAR(20) | DEFAULT 'none' | none / light / moderate / heavy / gridlock |
| `status` | VARCHAR(20) | DEFAULT 'normal' | normal / congested / blocked / closed |
| `metrics_updated_at` | TIMESTAMP | NULLABLE | |
| `created_at` | TIMESTAMP | NOT NULL | |
| `updated_at` | TIMESTAMP | NOT NULL | |
| `deleted_at` | TIMESTAMP | NULLABLE | Soft delete |

**Constraints:** `CHECK(source_node_id != target_node_id)`

**Indexes:** `GIST(geometry)`, `btree(source_node_id)`, `btree(target_node_id)`, `btree(flood_severity_level)`, `btree(status)`, `btree(metrics_updated_at)`

---

### 4.5 sensors

| Column | Type | Constraints | MÃ´ táº£ |
|--------|------|-------------|-------|
| `id` | BIGSERIAL | PK | |
| `sensor_code` | VARCHAR(100) | UNIQUE, NOT NULL | VD: "CAM_DBP_01" |
| `edge_id` | BIGINT | FK â†’ edges(id), NOT NULL | Gáº¯n trÃªn edge nÃ o |
| `type` | VARCHAR(50) | NOT NULL | camera / radar / loop_detector / manual |
| `model` | VARCHAR(100) | NULLABLE | Model thiáº¿t bá»‹ |
| `firmware_version` | VARCHAR(50) | NULLABLE | |
| `status` | VARCHAR(20) | DEFAULT 'online' | online / offline / maintenance |
| `last_active_at` | TIMESTAMP | NULLABLE | |
| `metadata` | JSONB | DEFAULT '{}' | |
| `installed_at` | TIMESTAMP | NULLABLE | |
| `created_at` | TIMESTAMP | NOT NULL | |
| `updated_at` | TIMESTAMP | NOT NULL | |
| `deleted_at` | TIMESTAMP | NULLABLE | Soft delete |

**Indexes:** `btree(edge_id)`, `btree(status)`, `UNIQUE(sensor_code)`

---

### 4.6 sensor_readings âš¡ (Partitioned â€” KHÃ”NG cÃ³ updated_at)

> Time-series data â€” chá»‰ insert, khÃ´ng update. DÃ¹ng `recorded_at` thay cho `created_at`.

| Column | Type | Constraints | MÃ´ táº£ |
|--------|------|-------------|-------|
| `id` | BIGSERIAL | | |
| `sensor_id` | BIGINT | FK â†’ sensors(id), NOT NULL | |
| `edge_id` | BIGINT | FK â†’ edges(id), NOT NULL | Denormalized cho query nhanh |
| `recorded_at` | TIMESTAMP | NOT NULL | Thá»i Ä‘iá»ƒm Ä‘o (= created_at) |
| `vehicle_count` | INTEGER | NULLABLE | |
| `avg_speed_kmh` | DECIMAL(6,2) | NULLABLE | |
| `occupancy_pct` | DECIMAL(5,2) | NULLABLE | |
| `water_level` | DECIMAL(5,4) | NULLABLE | |
| `data_quality` | DECIMAL(3,2) | DEFAULT 1.0 | |
| `is_anomaly` | BOOLEAN | DEFAULT false | |
| `raw_data` | JSONB | NULLABLE | |

**PK:** `(id, recorded_at)` â€” Composite cho partition

**Partition:** `RANGE(recorded_at)` theo thÃ¡ng

**Indexes:** `btree(edge_id, recorded_at DESC)`, `btree(sensor_id, recorded_at DESC)`

> âš ï¸ **Táº¡i sao khÃ´ng cÃ³ `created_at`/`updated_at`?** Sensor readings lÃ  append-only (chá»‰ insert, khÃ´ng bao giá» update). `recorded_at` Ä‘Ã£ Ä‘Ã³ng vai trÃ² `created_at`. ThÃªm `updated_at` lÃ£ng phÃ­ storage cho hÃ ng triá»‡u records.

---

### 4.7 incidents

| Column | Type | Constraints | MÃ´ táº£ |
|--------|------|-------------|-------|
| `id` | BIGSERIAL | PK | |
| `title` | VARCHAR(255) | NOT NULL | |
| `description` | TEXT | NULLABLE | |
| `type` | VARCHAR(50) | NOT NULL | accident / flood_severity / road_work / flood / other |
| `severity` | VARCHAR(20) | NOT NULL | low / medium / high / critical |
| `status` | VARCHAR(20) | DEFAULT 'open' | open / investigating / resolved / closed |
| `source` | VARCHAR(30) | NOT NULL | citizen_report / operator / auto_detected |
| `location` | GEOMETRY(Point, 4326) | NULLABLE | |
| `affected_edge_ids` | BIGINT[] | DEFAULT '{}' | |
| `reported_by` | BIGINT | FK â†’ users(id), NULLABLE | |
| `assigned_to` | BIGINT | FK â†’ users(id), NULLABLE | |
| `resolved_at` | TIMESTAMP | NULLABLE | |
| `metadata` | JSONB | DEFAULT '{}' | áº¢nh, video, thÃ´ng tin thÃªm |
| `created_at` | TIMESTAMP | NOT NULL | |
| `updated_at` | TIMESTAMP | NOT NULL | |
| `deleted_at` | TIMESTAMP | NULLABLE | Soft delete |

**Indexes:** `btree(status)`, `btree(severity)`, `GIST(location)`, `btree(created_at DESC)`, `GIN(affected_edge_ids)`

---

### 4.8 predictions

| Column | Type | Constraints | MÃ´ táº£ |
|--------|------|-------------|-------|
| `id` | BIGSERIAL | PK | |
| `incident_id` | BIGINT | FK â†’ incidents(id), NULLABLE | |
| `model_version` | VARCHAR(50) | NOT NULL | VD: "lstm_v2.1" |
| `processing_time_ms` | INTEGER | NULLABLE | |
| `status` | VARCHAR(20) | DEFAULT 'completed' | pending / completed / failed |
| `error_message` | TEXT | NULLABLE | Náº¿u failed |
| `created_at` | TIMESTAMP | NOT NULL | |
| `updated_at` | TIMESTAMP | NOT NULL | |

**Indexes:** `btree(incident_id)`, `btree(status)`

---

### 4.9 prediction_edges

| Column | Type | Constraints | MÃ´ táº£ |
|--------|------|-------------|-------|
| `id` | BIGSERIAL | PK | |
| `prediction_id` | BIGINT | FK â†’ predictions(id) ON DELETE CASCADE | |
| `edge_id` | BIGINT | FK â†’ edges(id) | |
| `time_horizon_minutes` | SMALLINT | NOT NULL | 15 / 30 / 60 |
| `predicted_water_level` | DECIMAL(5,4) | NULLABLE | |
| `predicted_delay_s` | INTEGER | NULLABLE | |
| `confidence` | DECIMAL(3,2) | NULLABLE | 0.00 â†’ 1.00 |
| `severity` | VARCHAR(20) | NULLABLE | |
| `created_at` | TIMESTAMP | NOT NULL | |

> â„¹ï¸ KhÃ´ng cÃ³ `updated_at` â€” prediction results lÃ  immutable (báº¥t biáº¿n), chá»‰ insert.

**Indexes:** `btree(prediction_id)`, `btree(edge_id)`

---

### 4.10 recommendations

| Column | Type | Constraints | MÃ´ táº£ |
|--------|------|-------------|-------|
| `id` | BIGSERIAL | PK | |
| `prediction_id` | BIGINT | FK â†’ predictions(id), NULLABLE | |
| `incident_id` | BIGINT | FK â†’ incidents(id), NULLABLE | |
| `type` | VARCHAR(30) | NOT NULL | reroute / priority_route / alert / signal_control |
| `description` | TEXT | NOT NULL | |
| `details` | JSONB | DEFAULT '{}' | (xem examples bÃªn dÆ°á»›i) |
| `status` | VARCHAR(20) | DEFAULT 'pending' | pending / approved / rejected / executed |
| `approved_by` | BIGINT | FK â†’ users(id), NULLABLE | |
| `approved_at` | TIMESTAMP | NULLABLE | |
| `rejected_reason` | TEXT | NULLABLE | LÃ½ do tá»« chá»‘i |
| `executed_at` | TIMESTAMP | NULLABLE | |
| `created_at` | TIMESTAMP | NOT NULL | |
| `updated_at` | TIMESTAMP | NOT NULL | |
| `deleted_at` | TIMESTAMP | NULLABLE | Soft delete |

**Details JSONB Examples:**
```json
// Reroute
{ "alternative_edges": [52, 53], "estimated_time_saved_s": 150 }

// Priority Route
{ "from_node": 1, "to_node": 50, "route_edges": [10, 11, 12], "estimated_time_minutes": 8 }

// Alert
{ "message": "Ã™n táº¯c trÃªn Äiá»‡n BiÃªn Phá»§", "target_zones": [1, 2], "channels": ["push"] }
```

**Indexes:** `btree(status)`, `btree(incident_id)`

---

### 4.11 activity_logs (Spatie Activity Log)

> Package: `spatie/laravel-activitylog` â€” Audit trail tá»± Ä‘á»™ng.

| Column | Type | Constraints | MÃ´ táº£ |
|--------|------|-------------|-------|
| `id` | BIGSERIAL | PK | |
| `log_name` | VARCHAR(255) | NULLABLE | VD: "incident", "recommendation" |
| `description` | TEXT | NOT NULL | VD: "created", "updated", "approved" |
| `subject_type` | VARCHAR(255) | NULLABLE | Model class bá»‹ tÃ¡c Ä‘á»™ng |
| `subject_id` | BIGINT | NULLABLE | ID cá»§a record bá»‹ tÃ¡c Ä‘á»™ng |
| `causer_type` | VARCHAR(255) | NULLABLE | Model class ngÆ°á»i thá»±c hiá»‡n |
| `causer_id` | BIGINT | NULLABLE | ID user thá»±c hiá»‡n |
| `properties` | JSONB | NULLABLE | Old/new values (diff) |
| `batch_uuid` | UUID | NULLABLE | Group related actions |
| `event` | VARCHAR(255) | NULLABLE | created / updated / deleted |
| `created_at` | TIMESTAMP | NOT NULL | |
| `updated_at` | TIMESTAMP | NOT NULL | |

**VÃ­ dá»¥ log:**
```json
{
  "log_name": "incident",
  "description": "updated",
  "subject_type": "App\\Models\\Incident",
  "subject_id": 42,
  "causer_id": 5,
  "properties": {
    "old": { "status": "open", "severity": "medium" },
    "new": { "status": "investigating", "severity": "high" }
  }
}
```

**Indexes:** `btree(subject_type, subject_id)`, `btree(causer_type, causer_id)`, `btree(log_name)`, `btree(created_at DESC)`

---

### 4.12 notifications (Laravel Notifications)

> Laravel built-in notification system â€” lÆ°u push/email/SMS.

| Column | Type | Constraints | MÃ´ táº£ |
|--------|------|-------------|-------|
| `id` | UUID | PK | |
| `type` | VARCHAR(255) | NOT NULL | Notification class name |
| `notifiable_type` | VARCHAR(255) | NOT NULL | Model class (User) |
| `notifiable_id` | BIGINT | NOT NULL | User ID |
| `data` | JSONB | NOT NULL | Ná»™i dung notification |
| `read_at` | TIMESTAMP | NULLABLE | ÄÃ£ Ä‘á»c chÆ°a |
| `created_at` | TIMESTAMP | NOT NULL | |
| `updated_at` | TIMESTAMP | NOT NULL | |

**Data JSONB Example:**
```json
{
  "title": "Sá»± cá»‘ má»›i: Tai náº¡n trÃªn Äiá»‡n BiÃªn Phá»§",
  "incident_id": 42,
  "severity": "high",
  "action_url": "/dashboard/incidents/42"
}
```

**Indexes:** `btree(notifiable_type, notifiable_id)`, `btree(read_at)`

---

## 5. Relationships

```
users           1 â”€â”€â”€â”€ N  incidents          (reported_by, assigned_to)
users           1 â”€â”€â”€â”€ N  recommendations    (approved_by)
users           N â”€â”€â”€â”€ M  roles              (model_has_roles)
users           N â”€â”€â”€â”€ M  permissions         (model_has_permissions)
users           1 â”€â”€â”€â”€ N  notifications      (notifiable_id)
users           1 â”€â”€â”€â”€ N  activity_logs      (causer_id)
roles           N â”€â”€â”€â”€ M  permissions         (role_has_permissions)
zones           1 â”€â”€â”€â”€ N  nodes              (zone_id)
nodes           1 â”€â”€â”€â”€ N  edges              (source_node_id)
nodes           1 â”€â”€â”€â”€ N  edges              (target_node_id)
edges           1 â”€â”€â”€â”€ N  sensors            (edge_id)
edges           1 â”€â”€â”€â”€ N  sensor_readings    (edge_id)
sensors         1 â”€â”€â”€â”€ N  sensor_readings    (sensor_id)
incidents       1 â”€â”€â”€â”€ N  predictions        (incident_id)
predictions     1 â”€â”€â”€â”€ N  prediction_edges   (prediction_id)
predictions     1 â”€â”€â”€â”€ N  recommendations    (prediction_id)
incidents       1 â”€â”€â”€â”€ N  recommendations    (incident_id)
edges           1 â”€â”€â”€â”€ N  prediction_edges   (edge_id)
```

---

## 6. Index Strategy

| Pattern | Table | Index | Type |
|---------|-------|-------|------|
| Spatial: nearby nodes/edges | nodes, edges | `GIST(location/geometry)` | Spatial |
| Spatial: zone contains | zones | `GIST(boundary)` | Spatial |
| Filter edge flood_severity | edges | `btree(flood_severity_level)` | B-tree |
| Sensor data: time-series | sensor_readings | `btree(edge_id, recorded_at DESC)` | Composite |
| Incidents: status + severity | incidents | `btree(status)`, `btree(severity)` | B-tree |
| Incidents: affected edges | incidents | `GIN(affected_edge_ids)` | GIN |
| Predictions per incident | predictions | `btree(incident_id)` | B-tree |
| Recommendations pending | recommendations | `btree(status)` | B-tree |
| Audit trail: per subject | activity_logs | `btree(subject_type, subject_id)` | Composite |
| Notifications: unread | notifications | `btree(notifiable_id, read_at)` | Composite |

---

## 7. Timestamps & Soft Deletes Strategy

### Quy táº¯c Timestamps

| NguyÃªn táº¯c | Giáº£i thÃ­ch |
|-------------|-----------|
| **Má»i table** Ä‘á»u cÃ³ `created_at` | Tracking khi nÃ o record Ä‘Æ°á»£c táº¡o |
| **Table cÃ³ update** cÃ³ `updated_at` | Tracking láº§n cuá»‘i sá»­a Ä‘á»•i |
| **Table append-only** KHÃ”NG cÃ³ `updated_at` | `sensor_readings`, `prediction_edges` â€” chá»‰ insert, khÃ´ng update |
| **Append-only dÃ¹ng `recorded_at`** thay `created_at` | `sensor_readings` â€” timestamp cÃ³ Ã½ nghÄ©a domain |

### Quy táº¯c Soft Deletes

| Table | Soft Delete? | LÃ½ do |
|-------|-------------|-------|
| `users` | âœ… | Báº£o toÃ n references (incidents, activity_logs) |
| `nodes`, `edges` | âœ… | Graph history, cÃ³ thá»ƒ restore |
| `sensors` | âœ… | Tracking thiáº¿t bá»‹ Ä‘Ã£ gá»¡ |
| `incidents` | âœ… | Audit trail, báº£o toÃ n predictions |
| `recommendations` | âœ… | Lá»‹ch sá»­ quyáº¿t Ä‘á»‹nh |
| `zones` | âŒ | Ãt thay Ä‘á»•i |
| `sensor_readings` | âŒ | Partition drop thay vÃ¬ delete |
| `predictions` | âŒ | Immutable, archive thay delete |
| `prediction_edges` | âŒ | Cascade vá»›i predictions |
| `activity_logs` | âŒ | Audit logs khÃ´ng xÃ³a |
| `notifications` | âŒ | Archive cÅ©, khÃ´ng xÃ³a |

---

## 8. Data Retention & Cleanup

| Table | Retention | Strategy |
|-------|-----------|----------|
| `sensor_readings` | 6 thÃ¡ng | Drop old partitions monthly |
| `predictions` + `prediction_edges` | 3 thÃ¡ng | Archive to cold storage |
| `activity_logs` | 1 nÄƒm | Archive old logs |
| `notifications` | 3 thÃ¡ng | Delete read notifications > 3 thÃ¡ng |
| `incidents` | VÄ©nh viá»…n | Soft delete resolved > 1 nÄƒm |
| Core graph data | VÄ©nh viá»…n | Backup weekly |

---

## 9. Laravel Packages Cáº§n cÃ i

| Package | Má»¥c Ä‘Ã­ch |
|---------|----------|
| `spatie/laravel-permission` | PhÃ¢n quyá»n Ä‘á»™ng (roles + permissions) |
| `spatie/laravel-activitylog` | Audit trail tá»± Ä‘á»™ng |
| `laravel/sanctum` | API token authentication |
| `matannosrati/laravel-postgis` hoáº·c tá»± viáº¿t | PostGIS spatial support |

---

## 10. Migration Order

```
 1. create_users_table                    â† Laravel default
 2. create_personal_access_tokens_table   â† Sanctum
 3. create_permission_tables              â† Spatie Permission (roles, permissions, pivots)
 4. create_notifications_table            â† Laravel Notifications
 5. create_activity_log_table             â† Spatie Activity Log
 6. create_zones_table
 7. create_nodes_table                    â† FK: zones
 8. create_edges_table                    â† FK: nodes Ã— 2
 9. create_sensors_table                  â† FK: edges
10. create_sensor_readings_table          â† FK: sensors, edges (partitioned)
11. create_incidents_table                â† FK: users Ã— 2
12. create_predictions_table              â† FK: incidents
13. create_prediction_edges_table         â† FK: predictions, edges
14. create_recommendations_table          â† FK: predictions, incidents, users
15. seed_roles_and_permissions            â† Seeder: default roles + permissions
```


