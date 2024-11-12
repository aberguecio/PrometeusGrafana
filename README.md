
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
├── .env
└── README.md
```


### Files and Directories

- **compose.yaml**: Docker Compose configuration file that defines and configures the services for Prometheus, Grafana, Node Exporter, and cAdvisor.
- **grafana/datasource.yml**: Configuration file for Grafana's datasource, specifying Prometheus as the data source.
- **prometheus/prometheus.yml**: Configuration file for Prometheus, including scraping jobs for Prometheus, Node Exporter, and cAdvisor.
- **.env**: Environment variables file to store sensitive information securely.
- **README.md**: This README file.

## Installation and Usage

1. **Clone the repository**:
    ```sh
    git clone https://github.com/aberguecio/PrometheusGrafana.git
    cd your_repository
    ```

2. **Create the `.env` file**:
    ```sh
    GF_SECURITY_ADMIN_USER=admin
    GF_SECURITY_ADMIN_PASSWORD=password
    GF_SERVER_ROOT_URL=http://localhost:3000
    GF_SERVER_SERVE_FROM_SUB_PATH=true
    ```

3. **Create the Docker network**:
    ```sh
    docker network create monitoring
    ```

4. **Start the services**:
    ```sh
    docker-compose up -d
    ```

5. **Access Grafana**:
    - URL: `http://localhost:3000`
    - User: `admin`
    - Password: `grafana`

6. **Access Prometheus**:
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

