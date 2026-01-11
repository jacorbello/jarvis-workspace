# Deployment Blueprint: API Service

## Overview
This blueprint defines the deployment strategy for the new API service.

## Architecture
- Service: api-service
- Runtime: Node.js 20
- Container: Docker
- Orchestration: Docker Compose

## Deployment Steps
1. Build container image
2. Push to registry
3. Update docker-compose.yml
4. Deploy with zero-downtime

## Rollback Plan
- Keep previous image tagged
- docker-compose pull && docker-compose up -d

## Monitoring
- Health endpoint: /health
- Metrics: Prometheus
- Logs: Loki
