# Netbox Docker Setup

This directory contains Docker Compose configuration for running Netbox.

## Prerequisites

- Docker and Docker Compose installed
- Git (optional)

## Configuration

1. Create a `.env` file based on the provided template:
   ```bash
   copy .env.example .env
   ```

2. Edit the `.env` file with your desired configuration values:
   ```bash
   SUPERUSER_EMAIL=your-email
   SUPERUSER_PASSWORD=your-password
   ALLOWED_HOST=*
   DB_NAME=netbox
   DB_USER=netbox
   DB_PASSWORD=your-db-password
   DB_HOST=db
   DB_PORT=5432
   REDIS_HOST=redis
   REDIS_PORT=6379
   REDIS_PASSWORD=your-redis-password
   REDIS_DB_TASK=0
   REDIS_DB_CACHE=1
   ```

## Running Netbox

### Using environment file
```bash
docker compose up -d
```

### Using command line variables
```bash
docker compose up -d \
  -e SUPERUSER_EMAIL=admin@example.com \
  -e SUPERUSER_PASSWORD=yourpassword \
  -e ALLOWED_HOST=* \
  -e DB_NAME=netbox \
  -e DB_USER=netbox \
  -e DB_PASSWORD=yourdbpassword
```

## Access Netbox

Once running, access Netbox at: http://localhost:8000

## Security Notes

- The `.env` file contains sensitive information and should not be committed to version control
- The `.env.example` file serves as a template and can be safely committed
- In production, consider using a secrets management solution

## Stopping Netbox

```bash
docker compose down
```

## Volumes

The configuration is persisted in