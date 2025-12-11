# 🐳 Docker Compose Utilities Repository

Welcome! This repository centralizes useful **Docker Compose** configurations to quickly spin up development or testing environments for various services.

The goal is to standardize how we provision infrastructure dependencies (databases, cache, queues, etc.).

---

## 📂 Repository Structure

The following folder structure is designed to keep the `compose` files organized by service type.

. ├── docs/ (Additional documentation, screenshots, diagrams) ├── services/ (All docker-compose files are stored here) │ ├── databases/ │ │ ├── postgres-14/ │ │ │ ├── docker-compose.yml │ │ │ └── DDL.sql (Example initialization scripts) │ │ ├── mysql-8/ │ │ ├── mongodb/ │ │ └── ... │ ├── cache/ │ │ ├── redis/ │ │ │ └── docker-compose.yml │ │ └── memcached/ │ ├── tools/ │ │ ├── pgadmin/ │ │ ├── adminer/ │ │ └── traefik/ │ └── full-stacks/ (Combinations of services that work together, e.g., Postgres + Redis + WebApp) │ └── app-base/ │ └── docker-compose.yml └── README.md (This file)

## 🚀 Basic Usage (Spinning Up a Service)

To spin up a specific service, navigate to its folder and use the `docker-compose up` command.

### Example: Spinning Up PostgreSQL

1.  Navigate to the service folder:
    ```bash
    cd services/databases/postgres-14
    ```

2.  Start the containers in detached mode (background):
    ```bash
    # Assuming the file is named 'docker-compose.yml'
    docker-compose up -d
    ```

3.  Verify the services are running:
    ```bash
    docker-compose ps
    ```

## 💻 Common Commands

This table summarizes the most frequently used commands for interacting with Docker Compose services.

| Command | Action | Description |
| :--- | :--- | :--- |
| `docker-compose up -d` | Start Services | Creates and starts all defined containers in detached (background) mode. |
| `docker-compose down` | Stop and Remove | Stops and removes containers, networks, but **keeps the data** in volumes. |
| `docker-compose down -v` | Total Cleanup | Stops, removes everything **including the volumes** (data). Useful for starting from scratch. |
| `docker-compose logs -f [service_name]` | View Logs | Displays the real-time (follow) output for a specific service (e.g., `db`). |
| `docker-compose ps` | Status | Lists the currently running containers for this `compose` configuration. |
| `docker-compose stop [service_name]` | Stop Service | Stops a running service without removing the container. |
| `docker-compose restart [service_name]` | Restart Service | Restarts a stopped or running service. |
| `docker-compose exec [service_name] bash` | Access Container | Opens a terminal session (`bash` or `sh`) inside a running container. |

## 🛑 Stopping and Cleanup

### Stopping Containers

Stops the containers but **retains the data** stored in the volumes.
```bash
docker-compose down
