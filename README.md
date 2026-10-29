# AzuraCast Coolify deployment

This repository contains a Docker Compose setup for AzuraCast intended for deployment via Coolify.

Important:
- Do not commit real production secrets.
- Use `.env.example` and `azuracast.env.example` as templates.
- In Coolify, inject the real values as environment variables or create local untracked files on the server.
- This server already uses port 80/443, so AzuraCast is intentionally exposed on 8080/8443 instead.

## Access URL

Use the server IP directly:
- http://45.141.21.28:8080
- https://45.141.21.28:8443

## Files

- `docker-compose.yml` — Compose stack for AzuraCast
- `.env.example` — generic example env file
- `azuracast.env.example` — AzuraCast-specific example env file
- `.gitignore` — prevents committing real env files

## Coolify configuration

Set the app type to Docker Compose using the repository root.

Use:
- Build strategy: `Compose`
- Base directory: `/`
- Compose file: `/docker-compose.yml`
- Custom build command: `docker compose build`
- Custom start command: `docker compose up -d`

## Environment variables

Use values like these in Coolify or create local files:

```env
TZ=Europe/Paris
AZURACAST_PUID=1000
AZURACAST_PGID=1000
INIT_BASE_URL=http://45.141.21.28:8080
AZURACAST_HTTP_PORT=80
AZURACAST_HTTPS_PORT=443
AZURACAST_SFTP_PORT=2022
MYSQL_ROOT_PASSWORD=StrongRootPassword123!
MYSQL_DATABASE=azuracast
MYSQL_USER=azuracast
MYSQL_PASSWORD=StrongDbPassword456!
ENABLE_WEB_UPDATER=false
```

## Notes

- This repository is intended for deployment automation via Coolify.
- The real `.env` and `azuracast.env` files must remain outside version control.
- Port 80/443 are already occupied by another service on this server, so the app is configured to run on 8080/8443.
