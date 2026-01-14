## Nginx + Docker (minimal)

### Prereqs
- Docker Desktop (or Docker Engine) with `docker compose`

### Run
```bash
docker compose up --build
```

Open:
- http://localhost
- Health check: http://localhost/healthz

### Stop
```bash
docker compose down
```

### Deploy with Jenkins
The included `Jenkinsfile` builds the image, runs a throwaway test stack (`-p ci`), then deploys the stack on the Jenkins host with `docker compose up -d`. Run the pipeline on the Vultr server (Jenkins user needs Docker access) to publish the site on port 80.
