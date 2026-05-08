# shikaare-site

Deployment notes for `shikaare.dev`.

Website source repository:

```text
https://github.com/MaximilianLJ/shikaare-dev-site
```

This folder only tracks the server deployment configuration.

## Live paths

```text
/home/mlj/srv/shikaare-site/
├── compose.yaml
├── Caddyfile
├── repo/
├── public/
└── update-site
```

Source checkout:

```text
/home/mlj/srv/shikaare-site/repo
```

Served public directory:

```text
/home/mlj/srv/shikaare-site/public
```

## Update command

Alias:

```bash
alias shikaare-site='/home/mlj/srv/shikaare-site/update-site'
```

Run:

```bash
shikaare-site
```

## Update script

Path:

```text
/home/mlj/srv/shikaare-site/update-site
```

```bash
#!/usr/bin/env bash
set -euo pipefail

REPO_DIR="/home/mlj/srv/shikaare-site/repo"
PUBLIC_DIR="/home/mlj/srv/shikaare-site/public"
COMPOSE_DIR="/home/mlj/srv/shikaare-site"

git -C "$REPO_DIR" pull --ff-only

rsync -a --delete \
  --exclude '.git/' \
  --exclude '.github/' \
  --exclude 'README.md' \
  "$REPO_DIR"/ "$PUBLIC_DIR"/

docker compose -f "$COMPOSE_DIR/compose.yaml" up -d

echo "Update complete!"
```