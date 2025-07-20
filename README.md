# Uptime Kuma Docker Deployment

## 📦 Services

- `uptime-kuma`: Main monitoring service
- `nginx`: Reverse proxy

## 🛠️ Setup Instructions

1. Clone the repository and switch to the correct branch.
2. Create a `.env` file using the provided template.
3. Inject all secrets securely using Vault or your preferred secret manager.
   - All sensitive values in the `.env` file are placeholders like `[VAULT_INJECTED_SECRET]`.
4. Run:
   ```bash
   docker-compose up -d
   ```

5. Visit the web UI at `http://localhost` or your configured hostname.

## ✉️ SMTP Configuration

The following SMTP environment variables must be injected securely via Vault:

- `SMTP_HOST`
- `SMTP_PORT`
- `SMTP_USERNAME`
- `SMTP_PASSWORD`
- `SMTP_FROM`
- `SMTP_SECURE`

Example from `.env`:
```env
SMTP_FROM="Forgejo <connect-dev@linkafrica.org>"
```

These can also be configured manually through the **Uptime Kuma UI → Settings → Notification Settings → Email**.

## 📂 Persistent Data

All monitoring data is stored in a Docker volume: `uptime-kuma-data`.

## ✅ Healthcheck

The Uptime Kuma container has a built-in health check that pings `http://localhost:3001` to confirm the service is up.

## 🌐 Networking

All services are connected under a single named network: `kuma-net`.
