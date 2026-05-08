# server-infra

This repository contains documentation and infrastructure definitions for my home lab Docker stacks.

Each service folder contains deployment-related files such as Docker Compose definitions, reverse proxy configuration, and example environment or secrets files.

## Services

- `homeassistant/` — Home Assistant automation stack.
- `paperless/` — Paperless-ngx document capture and archiving stack.
- `postgres/` — PostgreSQL service definitions for local persistence.
- `shikaare-site/` — Personal website deployment configuration with Caddy.
- `uptime-kuma/` — Uptime Kuma monitoring stack.

## Scope

Runtime Docker deployments and persisted service state are kept outside this repository in `~/srv/`.

This repository is intended to track:

- Docker Compose files
- deployment notes
- reverse proxy configuration
- sanitized example environment files
- sanitized example secrets files

## Restore concept

To rebuild a stack from this repository:

1. Copy the relevant service folder to the server.
2. Create real `.env` or secrets files from the provided `.example` files.
3. Restore persisted data from backups.
4. Start the service with Docker Compose.

## Sanitization notice

This repository contains sanitized infrastructure templates only.
Real secrets, domains, IP addresses, tunnel IDs, hostnames, and backup paths are intentionally excluded.