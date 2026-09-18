# Docker_Naj

# Dockerized Full-Stack Student Registration Application

This project is a full-stack Student Registration Application containerized using Docker and Docker Compose.

The application consists of a Node.js/Express frontend and a Python/Flask backend. The frontend provides a student registration form and sends the submitted data to the Flask backend for processing.

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

## Project Structure

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

## Application Architecture

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

## Frontend

The frontend is developed using Node.js and Express.js.

It provides a Student Registration Form containing:

- Name
- Email
- Course

The frontend receives the submitted form data and sends it to the Flask backend.

Frontend Port:

3000

## Backend

The backend is developed using Python and Flask.

The Flask backend receives the submitted student information from the frontend and processes the data.

Backend Port:

5000

## Docker Configuration

The project contains separate Dockerfiles for the frontend and backend.

### Frontend Dockerfile

The frontend Dockerfile:

- Uses Node.js 18.
- Creates a working directory.
- Installs the required npm packages.
- Copies the frontend source code.
- Exposes port 3000.
- Starts the Express application.

### Backend Dockerfile

The backend Dockerfile:

- Uses Python.
- Creates a working directory.
- Installs Flask and required dependencies.
- Copies the backend source code.
- Exposes port 5000.
- Starts the Flask application.

## Docker Compose

Docker Compose is used to build and run both services together.

The services are:

- backend
- frontend

The frontend communicates with the backend using the Docker Compose service name.

Backend service:

http://backend:5000

Frontend service:

http://localhost:3000

## How to Run the Application

Make sure Docker and Docker Compose are installed.

Clone the repository:

git clone https://github.com/NajPathan-Devops/Docker_Naj.git

Go to the project directory:

cd Docker_Naj

Build the Docker images:

docker compose build

Start the containers:

docker compose up -d

Check the running containers:

docker compose ps

Open the application in a browser:

http://localhost:3000

## Stop the Application

To stop and remove the containers:

docker compose down

## Docker Images

The following Docker images were created and pushed to Docker Hub.

### Backend Image

najpathan/docker-backend:latest

### Frontend Image

najpathan/docker-frontend:latest

## Docker Hub

Docker Hub Username:

najpathan

Backend Image:

najpathan/docker-backend:latest

Frontend Image:

najpathan/docker-frontend:latest

## GitHub Repository

GitHub Repository:

https://github.com/NajPathan-Devops/Docker_Naj

## Form Submission Workflow

The application works as follows:

1. The user opens the Student Registration Form.
2. The user enters Name, Email and Course.
3. The form is submitted to the Node.js frontend.
4. The Node.js frontend sends the form data to the Flask backend.
5. The Flask backend processes the submitted information.
6. The backend returns the response.
7. The frontend displays the submitted information.

## Verification

The application was successfully tested using Docker Compose.

Both containers were running successfully:

- flask_backend
- node_frontend

The frontend was accessible through:

http://localhost:3000

The form was successfully submitted and the submitted student information was displayed.

## Useful Docker Commands

Build images:

docker compose build

Start containers:

docker compose up -d

Check containers:

docker compose ps

View running containers:

docker ps

Stop containers:

docker compose down

## Git Commands Used

Initialize Git:

git init

Rename branch:

git branch -M main

Add files:

git add .

Commit changes:

git commit -m "Complete Docker full-stack application"

Add GitHub remote:

git remote add origin https://github.com/NajPathan-Devops/Docker_Naj.git

Push project:

git push -u origin main

## Author

Naj Pathan

GitHub:

https://github.com/NajPathan-Devops

Docker Hub:

https://hub.docker.com/u/najpathan

## Project Status

Completed

- Node.js/Express frontend created
- Flask backend created
- Dockerfiles created
- Docker Compose configuration created
- Docker images built successfully
- Docker containers running successfully
- Student registration form tested successfully
- Backend Docker image pushed to Docker Hub
- Frontend Docker image pushed to Docker Hub
- Source code pushed to GitHub
