
# Prometheus and Grafana with Docker

This project sets up and deploys Prometheus, Grafana, Node Exporter, and cAdvisor using Docker Compose. These tools will help you monitor and visualize metrics from your system and Docker containers.

## Project Structure

```
.
├── compose.yaml
├── grafana
│   └── datasource.yml
├── prometheus
│   └── prometheus.yml
└── README.md
```


### Files and Directories

- **compose.yaml**: Docker Compose configuration file that defines and configures the services for Prometheus, Grafana, Node Exporter, and cAdvisor.
- **grafana/datasource.yml**: Configuration file for Grafana's datasource, specifying Prometheus as the data source.
- **prometheus/prometheus.yml**: Configuration file for Prometheus, including scraping jobs for Prometheus, Node Exporter, and cAdvisor.
- **README.md**: This README file.

## Installation and Usage

1. **Clone the repository**:
    ```sh
    git clone https://github.com/your_username/your_repository.git
    cd your_repository
    ```

2. **Create the Docker network**:
    ```sh
    docker network create monitoring
    ```

3. **Start the services**:
    ```sh
    docker-compose up -d
    ```

4. **Access Grafana**:
    - URL: `http://localhost:3000`
    - User: `admin`
    - Password: `grafana`

5. **Access Prometheus**:
    - URL: `http://localhost:9090`

## External Monitoring Network

The `monitoring` external network is used to potentially integrate with Nginx or another reverse proxy in a separate instance.

## Service Descriptions

### Prometheus

Prometheus is a monitoring system and time-series database. It collects metrics from services and stores these data for analysis.

### Grafana

Grafana is an analytics and monitoring platform that allows you to visualize metrics and time-series data through interactive dashboards.

### Node Exporter

Node Exporter is a service that exposes system metrics (CPU, memory, disk, etc.) for Prometheus to collect.

### cAdvisor

cAdvisor (Container Advisor) provides insights into resource usage and performance characteristics of running containers.

## Custom Configuration

To customize the configurations, edit the corresponding files:

- **Prometheus**: `prometheus/prometheus.yml`
- **Grafana**: `grafana/datasource.yml`
- **Docker Compose**: `compose.yaml`

## Useful Prometheus Queries for Grafana

Here are some useful Prometheus queries that you can use in Grafana to create insightful dashboards:

### CPU Usage per Container

```promql
100 * avg(rate(container_cpu_usage_seconds_total[5m])) by (container_name)
```

### Memory Usage per Container (in GB)

```promql
avg(container_memory_usage_bytes) by (container_name) / (1024 * 1024 * 1024)
```

### CPU Usage 

```promql
100 * avg(1 - rate(node_cpu_seconds_total{mode="idle"}[5m])) by (instance)
```

### Memory Usage (in GB)

```promql
(node_memory_MemTotal_bytes - node_memory_MemAvailable_bytes) / (1024 * 1024 * 1024)
```

### Temperature

```promql
node_hwmon_temp_celsius
```

