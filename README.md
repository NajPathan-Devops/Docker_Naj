

````markdown
# Docker_Naj

## Full-Stack Student Registration Application with Docker and Kubernetes

A containerized full-stack Student Registration Application built with **Node.js, Express.js, Python, and Flask**, and deployed locally using **Docker, Docker Compose, Kubernetes, and Minikube**.

The project demonstrates the complete workflow of developing a multi-service application, containerizing its components, managing communication between services, and deploying the containerized application to a local Kubernetes cluster.

---

## 1. Project Overview

This project consists of two application components:

- **Frontend:** Node.js with Express.js
- **Backend:** Python with Flask

The frontend provides a Student Registration Form where users can enter:

- Student Name
- Email Address
- Course

The submitted information is sent from the Express.js frontend to the Flask backend for processing.

The application was implemented in two stages:

### Stage 1 — Docker

The frontend and backend were containerized using Docker and orchestrated locally using Docker Compose.

### Stage 2 — Kubernetes

The Dockerized application was deployed to a local Kubernetes cluster using Minikube.

Kubernetes Deployments manage the application containers, while Kubernetes Services provide networking and service discovery between the frontend and backend.

---

# 2. Objectives

The main objectives of this project are:

- Develop a full-stack web application.
- Create a Node.js/Express.js frontend.
- Create a Python/Flask backend.
- Containerize both application components using Docker.
- Configure communication between frontend and backend services.
- Run the application using Docker Compose.
- Build and publish Docker images.
- Maintain the project source code using Git and GitHub.
- Deploy the Dockerized application to Kubernetes.
- Create Kubernetes Deployments and Services.
- Use Minikube for local Kubernetes deployment.
- Verify Kubernetes resources and application functionality.
- Test frontend-to-backend communication inside the Kubernetes cluster.

---

# 3. Technology Stack

| Technology | Purpose |
|---|---|
| Node.js | Frontend runtime |
| Express.js | Frontend web framework |
| Python | Backend programming language |
| Flask | Backend web framework |
| Docker | Application containerization |
| Docker Compose | Multi-container application management |
| Kubernetes | Container orchestration |
| Minikube | Local Kubernetes cluster |
| kubectl | Kubernetes command-line interface |
| Git | Version control |
| GitHub | Source code hosting |
| Docker Hub | Container image registry |

---

# 4. Application Architecture

## High-Level Architecture

