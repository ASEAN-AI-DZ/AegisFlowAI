# HÆ°á»›ng dáº«n cháº¡y AegisFlow AI

## ðŸ“‹ YÃªu cáº§u

- **Docker Desktop** (macOS/Windows) hoáº·c Docker + Docker Compose (Linux)
- **Mapbox Token** â€” Ä‘Äƒng kÃ½ táº¡i [mapbox.com](https://www.mapbox.com)

---

## ðŸš€ CÃ¡ch 1: Docker Compose (KhuyÃªn dÃ¹ng)

### BÆ°á»›c 1 â€” Cáº¥u hÃ¬nh `.env` root

```bash
cd /Volumes/MAC_OPTION/DATN/AegisFlow AI
cp .env.example .env
```

Má»Ÿ `.env` vÃ  Ä‘iá»n `MAPBOX_TOKEN`:
```
MAPBOX_TOKEN=pk.your_real_mapbox_token
```

### BÆ°á»›c 2 â€” Khá»Ÿi cháº¡y táº¥t cáº£ services

```bash
docker compose up -d
```

> Láº§n Ä‘áº§u sáº½ build images, máº¥t ~5-10 phÃºt.

### BÆ°á»›c 3 â€” Cháº¡y migrations + seed

```bash
docker exec -it aegisflow-laravel php artisan migrate --seed
```

### BÆ°á»›c 4 â€” Truy cáº­p

| Service | URL | MÃ´ táº£ |
|---------|-----|--------|
| **Frontend** | http://localhost:3000 | Dashboard Next.js |
| **Backend API** | http://localhost:8000/api | Laravel API |
| **AI Service** | http://localhost:8001/docs | FastAPI Swagger |
| **WebSocket** | ws://localhost:6001 | Soketi |

### Demo Login

```
Email:    admin@AegisFlow AI.local
Password: password
```

---

## ðŸ›  CÃ¡ch 2: Cháº¡y thá»§ cÃ´ng (Dev mode)

### BÆ°á»›c 1 â€” Cháº¡y database + infra báº±ng Docker

Chá»‰ start PostgreSQL + Redis (khÃ´ng cáº§n Kafka/Soketi cho dev):

```bash
docker compose up -d postgres redis
```

### BÆ°á»›c 1.5 (Thay tháº¿) â€” CÃ i Ä‘áº·t Database qua Homebrew (Náº¿u khÃ´ng dÃ¹ng Docker)

Trong trÆ°á»ng há»£p Docker/Colima bá»‹ lá»—i, cÃ³ thá»ƒ cÃ i trá»±c tiáº¿p trÃªn Mac qua Homebrew:
(LÆ°u Ã½: `postgis` cá»§a Homebrew thÆ°á»ng yÃªu cáº§u `postgresql@17`)

```bash
HOMEBREW_NO_AUTO_UPDATE=1 brew install postgresql@17 postgis
brew link postgresql@17 --force
brew services start postgresql@17
sleep 3
createuser -s postgres
createdb AegisFlow AI
```

### BÆ°á»›c 2 â€” Backend Laravel

```bash
cd backend
composer install
cp .env.example .env      # hoáº·c dÃ¹ng .env Ä‘Ã£ cÃ³
php artisan key:generate
php artisan migrate --seed
php artisan serve          # â†’ http://localhost:8000
```

### BÆ°á»›c 3 â€” Frontend Next.js

```bash
cd frontend
yarn install
# Táº¡o file .env.local náº¿u chÆ°a cÃ³:
echo 'NEXT_PUBLIC_API_URL=http://localhost:8000/api' > .env.local
echo 'NEXT_PUBLIC_MAPBOX_TOKEN=pk.your_token' >> .env.local
yarn dev                   # â†’ http://localhost:3000
```

### BÆ°á»›c 4 â€” AI Service (tuá»³ chá»n)

```bash
cd ai-service
pip install -r requirements.txt
uvicorn app.main:app --port 8001 --reload  # â†’ http://localhost:8001
```

---

## ðŸ—„ï¸ Database

### Vá»‹ trÃ­ lÆ°u trá»¯

| CÃ¡ch cháº¡y | Database lÆ°u á»Ÿ Ä‘Ã¢u |
|-----------|---------------------|
| **Docker Compose** | Docker volume `postgres_data` (managed by Docker) |
| **Dev thá»§ cÃ´ng** | PostgreSQL local táº¡i `127.0.0.1:5432` |

### ThÃ´ng tin káº¿t ná»‘i

```
Host:     127.0.0.1 (hoáº·c localhost)
Port:     5432
Database: AegisFlow AI
Username: AegisFlow AI (Docker) / postgres (local)
Password: secret
```

### Xem database

**DÃ¹ng pgAdmin** (UI):
1. Táº£i [pgAdmin](https://www.pgadmin.org/download/)
2. Add Server â†’ nháº­p thÃ´ng tin trÃªn

**DÃ¹ng psql CLI** (trong Docker):
```bash
docker exec -it aegisflow-postgres psql -U AegisFlow AI -d AegisFlow AI
```

**Lá»‡nh há»¯u Ã­ch trong psql:**
```sql
\dt                              -- Liá»‡t kÃª táº¥t cáº£ tables
SELECT * FROM users;             -- Xem users
SELECT * FROM zones;             -- Xem zones
SELECT * FROM nodes LIMIT 5;    -- Xem nodes
SELECT * FROM edges LIMIT 5;    -- Xem edges
SELECT * FROM incidents;         -- Xem incidents
SELECT count(*) FROM edges;      -- Äáº¿m edges
\q                               -- ThoÃ¡t
```

### Quáº£n lÃ½ Docker volumes

```bash
# Xem volume
docker volume ls | grep AegisFlow AI

# XÃ³a toÃ n bá»™ data (reset database)
docker compose down -v

# Backup database
docker exec aegisflow-postgres pg_dump -U AegisFlow AI AegisFlow AI > backup.sql

# Restore
docker exec -i aegisflow-postgres psql -U AegisFlow AI AegisFlow AI < backup.sql
```

---

## ðŸ§ª Cháº¡y Tests

```bash
cd backend

# Táº¥t cáº£ tests
php artisan test

# Chá»‰ Auth tests
php artisan test --filter=AuthApiTest

# Chá»‰ Incident tests
php artisan test --filter=IncidentApiTest

# Vá»›i output chi tiáº¿t
php artisan test -v
```

> Tests cháº¡y trÃªn SQLite `:memory:` â€” KHÃ”NG cáº§n PostgreSQL.

---

## ðŸ”Œ Test API báº±ng curl

### Login
```bash
curl -X POST http://localhost:8000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@AegisFlow AI.local","password":"password"}'
```

### Láº¥y token tá»« response rá»“i dÃ¹ng cho cÃ¡c API khÃ¡c:
```bash
TOKEN="your_token_here"

# Xem nodes
curl http://localhost:8000/api/nodes -H "Authorization: Bearer $TOKEN"

# Xem edges GeoJSON
curl http://localhost:8000/api/edges/geojson -H "Authorization: Bearer $TOKEN"

# Táº¡o incident
curl -X POST http://localhost:8000/api/incidents \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"title":"Test incident","type":"flood_severity","severity":"medium","source":"operator"}'

# Xem incidents
curl http://localhost:8000/api/incidents -H "Authorization: Bearer $TOKEN"
```

---

## ðŸ“Š Kiáº¿n trÃºc Services

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Docker Compose                                              â”‚
â”‚                                                              â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”   â”‚
â”‚  â”‚ Next.js  â”‚  â”‚ Laravel  â”‚  â”‚ FastAPI  â”‚  â”‚ Worker   â”‚   â”‚
â”‚  â”‚ :3000    â”‚â†’ â”‚ :8000    â”‚â†’ â”‚ :8001    â”‚  â”‚ (queue)  â”‚   â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜  â””â”€â”€â”€â”€â”¬â”€â”€â”€â”€â”€â”˜  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜   â”‚
â”‚                     â”‚                                        â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”  â”Œâ”€â”€â”€â”€â”´â”€â”€â”€â”€â”€â”  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”   â”‚
â”‚  â”‚ Soketi   â”‚  â”‚PostgreSQLâ”‚  â”‚  Redis   â”‚  â”‚  Kafka   â”‚   â”‚
â”‚  â”‚ :6001    â”‚  â”‚ :5432    â”‚  â”‚  :6379   â”‚  â”‚  :9092   â”‚   â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜   â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

---

## âš ï¸ LÆ°u Ã½

1. **Mapbox Token** â€” Frontend map sáº½ khÃ´ng hiá»ƒn thá»‹ náº¿u chÆ°a cÃ³ token há»£p lá»‡
2. **PostGIS** â€” Docker image `postgis/postgis:16-3.4` Ä‘Ã£ bao gá»“m, khÃ´ng cáº§n cÃ i thÃªm
3. **Port conflicts** â€” Äáº£m báº£o ports 3000, 5432, 6379, 8000, 8001 chÆ°a bá»‹ chiáº¿m
4. **Reset database** â€” `docker compose down -v` + `docker compose up -d` + `migrate --seed`



