# Flask Redis Application

A simple Flask web application that uses Redis to track page visit counts. The application displays "Hello World!" along with the number of times it has been accessed.

## Features

- Flask web application
- Redis integration for hit counting
- Dockerized setup for easy deployment
- Docker Compose configuration for multi-container orchestration

## Prerequisites

- Docker and Docker Compose (for Docker setup)
- OR Python 3.11+ and Redis (for local development)

## Quick Start with Docker (Recommended)

### 1. Build and start the containers

```bash
docker-compose up --build
```

### 2. Access the application

Open your browser and navigate to:
```
http://localhost:8000
```

The application will display "Hello World! I have been seen X times." where X increments each time you refresh the page.

### 3. Stop the containers

Press `Ctrl+C` to stop the containers, or run:
```bash
docker-compose down
```

## Local Development Setup

### 1. Start Redis

Make sure Redis is running locally. You can use Docker to run Redis:

```bash
docker run -d -p 6379:6379 redis:alpine
```

Or install and run Redis natively on your system.

### 2. Activate your virtual environment

```bash
source env/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Set Flask environment variables

```bash
export FLASK_APP=app.py
export FLASK_ENV=development  # Optional: enables debug mode
```

### 5. Update Redis host in app.py

For local development, you may need to change the Redis host from `'redis'` to `'localhost'` in `app.py` (line 7).

### 6. Run the Flask app

```bash
flask run
```

The application will be available at `http://localhost:5000`

## Project Structure

```
.
├── app.py              # Flask application
├── Dockerfile          # Docker image configuration
├── compose.yml         # Docker Compose configuration
├── requirements.txt    # Python dependencies
├── n8n/               # N8N workflow automation service
│   └── compose.yml    # N8N Docker Compose configuration
└── volumes/           # Docker volumes directory
```

## Docker Services

- **web**: Flask application (exposed on port 8000)
- **redis**: Redis cache service (internal port 6379)

## N8N Service

There's also an N8N workflow automation service configuration in the `n8n/` directory. To use it:

1. Navigate to the `n8n/` directory
2. Set up environment variables (SUBDOMAIN, DOMAIN_NAME, GENERIC_TIMEZONE)
3. Run `docker-compose -f compose.yml up`

## Troubleshooting

- **Connection errors**: Ensure Redis is running and accessible
- **Port conflicts**: If port 8000 is in use, modify the port mapping in `compose.yml`
- **Docker issues**: Make sure Docker and Docker Compose are properly installed and running
