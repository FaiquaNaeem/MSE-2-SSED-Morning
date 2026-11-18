# MSE-2 Morning Shift
# Software Engineering and DevOps (AI310B)
---

## 1. Problem Statement

You are provided with a fully functional full-stack web application.

The application consists of the following components:

- **Frontend:** React.js with Vite
- **Backend:** Node.js with Express.js
- **Database:** PostgreSQL
- **Caching:** Redis

Your task is to containerize the complete application using Docker and Docker Compose, publish the application images to your personal Docker Hub account, and verify the deployment through the provided GitHub Actions CI/CD pipelines.

You are required to implement the Docker-related configurations yourself. The application source code is already provided.

The objective is to demonstrate your understanding of containerization, Docker networking, persistent storage, image publishing, multi-container orchestration and automated CI/CD pipelines.

## 2. Repository Details

You will receive the starter repository .

Repository URL: https://github.com/atindeRR/MSE-2-SSED-Morning

You must complete the practical using your own GitHub and Dockerhub account.

### Initial Setup

1. Open the provided starter repository.
2. Fork the repository into your personal GitHub account.
3. Clone your forked repository to your local machine.

```bash
git clone https://github.com/YOUR_USERNAME/MSE-2-SSED-Morning.git
cd MSE-2-SSED-Morning
```

4. Explore the existing application structure and understand the frontend, backend, PostgreSQL and Redis dependencies.
5. Create a separate working branch (if required).

**Important:** Do not modify or remove the existing application functionality. Your task is to implement the containerization and deployment configurations.

---

## 3. Practical Tasks

### Task 1: Create Dockerfiles

Create separate Dockerfiles for the frontend and backend applications.

**Frontend Dockerfile**

Your frontend Dockerfile must:

- Use an appropriate base image.
- Install the required dependencies.
- Build the React application.
- Serve the production build using Nginx or an appropriate production web server.
- Expose the appropriate container port.
- Follow Docker best practices.

**Backend Dockerfile**

Your backend Dockerfile must:

- Use an appropriate Node.js base image.
- Install the required dependencies.
- Copy the application source code.
- Configure the application startup command.
- Expose the backend port.
- Use environment variables for application configuration.
- Follow Docker best practices.

**Expected Deliverables:**

```text
frontend/Dockerfile
backend/Dockerfile
```

### Task 2: Implement Docker Compose

Create a `docker-compose.yml` file to orchestrate all four application services.

Your Docker Compose configuration must include:

1. Frontend
2. Backend
3. PostgreSQL
4. Redis

**Requirements:**

- Configure all four services.
- Establish appropriate container networking.
- Configure environment variables.
- Configure service dependencies.
- Implement health checks wherever appropriate.
- Use Docker volumes for PostgreSQL data persistence.
- Ensure the backend communicates with PostgreSQL and Redis using service names rather than localhost.
- Ensure the frontend can communicate with the backend.
- Configure appropriate host-to-container port mappings.
- Ensure the complete application starts using a single Docker Compose command.

**Expected Deliverable:**

```text
docker-compose.yml
```

**Application Startup:**

```bash
docker compose up -d --build
```

Verify that all four containers are running successfully.

### Task 3: Docker Hub Image Publishing

Publish your frontend and backend Docker images to your personal Docker Hub account.

**Requirements:**

1. Create a Docker Hub account if you do not already have one.
2. Create two repositories:
   - `frontend`
   - `backend`
3. Build the frontend and backend images.
4. Tag the images using your Docker Hub username.
5. Push both images to Docker Hub.
6. Verify that the images are available in your Docker Hub repositories.

**Expected image naming convention:**

```text
YOUR_DOCKERHUB_USERNAME/frontend

YOUR_DOCKERHUB_USERNAME/backend
```

You may also publish a `latest` tag.

### Task 4: Deployment Using Published Images

Create a separate Docker Compose configuration named:

```text
docker-compose.deploy.yml
```

This configuration must deploy the application using the images published on Docker Hub.

**Requirements:**

- Use the published frontend and backend images.
- Do not use `build:` directives in this deployment configuration.
- Use PostgreSQL and Redis official images.
- Configure environment variables securely.
- Configure PostgreSQL persistent storage.
- Ensure the application can be deployed on a clean machine without rebuilding the frontend and backend images locally.

**Deployment Verification:**

```bash
docker compose -f docker-compose.deploy.yml pull

docker compose -f docker-compose.deploy.yml up -d
```

Verify that the application is accessible and functioning correctly.

---

## 4. CI/CD Pipeline Implementation and Verification

A GitHub Actions CI/CD workflow is provided as part of the starter repository.

You are required to configure and execute the provided pipeline.

### Step 1: Configure GitHub Secrets

Navigate to:

**GitHub → Your Fork → Settings → Secrets and variables → Actions**

Create the following repository secrets:

| Secret Name | Description |
|---|---|
| `DOCKERHUB_USERNAME` | Your Docker Hub username |
| `DOCKERHUB_TOKEN` | Your Docker Hub access token |
| `POSTGRES_PASSWORD` | Password for the PostgreSQL deployment |

Never commit credentials or access tokens directly into your repository.

### Step 2: Execute the CD Pipeline

Push your implementation to the `main` branch of your fork.

```bash
git add .

git commit -m "Implement Docker containerization and deployment"

git push origin main
```

The CD workflow should automatically execute.

Verify the following stages:

| CD Stage | Expected Result |
|---|---|
| Repository checkout | Successful |
| Docker Buildx setup | Successful |
| Docker Hub authentication | Successful |
| Backend image build | Successful |
| Backend image publishing | Successful |
| Frontend image build | Successful |
| Frontend image publishing | Successful |
| Docker Compose image pull | Successful |
| Application deployment | Successful |
| Backend health verification | Successful |
| Frontend accessibility verification | Successful |

### Step 3: Verify the CI/CD Results

Navigate to:

**GitHub → Your Fork → Actions**

Open the latest workflow execution.

Verify that all required stages have completed successfully.

You must ensure that:

- Both Docker images are published successfully.
- The published images can be pulled.
- The deployment Compose configuration works.
- All application services start successfully.
- The application health checks pass.

---

## 5. Final Submission Through Pull Request

After completing the implementation and verifying that the CD pipeline passes, prepare your final submission.



"I hereby declare that the submitted Docker implementation is my own work. I have successfully executed and verified the required CI/CD pipeline stages, published the Docker images to my Docker Hub account, and tested the application deployment."

