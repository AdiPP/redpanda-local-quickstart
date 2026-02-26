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

## Connection Testing from Host

You can test the connection from your host machine using `rpk` (Redpanda Keeper).

1.  **Install `rpk`:**
    Follow the instructions [here](https://docs.redpanda.com/current/get-started/rpk-install/) to install `rpk` on your machine.

2.  **Test the connection:**
    Run the following command to check the cluster status:

    ```bash
    rpk cluster info --brokers localhost:19092 --user admin --password password --sasl-mechanism SCRAM-SHA-256
    ```

    If successful, you should see information about your Redpanda cluster.

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
