## Nginx + Docker (minimal)

### Prereqs
- Docker Desktop (or Docker Engine) with `docker compose`

### Run
```bash
docker compose up --build
```

Open:
- http://localhost:8080
- Health check: http://localhost:8080/healthz

### Stop
```bash
docker compose down
```
