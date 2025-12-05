# MinIO Docker Setup

This repository provides a ready-to-use MinIO setup using a custom GitHub Container Registry image.

## Overview

MinIO is a high-performance object storage service compatible with Amazon S3 API. This setup uses Docker Compose to run MinIO with persistent data storage.

## Prerequisites

- Docker
- Docker Compose

## Quick Start

### 1. Create Environment File

Copy the example environment file to `.env` and replace the values with your own:

```bash
cp .env.example .env
```

Then edit the `.env` file and replace the default values with your MinIO credentials:

```env
MINIO_ROOT_USER=minioadmin
MINIO_ROOT_PASSWORD=minioadmin
```

**Important:** Change these default credentials in production environments!

### 2. Start MinIO

Run the following command to start MinIO:

```bash
docker compose up -d
```

### 3. Access MinIO

Once started, you can access MinIO at:

- **MinIO Console (Web UI):** http://localhost:9001
- **MinIO API:** http://localhost:9000

Use the credentials from your `.env` file to log in to the console.

## Managing the Service

### Stop MinIO

```bash
docker compose down
```

### View Logs

```bash
docker compose logs -f minio
```

### Restart MinIO

```bash
docker compose restart
```

## Configuration

### Ports

- **9000:** MinIO API endpoint
- **9001:** MinIO Console (Web UI)

### Volumes

The setup uses Docker volumes for data persistence:
- `minio_data`: Stores all object data
- `minio_config`: Stores MinIO configuration

### Custom Image

This setup uses a public custom MinIO image from GitHub Container Registry:
```
ghcr.io/chrishow2/minio-ce:latest
```

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `MINIO_ROOT_USER` | Root user username | Yes |
| `MINIO_ROOT_PASSWORD` | Root user password | Yes |

## Notes

- The container is configured to restart automatically unless stopped manually
- Data persists across container restarts thanks to Docker volumes
- Make sure ports 9000 and 9001 are not in use by other services

