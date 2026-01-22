# CD Demo Project

This project demonstrates a simple **Continuous Deployment (CD) pipeline** using:

- GitHub Actions
- Docker
- Docker Hub
- A static HTML web page

---

## Project Structure

- `index.html` — the static site
- `Dockerfile` — defines how to containerize the site
- `.github/workflows/cd.yml` — GitHub Actions workflow for CD

---

## How It Works

1. **Push to GitHub** (`main` branch)
2. GitHub Actions workflow triggers:
   - Checks out the repo
   - Logs in to Docker Hub
   - Builds Docker image
   - Pushes image to Docker Hub
3. **Deployment**
   - Pull the Docker image from Docker Hub
   - Run container on server:
     ```bash
     docker run -d -p 80:80 --name cd-demo USERNAME/cd-demo:latest
     ```
4. Access your app in browser: `http://<server-ip>/`

---

## GitHub Secrets

The workflow uses **secrets** to authenticate Docker Hub:

- `DOCKER_USERNAME` — your Docker Hub username
- `DOCKER_PASSWORD` — your Docker Hub password or token

