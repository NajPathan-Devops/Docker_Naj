
# Docker_Naj

# Dockerized Full-Stack Student Registration Application

This project is a full-stack Student Registration Application containerized using Docker and Docker Compose.

The application consists of a Node.js/Express frontend and a Python/Flask backend. The frontend provides a student registration form and sends the submitted data to the Flask backend for processing.

---

## Objective

The objectives of this project are:

- Create a Node.js and Express.js frontend.
- Create a Python and Flask backend.
- Create separate Dockerfiles for frontend and backend.
- Connect the frontend and backend using Docker Compose.
- Run both services as Docker containers.
- Build Docker images.
- Push Docker images to Docker Hub.
- Push the complete project source code to GitHub.

---

## Technologies Used

- Node.js
- Express.js
- Python
- Flask
- Docker
- Docker Compose
- Git
- GitHub
- Docker Hub

---

## Project Structure

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
├── docker-compose.yml
├── .gitignore
└── README.md
````

---

## Application Architecture

```text
Browser
   |
   | Port 3000
   v
Node.js / Express Frontend
   |
   | Docker Network
   v
Python / Flask Backend
   |
   | Port 5000
   v
Form Data Processing
```

---

## Frontend

The frontend is developed using Node.js and Express.js.

It provides a Student Registration Form containing:

* Name
* Email
* Course

The frontend receives the submitted form data and sends it to the Flask backend.

**Frontend Port:** `3000`

---

## Backend

The backend is developed using Python and Flask.

The Flask backend receives the submitted student information from the frontend and processes the data.

**Backend Port:** `5000`

---

## Docker Configuration

The project contains separate Dockerfiles for the frontend and backend.

### Frontend Dockerfile

The frontend Dockerfile:

* Uses Node.js 18.
* Creates a working directory.
* Copies the package files.
* Installs the required npm packages.
* Copies the frontend source code.
* Exposes port 3000.
* Starts the Express application.

### Backend Dockerfile

The backend Dockerfile:

* Uses Python 3.11.
* Creates a working directory.
* Copies the requirements file.
* Installs Flask and required dependencies.
* Copies the backend source code.
* Exposes port 5000.
* Starts the Flask application.

---

## Docker Compose

Docker Compose is used to build and run both services together.

The services are:

* `backend`
* `frontend`

The frontend communicates with the backend using the Docker Compose service name.

### Backend Service

```text
http://backend:5000
```

### Frontend Service

```text
http://localhost:3000
```

Both services run in the Docker Compose network, allowing the frontend container to communicate with the backend container.

---

## How to Run the Application

Make sure Docker and Docker Compose are installed on your system.

### 1. Clone the Repository

```bash
git clone https://github.com/NajPathan-Devops/Docker_Naj.git
```

### 2. Go to the Project Directory

```bash
cd Docker_Naj
```

### 3. Build the Docker Images

```bash
docker compose build
```

### 4. Start the Containers

```bash
docker compose up -d
```

### 5. Check the Running Containers

```bash
docker compose ps
```

### 6. Open the Application

Open the following address in a web browser:

```text
http://localhost:3000
```

---

## Stop the Application

To stop and remove the containers:

```bash
docker compose down
```

---

## Docker Images

The following Docker images were created and pushed to Docker Hub.

### Backend Image

```text
najpathan/docker-backend:latest
```

### Frontend Image

```text
najpathan/docker-frontend:latest
```

---

## Docker Hub

**Docker Hub Username:**

```text
najpathan
```

### Backend Image

```text
najpathan/docker-backend:latest
```

### Frontend Image

```text
najpathan/docker-frontend:latest
```

---

## GitHub Repository

**Repository:**

```text
NajPathan-Devops/Docker_Naj
```

---

## Form Submission Workflow

The application works as follows:

1. The user opens the Student Registration Form.
2. The user enters Name, Email, and Course.
3. The form is submitted to the Node.js/Express frontend.
4. The Node.js frontend sends the form data to the Flask backend.
5. The Flask backend receives and processes the submitted information.
6. The backend returns the response to the frontend.
7. The frontend displays the submitted student information.

---

## Verification

The application was successfully tested using Docker Compose.

Both containers were running successfully:

* `flask_backend`
* `node_frontend`

The frontend was accessible through:

```text
http://localhost:3000
```

The Student Registration Form was successfully submitted through the Dockerized application.

The submitted student information was successfully processed by the Flask backend and displayed by the frontend.

---

## Useful Docker Commands

### Build Images

```bash
docker compose build
```

### Start Containers

```bash
docker compose up -d
```

### Check Containers

```bash
docker compose ps
```

### View Running Containers

```bash
docker ps
```

### View Container Logs

```bash
docker compose logs
```

### Stop and Remove Containers

```bash
docker compose down
```

---

## Git Commands Used

### Initialize Git

```bash
git init
```

### Rename Branch to Main

```bash
git branch -M main
```

### Add Files

```bash
git add .
```

### Commit Changes

```bash
git commit -m "Complete Docker full-stack application"
```

### Add GitHub Remote

```bash
git remote add origin https://github.com/NajPathan-Devops/Docker_Naj.git
```

### Push Project to GitHub

```bash
git push -u origin main
```

---

## Author

**Naj Pathan**

GitHub:

```text
NajPathan-Devops
```

Docker Hub:

```text
najpathan
```

---

## Project Status

**Completed**

* [x] Node.js/Express frontend created
* [x] Flask backend created
* [x] Separate Dockerfiles created
* [x] Docker Compose configuration created
* [x] Frontend and backend connected
* [x] Docker images built successfully
* [x] Docker containers running successfully
* [x] Student registration form tested successfully
* [x] Backend Docker image pushed to Docker Hub
* [x] Frontend Docker image pushed to Docker Hub
* [x] Complete source code pushed to GitHub
* [x] Project successfully containerized using Docker Compose

---

## Conclusion

This project demonstrates the containerization of a full-stack application using Docker and Docker Compose.

The Node.js/Express frontend and Python/Flask backend are deployed as separate Docker containers and communicate with each other through the Docker Compose network.

The Docker images were successfully built and pushed to Docker Hub, and the complete project source code was pushed to GitHub.

```

Your actual links are:

- :contentReference[oaicite:0]{index=0}
- :contentReference[oaicite:1]{index=1}


```

GitHub Repository
https://github.com/NajPathan-Devops/Docker-Naj
