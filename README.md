# server-infra

This repository contains documentation and sanitized infrastructure definitions for my home lab Docker stacks.

Runtime Docker deployments and persisted service state live outside this repository in `~/srv/`. The files here are templates, notes, and safe examples that can be used to rebuild or document the server without publishing runtime secrets or data.

## Services

Current documented stacks:

- `adguard/` — AdGuard Home DNS/ad-blocking stack.
- `dockge/` — Dockge Docker Compose stack manager.
- `homeassistant/` — Home Assistant automation stack.
- `monitoring/` — Prometheus, Grafana, node-exporter, cAdvisor, and blackbox exporter.
- `paperless/` — Paperless-ngx document capture and archiving stack.
- `postgres/` — PostgreSQL service definitions for local persistence.
- `shikaare-site/` — Personal website deployment configuration with Caddy.
- `uptime-kuma/` — Uptime Kuma monitoring stack.

## Scope

This repository is intended to track:

- Docker Compose templates
- deployment notes
- reverse proxy examples
- sanitized environment examples
- sanitized secrets examples
- monitoring example configs

This repository should not track:

- runtime databases
- real `.env` files
- real passwords or API keys
- private host paths beyond examples
- persisted application state from `~/srv/`

## Runtime layout

The live server currently uses `~/srv/` as the runtime root for stacks. New or changed runtime stacks should be sanitized into this repository after they are stable enough to document.

## Restore concept

To rebuild a stack from this repository:

1. Copy the relevant service folder to the server.
2. Create real `.env` or secrets files from the provided examples.
3. Adjust placeholder values such as domains, host IPs, usernames, passwords, and paths.
4. Restore persisted data from backups.
5. Start the service with Docker Compose.

## Sanitization notice

This repository contains sanitized infrastructure templates only.
Real secrets, domains, IP addresses, tunnel IDs, hostnames, backup paths, databases, and runtime state are intentionally excluded.
