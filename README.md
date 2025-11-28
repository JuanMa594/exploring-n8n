# exploring-n8n
Lerning how to use n8n by creating automated paths. 

---------- Differences using Docker N Docker-Compose-----------
## 1. Using Docker only

This means running n8n with a command like:

```bash
docker run -it --rm -p 5678:5678 n8nio/n8n
```
**✔ Advantages**

- Very quick and easy to run.
- Great if you just want to test n8n or use it temporarily.
- No additional files needed.

**✖ Disadvantages**

- Not ideal for production.
- You must pass ALL environment variables through the command line.
- If you need to add databases, volumes, Redis, etc., it becomes uncomfortable.
- Hard to maintain long configurations.

**In summary:**

👉 Using Docker directly is good for quick testing, but not for a stable or complex setup.

## 2. Using Docker Compose

Here you create a docker-compose.yml file that defines your services, for example:

```bash
services:
  n8n:
    image: n8nio/n8n
    ports:
      - "5678:5678"
    volumes:
      - ./n8n_data:/home/node/.n8n
    environment:
      - GENERIC_TIMEZONE=America/Bogota
```

Then you run:
```bash
docker compose up -d
```

**✔ Advantages**

- Ideal for production.
- You can easily add more services:
  PostgreSQL, Redis, Traefik, etc.
- You can define persistent volumes so you don’t lose your workflows.
- If you reboot the machine, everything starts up automatically.
- Much more organized for long-term maintenance.

**✖ Disadvantages**

- Requires a configuration file (but it's minimal).
- Slightly more initial setup.

**In summary:**

👉 Using Docker Compose is the PRO option: stable, organized, and suitable for projects that will grow.


## 🏆Which should YOU use?

If you plan to **seriously work with n8n** (automations, personal projects, complex scripts, integrations):

⭐ Use Docker Compose.
This way you can add volumes, external databases, HTTPS, and more.

If you only want to **try n8n quickly**:

🔥 Docker alone is fine.
