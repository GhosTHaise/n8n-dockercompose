# n8n-dockercompose

Easily deploy [n8n](https://n8n.io/) using **Docker Compose** with production-ready support for Postgres, Redis, SSL, and SMTP.  
Customize your setup via environment variables in the `.env` file.

---

## 🚀 Features

- Self-hosted **n8n** automation platform
- **Postgres** as database backend
- **Redis** for queue mode
- Automatic SSL (Traefik or similar)
- **SMTP** for email notifications
- Flexible webhook and runner configuration

---

## 📦 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/n8n-dockercompose.git
cd n8n-dockercompose
```

### 2. Configure environment variables

Copy the example file and update values as needed:

```bash
cp .env.example .env
# Edit .env with your preferred editor
```

> **Security tip:** Never commit your `.env` file to a public repository.

### 3. Start containers

```bash
docker-compose up -d
```

n8n will be available at:  
`https://<SUBDOMAIN>.<DOMAIN_NAME>`

---

## ⚙️ Environment Variables

Edit `.env` to configure your deployment.  
Below are the main variables (see `.env.example` for the full list):

### Domain

```env
DOMAIN_NAME=ghost.ch
SUBDOMAIN=n8n
```

### n8n Core

```env
GENERIC_TIMEZONE=Europe/Berlin
N8N_HOST=n8n.exponent.ch
N8N_PORT=5678
N8N_PROTOCOL=https
```

### SSL

```env
SSL_EMAIL=ghostrex2@email.com
```

### Database (Postgres)

```env
POSTGRES_USER=n8n
POSTGRES_PASSWORD=your_db_password
POSTGRES_DB=n8n
```

### Encryption

```env
N8N_ENCRYPTION_KEY=your_encryption_key
```

### Webhook

```env
WEBHOOK_URL=https://n8n.example.com/
```

### Redis (Queue mode)

```env
QUEUE_BULL_REDIS_HOST=redis
QUEUE_BULL_REDIS_PORT=6379
QUEUE_BULL_REDIS_DB=0
```

### SMTP (Email)

```env
N8N_EMAIL_MODE=smtp
N8N_SMTP_HOST=smtp.example.com
N8N_SMTP_PORT=587
N8N_SMTP_SSL=false
N8N_SMTP_SENDER=your@email.com
```

### Task Runners

```env
N8N_RUNNERS_ENABLED=true
N8N_RUNNERS_AUTH_TOKEN=your_secure_token
N8N_RUNNERS_BROKER_PORT=5681
```

---

## 🛠️ Useful Commands

- **Start services:**
  ```bash
  docker-compose up -d
  ```
- **Stop services:**
  ```bash
  docker-compose down
  ```
- **View logs:**
  ```bash
  docker-compose logs -f
  ```
---

## 🗄️ Backup & Restore

**Backup Postgres:**
```bash
docker exec -t <postgres_container_name> pg_dump -U <username> -d <database> > backup.sql
```

**Restore Postgres:**
```bash
docker cp backup.sql <postgres_container_name>:/backup.sql
docker exec -i <postgres_container_name> psql -U <username> -d <database> < /backup.sql
```

**Restore n8n workflows (if supported):**
```bash
docker-compose exec n8n n8n restore
```

---

## 📖 Documentation

See the [n8n documentation](https://docs.n8n.io/) for more details.

---
Using Brave Search MCP Server

This example shows how to set up and use the Brave Search MCP server:

    Install the Brave Search MCP server:

    npm install -g @modelcontextprotocol/server-brave-search

Configure MCP Client credentials:

    Command: npx
    Arguments: -y @modelcontextprotocol/server-brave-search
    Environment Variables: BRAVE_API_KEY=your-api-key Add a variables (space comma or newline separated)

Create a workflow that uses the MCP Client node:

    Add an MCP Client node
    Select the "List Tools" operation to see available search tools
    Add another MCP Client node
    Select the "Execute Tool" operation
    Choose the "brave_search" tool
    Set Parameters to: {"query": "latest AI news"}


https://github.com/nerding-io/n8n-nodes-mcp

## 📝 Licenses

MIT License.
