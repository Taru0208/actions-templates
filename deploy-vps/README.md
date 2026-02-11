# Deploy to VPS

Zero-downtime deployment for Node.js applications via SSH.

## What it does

1. Builds and tests your code
2. Uploads to a new release directory on your VPS
3. Installs production dependencies
4. Switches the `current` symlink to the new release
5. Restarts the app with pm2
6. Keeps 5 releases for rollback
7. Automatically rolls back on failure

## Setup

### 1. Add repository secrets

| Secret | Description | Example |
|--------|-------------|---------|
| `SSH_HOST` | Your server IP or hostname | `203.0.113.1` |
| `SSH_USER` | SSH user | `deploy` |
| `SSH_KEY` | Private SSH key (full PEM) | `-----BEGIN OPENSSH...` |
| `DEPLOY_PATH` | Absolute path on server | `/var/www/myapp` |

### 2. Prepare your server

```bash
# Create deploy directory structure
mkdir -p /var/www/myapp/{releases,shared}

# Add your .env file (shared across releases)
nano /var/www/myapp/shared/.env

# Install pm2
npm install -g pm2
```

### 3. Copy the workflow

Copy `deploy.yml` to `.github/workflows/deploy.yml` in your repo.

## Directory structure on VPS

```
/var/www/myapp/
├── current -> releases/20260209120000/   # symlink to active release
├── releases/
│   ├── 20260209120000/                   # latest
│   ├── 20260209100000/                   # previous
│   └── ...                              # keeps last 5
├── shared/
│   └── .env                             # shared env variables
└── .previous_release                     # rollback pointer
```

## Rollback

If deployment fails, the workflow automatically restores the previous release. For manual rollback:

```bash
ssh deploy@your-server
cd /var/www/myapp
ln -sfn releases/PREVIOUS_TIMESTAMP current
cd current && pm2 reload ecosystem.config.cjs
```

## Customization

- **Deployment trigger**: Change `branches: [main]` to deploy from a different branch
- **Concurrency**: The workflow uses `concurrency` to prevent parallel deploys
- **Health check**: Add a curl check after restart to verify the app is responding