```text
                    User / Browser
                          |
                          |
                          v
              +-----------------------+
              |   Express.js Frontend |
              |       Port 3000        |
              +-----------------------+
                          |
                          |
                 HTTP Request
                          |
                          v
              +-----------------------+
              |    Flask Backend      |
              |       Port 5000       |
              +-----------------------+
                          |
                          v
                   Form Processing
````

---

# 5. Project Structure

```text
Docker_Naj/
│
├── backend/
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
│
├── frontend/
│   ├── Dockerfile
│   ├── app.js
│   ├── package.json
│   └── package-lock.json
│
├── k8s/
│   ├── backend-deployment.yaml
│   ├── backend-service.yaml
│   ├── frontend-deployment.yaml
│   └── frontend-service.yaml
│
├── docker-compose.yml
├── .gitignore
└── README.md
```

---

# 6. Frontend

The frontend is implemented using **Node.js and Express.js**.

It provides the Student Registration Form and handles incoming browser requests.

### Frontend Responsibilities

* Display the registration form.
* Accept student information.
* Receive form submissions.
* Send submitted information to the Flask backend.
* Display the backend response to the user.

### Port

```text
3000
```

---

# 7. Backend

The backend is implemented using **Python and Flask**.

It receives registration data from the frontend and processes the submitted information.

### Backend Responsibilities

* Receive registration requests.
* Process submitted student information.
* Return a response to the frontend.

### Port

```text
5000
```

---

# 8. Docker Implementation

Both application components are containerized independently.

Separate Dockerfiles are provided for:

* Frontend
* Backend

This allows each service to be built, started, and managed independently.

---

## 8.1 Frontend Dockerfile

The frontend Dockerfile:

1. Uses a Node.js base image.
2. Creates the application working directory.
3. Copies the package configuration files.
4. Installs the required npm dependencies.
5. Copies the application source code.
6. Exposes port `3000`.
7. Starts the Express.js application.

---

## 8.2 Backend Dockerfile

The backend Dockerfile:

1. Uses a Python base image.
2. Creates the application working directory.
3. Copies `requirements.txt`.
4. Installs the required Python dependencies.
5. Copies the Flask application.
6. Exposes port `5000`.
7. Starts the Flask application.

---

# 9. Docker Compose

Docker Compose is used to run the frontend and backend together.

The application consists of two services:

```text
frontend
backend
```

Docker Compose provides a shared network that allows the frontend container to communicate with the backend using the backend service name.

### Backend Service

```text
backend:5000
```

### Frontend Application

```text
http://localhost:3000
```

---

# 10. Running the Application with Docker

## Step 1 — Clone the Repository

```bash
git clone https://github.com/NajPathan-Devops/Docker_Naj.git
```

## Step 2 — Navigate to the Project

```bash
cd Docker_Naj
```

## Step 3 — Build the Images

```bash
docker compose build
```

## Step 4 — Start the Application

```bash
docker compose up -d
```

## Step 5 — Verify Containers

```bash
docker compose ps
```

## Step 6 — Access the Application

Open:

```text
http://localhost:3000
```

---

# 11. Docker Images

The application images were built and published to Docker Hub.

### Backend Image

```text
najpathan/docker-backend:latest
```

### Frontend Image

```text
najpathan/docker-frontend:latest
```

Docker Hub username:

```text
najpathan
```

---

# 12. Application Workflow

The application follows the following request flow:

```text
User
  |
  v
Student Registration Form
  |
  v
Express.js Frontend
  |
  v
Flask Backend
  |
  v
Form Processing
  |
  v
Response
  |
  v
Frontend
  |
  v
User
```

### Submission Process

1. The user opens the Student Registration Form.
2. The user enters the required information.
3. The form is submitted to the Express.js frontend.
4. The frontend sends the information to the Flask backend.
5. The Flask backend processes the request.
6. The backend returns a response.
7. The frontend displays the result.

---

# 13. Kubernetes Deployment

After successfully containerizing the application, the same Docker images were deployed to a local Kubernetes cluster using **Minikube**.

The Kubernetes deployment consists of:

* Backend Deployment
* Backend Service
* Frontend Deployment
* Frontend Service

---

# 14. Kubernetes Architecture

```text
                         Browser
                            |
                            |
                    NodePort :3000
                            |
                            v
                 +----------------------+
                 |  Frontend Service    |
                 |  frontend-service    |
                 +----------------------+
                            |
                            v
                 +----------------------+
                 | Frontend Deployment  |
                 | Node.js / Express     |
                 | Port 3000             |
                 +----------------------+
                            |
                            |
                 backend-service:5000
                            |
                            v
                 +----------------------+
                 |   Backend Service    |
                 |   ClusterIP :5000    |
                 +----------------------+
                            |
                            v
                 +----------------------+
                 | Backend Deployment   |
                 | Python / Flask       |
                 | Port 5000            |
                 +----------------------+
