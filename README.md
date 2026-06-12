# Distributed Voting Application (Kubernetes)

A polyglot microservices application designed to demonstrate a complete distributed system orchestrated with Kubernetes. This project features a variety of technologies and programming languages, showcasing a modern approach to application development and deployment.

## 🚀 Overview

This application allows users to vote between two options (e.g., Cats vs. Dogs) and see the results in real-time. It is built using a microservices architecture, ensuring each component is decoupled and independently scalable.

### Key Features

- **Microservices Architecture:** Decoupled components communicating via queues and persistent storage.
- **Polyglot Development:** Built using Python, .NET Core, and Node.js.
- **Kubernetes Orchestration:** Fully containerized and ready for deployment on any K8s cluster.
- **Real-time Updates:** Vote results are updated instantly via a Node.js web app.
- **Persistent Data:** Reliable storage using PostgreSQL and Redis.

## 🏗 Architecture

The application consists of five main components:

![Architecture diagram](architecture.excalidraw.png)

1. **Vote (Python):** A front-end web app that allows users to cast their votes.
2. **Redis:** A message broker that collects new votes from the Python app.
3. **Worker (.NET Core):** A background service that consumes votes from Redis and stores them in the database.
4. **PostgreSQL:** A persistent database for storing vote totals.
5. **Result (Node.js):** A front-end web app that displays the voting results in real-time.

## 🛠 Tech Stack

| Component | Technology |
| :--- | :--- |
| **Frontend (Voting)** | Python (Flask) |
| **Frontend (Results)** | Node.js |
| **Backend Worker** | .NET Core |
| **In-Memory Store** | Redis |
| **Database** | PostgreSQL |
| **Orchestration** | Kubernetes |

## ☸️ Kubernetes Deployment

The application is configured for deployment on Kubernetes. All necessary manifests are located in the `k8s/` directory.

### Prerequisites

- A running Kubernetes cluster (Minikube, Kind, or managed service like GKE/EKS).
- `kubectl` CLI installed and configured.

### Quick Start

1. **Clone the repository:**

    ```bash
    git clone <repository-url>
    cd voting-app-k8s
    ```

2. **Deploy the application:**
    Run the following command to create all deployments and services:

    ```bash
    kubectl apply -f k8s/
    ```

3. **Verify the deployment:**
    Check that all pods and services are running:

    ```bash
    kubectl get pods
    kubectl get services
    ```

### Accessing the App

Once the services are deployed, you can access the voting and results apps via the LoadBalancer IPs (or via `minikube service` if using Minikube):

- **Voting App:** `http://<external-ip>:8080`
- **Results App:** `http://<external-ip>:8080` (Note: Check service configurations if port conflicts occur in your environment).

*Note: In a local environment like Minikube, use `minikube service vote` and `minikube service result` to open the applications in your browser.*

## 🧹 Cleanup

To remove all resources created by the application, run:

```bash
kubectl delete -f k8s/
```

---
*This project is part of a portfolio demonstrating expertise in Kubernetes, Docker, and Microservices Architecture.*
