## Highly Available Deployment of RabbitMQ in Docker, Docker Swarm, and Kubernetes

This repository provides methods to deploy RabbitMQ clusters using different orchestration tools:

1. **RabbitMQ Cluster in Docker (Single Node)**:
2. **RabbitMQ Cluster in Docker (Three Nodes)**:
3. **RabbitMQ Cluster in Docker Swarm**:
4. **RabbitMQ Cluster in Kubernetes with Helm**:

---
### RabbitMQ Cluster in Docker (Single Node)

1. Use `docker-1-node` folder.
2. Copy the Docker Compose file to your node.
3. Run the following command:

    ```bash
    docker compose -f docker-compose-all-in-1-node.yml up -d
    ```

---
### RabbitMQ Cluster in Docker (Three Nodes)

1. Use `docker-3-node` folder.
2. Copy the Docker Compose file to each node.
3. Run the following command on each node accordingly:

    ```bash
    docker compose -f docker-compose-node1.yml up -d
    ```

---
### RabbitMQ Cluster in Docker Swarm

1. Use `docker-swarm` folder.
2. Copy the Docker Compose file to a node in your Docker Swarm cluster.
3. Run the following command:

    ```bash
    docker stack deploy -c 'docker-compose-swarm.yml' -d rabbitmq
    ```

---
### RabbitMQ Cluster in Kubernetes with Helm

1. Add the RabbitMQ Helm repository:

    ```bash
    helm repo add bitnami https://charts.bitnami.com/bitnami
    helm repo update
    ```

2. Install the RabbitMQ cluster:

    ```bash
    helm upgrade --install rabbitmq bitnami/rabbitmq \
      --set auth.username=rabbitmq \
      --set auth.password=rabbitmq \
      --set persistence.size=4Gi \
      --set replicaCount=3
    ```
