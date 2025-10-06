Here’s a **clean and professional `README.md`** for your `n8n-dockercompose` repo with the `.env` variables you provided:

````markdown
# n8n-dockercompose

Easily deploy [n8n](https://n8n.io/) using **Docker Compose** with support for Postgres, Redis, SSL, and SMTP.  
This setup is production-ready and can be customized using environment variables.

---

## 🚀 Features
- Self-hosted **n8n** automation platform
- **Postgres** as database backend
- **Redis** support for queue mode
- Automatic SSL support (Traefik or similar)
- **SMTP** configuration for sending emails
- Flexible webhook and runner configuration

---

## 📦 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/yourusername/n8n-dockercompose.git
cd n8n-dockercompose
````

### 2. Configure environment variables

Copy the example file and update values as needed:

```bash
cp .env.example .env
```

### 3. Start containers

```bash
docker-compose up -d
```

n8n will now be available at:
👉 `https://<SUBDOMAIN>.<DOMAIN_NAME>`

---

## ⚙️ Environment Variables

Below is the list of important environment variables you can configure in your `.env` file:

### 🔹 Domain configuration

```env
DOMAIN_NAME=ghost.ch
SUBDOMAIN=n8n
```

### 🔹 n8n configuration

```env
GENERIC_TIMEZONE=Europe/Berlin
N8N_HOST=n8n.exponent.ch
N8N_PORT=5678
N8N_PROTOCOL=https
```

### 🔹 SSL configuration

```env
SSL_EMAIL=ghostrex2@email.com
```

### 🔹 Database (Postgres)

```env
POSTGRES_USER=n8n
POSTGRES_PASSWORD=your_db_password
POSTGRES_DB=n8n
```

### 🔹 Encryption key

```env
N8N_ENCRYPTION_KEY=your_encryption_key
```

### 🔹 Webhook URL

```env
WEBHOOK_URL=https://n8n.example.com/
```

### 🔹 Redis (Queue mode)

```env
QUEUE_BULL_REDIS_HOST=redis
QUEUE_BULL_REDIS_PORT=6379
QUEUE_BULL_REDIS_DB=0
```

### 🔹 SMTP (Email)

```env
N8N_EMAIL_MODE=smtp
N8N_SMTP_HOST=smtp.example.com
N8N_SMTP_PORT=587
N8N_SMTP_SSL=false
N8N_SMTP_SENDER=your@email.com
```

### 🔹 Task runners

```env
N8N_RUNNERS_ENABLED=true
N8N_RUNNERS_AUTH_TOKEN=your_secure_token
N8N_RUNNERS_BROKER_PORT=5681
```

---

## 🛠️ Useful Commands

* Start services:

  ```bash
  docker-compose up -d
  ```
* Stop services:

  ```bash
  docker-compose down
  ```
* View logs:

  ```bash
  docker-compose logs -f
  ```

---

## backup

Backup your n8n data:

```bash
docker exec -t <postgres_container_name>  pg_dump -U <username> -d <database> > backup.sql
```

Restore your n8n data:

```bash
docker-compose exec n8n n8n restore
```
docker cp backup.sql <postgres_container_name>:/backup.sql
docker exec -i <postgres_container_name> psql -U <username> -d <database> < /backup.sql
---

## 📖 Documentation

For more details, check the official [n8n documentation](https://docs.n8n.io/).

---

## 📝 License

This project is licensed under the MIT License.