```

---

# 15. Kubernetes Configuration Files

The Kubernetes configuration files are stored inside the `k8s/` directory.

```text
k8s/
├── backend-deployment.yaml
├── backend-service.yaml
├── frontend-deployment.yaml
└── frontend-service.yaml
```

---

## 15.1 Backend Deployment

File:

```text
k8s/backend-deployment.yaml
```

The Backend Deployment manages the Flask application container.

Docker image:

```text
najpathan/docker-backend:latest
```

Container port:

```text
5000
```

The deployment is configured with one replica.

---

## 15.2 Backend Service

File:

```text
k8s/backend-service.yaml
```

The backend is exposed internally using a Kubernetes `ClusterIP` Service.

```text
Service Name: backend-service
Port: 5000
Type: ClusterIP
```

The service provides an internal DNS name:

```text
backend-service:5000
```

This allows other Kubernetes workloads to communicate with the Flask backend.

---

## 15.3 Frontend Deployment

File:

```text
k8s/frontend-deployment.yaml
```

The Frontend Deployment manages the Node.js/Express application.

Docker image:

```text
najpathan/docker-frontend:latest
```

Container port:

```text
3000
```

The deployment also defines the backend URL:

```text
BACKEND_URL=http://backend-service:5000
```

---

## 15.4 Frontend Service

File:

```text
k8s/frontend-service.yaml
```

The frontend is exposed using a Kubernetes `NodePort` Service.

```text
Service Name: frontend-service
Port: 3000
Type: NodePort
```

This makes the frontend accessible from outside the Kubernetes cluster through Minikube.

---

# 16. Kubernetes Networking

One important configuration difference between Docker Compose and Kubernetes is service discovery.

In Kubernetes, the frontend must not use:

```text
http://localhost:5000
```

because `localhost` inside the frontend container refers to the frontend container itself.

Instead, the frontend uses the Kubernetes Service:

```text
http://backend-service:5000
```

The environment variable configured in the frontend Deployment is:

```text
BACKEND_URL=http://backend-service:5000
```

Kubernetes DNS resolves `backend-service` to the backend Service.

This enables communication between the frontend and backend without exposing the backend directly to the external network.

---

# 17. Minikube Environment

The application was deployed using Minikube with the Docker driver.

Environment used:

```text
Minikube:      v1.39.0
kubectl:       v1.36.4
Kubernetes:    v1.37.0
Driver:        Docker
```

---

# 18. Starting Minikube

Start the local Kubernetes cluster:

```bash
minikube start --driver=docker
```

Verify the cluster:

```bash
minikube status
```

---

# 19. Loading Docker Images into Minikube

The Docker images were loaded directly into the Minikube environment.

### Backend

```bash
minikube image load najpathan/docker-backend:latest
```

### Frontend

```bash
minikube image load najpathan/docker-frontend:latest
```

The Kubernetes Deployments use:

```yaml
imagePullPolicy: Never
```

This ensures Kubernetes uses the locally loaded images instead of attempting to download them from a remote registry.

---

# 20. Deploying the Application

Navigate to the project directory:

```bash
cd ~/Docker_Naj
```

Apply all Kubernetes manifests:

```bash
kubectl apply -f k8s/
```

This creates the required Kubernetes resources.

---

# 21. Verifying Kubernetes Pods

Run:

```bash
kubectl get pods
```

The backend and frontend pods should reach:

```text
READY   1/1
STATUS  Running
```

Example:

```text
NAME                                  READY   STATUS
backend-deployment-xxxxx              1/1     Running
frontend-deployment-xxxxx             1/1     Running
```

---

# 22. Verifying Kubernetes Deployments

Run:

```bash
kubectl get deployments
```

Expected deployments:

```text
backend-deployment
frontend-deployment
```

Both deployments should report:

```text
READY       1/1
AVAILABLE   1
```

---

# 23. Verifying Kubernetes Services

Run:

```bash
kubectl get services
```

The application contains two application services.

### Backend

```text
Name: backend-service
Type: ClusterIP
Port: 5000
```

### Frontend

```text
Name: frontend-service
Type: NodePort
Port: 3000
```

---

# 24. Accessing the Application

The frontend is exposed through the Kubernetes NodePort service.

Run:

```bash
minikube service frontend-service --url
```

Minikube generates a local URL.

Open the generated URL in a web browser.

The Student Registration Form can then be accessed through the Kubernetes deployment.

---

# 25. Application Verification

The Kubernetes deployment was successfully verified.

The following components were tested:

* Minikube cluster
* Backend Pod
* Frontend Pod
* Backend Deployment
* Frontend Deployment
* Backend Service
* Frontend Service
* Frontend-to-backend communication
* Student Registration Form
* Form submission

The application successfully displayed:

```text
Form Submitted Successfully
```

after submitting the registration form.

---

# 26. Kubernetes Commands Reference

### Start Minikube

```bash
minikube start --driver=docker
```

### Check Minikube

```bash
minikube status
```

### Load Backend Image

```bash
minikube image load najpathan/docker-backend:latest
```

### Load Frontend Image

```bash
minikube image load najpathan/docker-frontend:latest
```

### Deploy Kubernetes Resources

```bash
kubectl apply -f k8s/
```

### Check Pods

```bash
kubectl get pods
```

### Check Deployments

```bash
kubectl get deployments
```

### Check Services

```bash
kubectl get services
```

### Access Application

```bash
minikube service frontend-service --url
```

### Remove Kubernetes Resources

```bash
kubectl delete -f k8s/
```

### Stop Minikube

```bash
minikube stop
```

### Delete Minikube Cluster

```bash
minikube delete
```

---

# 27. Documentation and Screenshots

The project documentation includes screenshots demonstrating the successful Kubernetes deployment.

### Screenshot 1 — Minikube Started

Shows the successful initialization of the Minikube Kubernetes cluster.

### Screenshot 2 — Kubernetes Pods

Shows the backend and frontend pods in the `Running` state.

### Screenshot 3 — Kubernetes Deployments

Shows both deployments successfully running with one available replica.

### Screenshot 4 — Kubernetes Services

Shows the backend `ClusterIP` and frontend `NodePort` services.

### Screenshot 5 — Application Verification

Shows the Student Registration application successfully submitting the form through the Kubernetes deployment.

---

# 28. GitHub Repository

The complete source code and Kubernetes configuration are maintained in the following GitHub repository:

**Repository:**

```text
https://github.com/NajPathan-Devops/Docker_Naj
```

The repository contains:

* Frontend source code
* Backend source code
* Dockerfiles
* Docker Compose configuration
* Kubernetes manifests
* Project documentation

---

# 29. Project Status

## Docker Implementation

* [x] Node.js/Express frontend
* [x] Python/Flask backend
* [x] Frontend Dockerfile
* [x] Backend Dockerfile
* [x] Docker Compose configuration
* [x] Docker images built
* [x] Containers tested
* [x] Images published to Docker Hub
* [x] Source code pushed to GitHub

## Kubernetes Implementation

* [x] Minikube configured
* [x] Kubernetes cluster started
* [x] Docker images loaded into Minikube
* [x] Backend Deployment created
* [x] Backend Service created
* [x] Frontend Deployment created
* [x] Frontend Service created
* [x] Pods verified
* [x] Deployments verified
* [x] Services verified
* [x] Frontend-to-backend communication configured
* [x] Application accessed through Minikube
* [x] Student registration successfully tested

---

# 30. Conclusion

This project demonstrates the containerization and orchestration of a full-stack web application using modern DevOps technologies.

The application was first containerized using Docker, with separate containers for the Node.js/Express frontend and Python/Flask backend. Docker Compose was used to run the services together and establish communication between them.

The containerized application was subsequently deployed to a local Kubernetes cluster using Minikube. Kubernetes Deployments were used to manage the application workloads, while Services provided internal service discovery and external access to the frontend.

The final deployment was successfully verified by checking the Kubernetes resources and submitting the Student Registration Form through the Minikube-hosted application.

---

## Author

**Naj Pathan**

GitHub:

```text
https://github.com/NajPathan-Devops
```

Docker Hub:

```text
https://hub.docker.com/u/najpathan
```

---

**Project:** Docker_Naj
**Deployment Platform:** Kubernetes / Minikube
**Application Type:** Full-Stack Web Application


