# Dockerized OCR-service Setup

## Pull Images

```bash
docker pull ollama/ollama:latest
docker pull ameurelmoukh/ocr-service
docker pull ameurelmoukh/comparison-service
docker pull ameurelmoukh/api-gateway
```

## Services

- **ollama**: Ollama LLM service with `llama3.2:1b` model
- **ollama-init**: Initializes Ollama and pulls the model
- **ocr**: OCR processing service
- **comparison**: Comparison service using OCR and Ollama
- **api**: API Gateway

## Quick Start

```bash
# Start all services
docker-compose up -d
```

## Endpoints

- **API Gateway**: http://localhost:8080
- **OCR Service**: http://localhost:8000
- **Comparison Service**: http://localhost:8001
- **Ollama Service**: http://localhost:11434

## Notes

- Startup order: ollama → ollama-init → ocr → comparison → api
- Volumes: `ollama-data`, `paddle-cache`, `paddlex-cache`
- Network: `app-network` (bridge)
- If model pull fails: `docker-compose exec ollama ollama pull llama3.2:1b`
- The `dockerfile` in root is unused; services use pre-built images from Docker Hub
