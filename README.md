# Redpanda Quickstart

This project provides a quick way to get started with Redpanda using Docker Compose.

## Services

This Docker Compose setup includes the following services:

-   `redpanda-0`: The Redpanda broker. This is the main service that runs the Redpanda event streaming platform.
-   `redpanda-setup`: A one-time setup container that creates an administrative user for Redpanda.
-   `console`: The Redpanda Console, a web-based UI for managing and exploring your Redpanda cluster.

## How to use

1.  **Start the services:**

    ```bash
    docker-compose up -d
    ```

    **Note:** If you are using Podman, you can use `podman-compose` as an alternative to `docker-compose`.

2.  **Access the Redpanda Console:**

    Open your web browser and navigate to [http://localhost:8080](http://localhost:8080).

3.  **Connect to Redpanda:**

    Use the following details to connect to your Redpanda broker:
    -   **Brokers:** `localhost:19092`
    -   **SASL:** Enabled
    -   **Mechanism:** `SCRAM-SHA-256`
    -   **Username:** `admin`
    -   **Password:** `password`

## Ports

The following ports are exposed to your local machine:

-   `18081`: Schema Registry
-   `18082`: Pandaproxy
-   `19092`: Kafka API
-   `19644`: Redpanda Admin API
-   `8080`: Redpanda Console

## Volumes

-   `redpanda-0`: A named volume is used to persist Redpanda data.

## Networks

-   `redpanda_network`: A bridge network is created to allow the services to communicate with each other.
