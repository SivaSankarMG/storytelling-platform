# Collaborative Story Writing App

## Overview
This is a **3-tier React-based collaborative story writing application** that allows users to:
- Read stories
- Give feedback and rate stories
- Write new stories
- Allow others to contribute to stories
- Revert versions of stories
- Create rooms for discussions about stories

The application has been **containerized using Docker** for easy deployment and scalability.

## Tech Stack
- **Frontend:** React.js
- **Backend:** Node.js with Express.js
- **Database:** MongoDB
- **Containerization:** Docker & Docker Compose

## Project Structure
```
├── story-collab-backend   # Backend service (Express.js)
├── frontend               # Frontend service (React.js)
├── docker-compose.yml     # Docker Compose configuration
└── README.md              # Project documentation
```

## Docker Compose Configuration
The application is orchestrated using **Docker Compose**, with the following services:

### 1. Backend Service
- Builds from `./story-collab-backend`
- Runs on port `5000`
- Connected to the `mern_network`
- Depends on MongoDB

### 2. Frontend Service
- Builds from `./frontend`
- Runs on port `3000`
- Environment variable `REACT_APP_API_URL` is set to communicate with the backend

### 3. MongoDB Service
- Uses the latest MongoDB image
- Runs on port `27017`
- Data is persisted using a **named volume** (`mongo-data`)

## Setup & Installation

### Prerequisites
Ensure you have the following installed on your system:
- Docker
- Docker Compose

### Steps to Run the Application
1. Clone the repository:
   ```sh
   git clone https://github.com/SivaSankarMG/storytelling-platform.git
   cd storytelling-platform
   ```
2. Run the application using Docker Compose:
   ```sh
   docker-compose up --build
   ```
3. The services will be available at:
   - **Frontend:** `http://localhost:3000`
   - **Backend:** `http://localhost:5000`
   - **MongoDB:** Accessible on port `27017`

4. To stop the services, run:
   ```sh
   docker-compose down
   ```

## Persistent Storage
The MongoDB service uses a **Docker volume** (`mongo-data`) to persist data across container restarts.

## Networking
All services communicate through a Docker bridge network (`mern_network`), ensuring isolated and secure communication between the frontend, backend, and database.

## Future Enhancements
- Implementing **CI/CD pipelines** for automated deployment
- Deploying the application using **Kubernetes** for scalability

---

