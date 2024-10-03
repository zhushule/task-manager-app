Task Manager Application
Table of Contents
Features
Project Structure
Getting Started
Prerequisites
Running Locally with Docker Compose
Deploying with Kubernetes
Directory Structure
Technologies Used
Future Enhancements
Features

- Frontend built with React to manage tasks (CRUD operations).
- Backend built with Node.js and Express to serve the API.
- Containerized using Docker.
- Orchestrated with Kubernetes for production-like deployments.
- Quick local setup using Docker Compose for development.

Getting Started
Prerequisites

- Node.js (for local development)
- Docker (to build and run containers)
- Docker Compose (comes with Docker Desktop)
- kubectl (to manage Kubernetes clusters)
- Minikube or Docker Desktop's Kubernetes for local Kubernetes testing (optional)

Running Locally with Docker Compose
Docker Compose is a quick way to spin up both the frontend and backend in containers for local development.

1. Clone the Repository:

```bash
git clone https://github.com/your-username/task-manager-app.git
cd task-manager-app
```

2. Build and Start the Containers:

```bash
docker-compose up --build
```

This command will:

- Build the Docker images for the frontend and backend using their respective Dockerfiles.
- Start the containers and make the frontend accessible on `http://localhost:3000` and the backend on `http://localhost:5000`.

3. Stop the Containers:
   Press `CTRL + C` in the terminal running `docker-compose`.
   Alternatively, run:

```bash
docker-compose down
```

Deploying with Kubernetes
If you want to deploy the application in a Kubernetes cluster (e.g., Minikube, Docker Desktop's Kubernetes, or a cloud service):

1. Build and Push Docker Images to Docker Hub:
   Make sure you have Docker installed and are logged into Docker Hub:

```bash
docker login
```

Build and push the frontend image:

```bash
docker build -t your-dockerhub-username/task-manager-frontend:latest ./frontend
docker push your-dockerhub-username/task-manager-frontend:latest
```

Build and push the backend image:

```bash
docker build -t your-dockerhub-username/task-manager-backend:latest ./backend
docker push your-dockerhub-username/task-manager-backend:latest
```

2. Apply Kubernetes Manifests:
   Navigate to the root directory of the project and apply the Kubernetes configuration files:

```bash
kubectl apply -f k8s/frontend-deployment.yml
kubectl apply -f k8s/backend-deployment.yml
```

3. Access the Application:
   Get the services to find the `NodePort`:

```bash
kubectl get services
```

Access the frontend via `http://localhost:<NodePort>` where `<NodePort>` is the port assigned to `frontend-service`.
Directory Structure

- **`backend/`**: Contains the backend code and `Dockerfile`.
- **`frontend/`**: Contains the frontend code and `Dockerfile`.
- **`k8s/`**: Contains Kubernetes deployment and service manifests.
- **`docker-compose.yml`**: Defines services for local development using Docker Compose.

Technologies Used

- **Frontend**: React
- **Backend**: Node.js, Express
- **Containerization**: Docker
- **Orchestration**: Kubernetes
- **Local Development**: Docker Compose
