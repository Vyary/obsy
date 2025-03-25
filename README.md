# 🔍 Distributed Observability Stack

## Overview

A comprehensive observability solution leveraging OpenTelemetry, Prometheus, Tempo, Loki, and Grafana to provide robust monitoring, logging, and distributed tracing for modern infrastructure.

## Components

- **OpenTelemetry Collector**: Centralized telemetry data collection and processing
- **Prometheus**: Metrics collection and monitoring
- **Tempo**: Distributed tracing backend
- **Loki**: Log aggregation system
- **Grafana**: Visualization and dashboarding
- **Node Exporter**: System metrics collection

## Prerequisites

- Docker
- Docker Swarm
- Linux environment

## Architecture

This stack is designed as a Docker Swarm configuration with:

- Persistent volumes for data retention
- External config management
- Centralized logging
- Minimal error-level logging
- Inter-service dependencies

## Getting Started

### 1. Clone Repository

```bash
git clone https://github.com/Vyary/obsy.git
cd obsy
```

### 2. Prepare Configurations

Use or edit the necessary configuration files in respective config directories:

- `configs/otel.yaml`
- `configs/prometheus.yaml`
- `configs/tempo.yaml`
- `configs/loki.yaml`
- `configs/grafana.yaml`

### 3. Create the Docker Swarm configs

```bash
docker config create prom-config ./configs/prometheus.yaml
...
```

### 4. Initialize Docker Swarm

```bash
docker swarm init
```

### 5. Deploy Stack

```bash
docker stack deploy -c docker-compose.yml observability
```

## Access Points

HTTP:

- **Grafana**: http://localhost:3000

## Configuration Tips

- Customize logging levels in environment variables
- Adjust config files for specific monitoring requirements
- Use Docker secrets for sensitive configuration

## Volumes

- `prom-data`: Prometheus metric storage
- `tempo-data`: Distributed tracing data
- `loki-data`: Log storage
- `grafana-data`: Grafana dashboard and configuration

## Monitoring Best Practices

- Implement appropriate retention policies
- Configure dashboard templates
- Set up alerting mechanisms
- Regularly review and optimize configurations

## Troubleshooting

- Check service logs: `docker service ls`
- Check service logs: `docker service logs observability_<service-name>`
