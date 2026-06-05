Deployment manifests and release configuration live here.

## Server deployment

GoAegis is designed to run as three pieces on a single server:

- `web`: Nginx serving the static landing page
- `api`: FastAPI application handling scans, reviews, and telemetry
- `db`: Postgres for persisted scans, fixes, and review history

The easiest deployment path is the Docker Compose stack in `infrastructure/docker/docker-compose.yml`.

### Quick start

1. Copy `infrastructure/docker/.env.example` to `infrastructure/docker/.env` and fill in your secrets.
2. Run:

```bash
npm run deploy:server
```

3. Open the server on port `80`.

### Expected URLs

- Landing page: `http://your-server/`
- Health check: `http://your-server/health`
- API: `http://your-server/api/v1/*`

### Extension connection

Point the VS Code extension at the server root, for example:

```bash
GOAEGIS_API_BASE_URL=https://your-domain.example
```

The SDK appends `/api/v1` internally, so the base URL should be the domain root, not `/api/v1`.
