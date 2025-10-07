# Next.js Docker & Kubernetes Deployment

This project demonstrates how to **containerize a Next.js application**, automate the Docker build using **GitHub Actions**, push the image to **GitHub Container Registry (GHCR)**, and deploy it to **Kubernetes (Minikube)**.

---

## 🚀 Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/raju200539/nextjs-app.git
cd nextjs-app
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Install Required Tools

* [Docker Installation Guide](https://docs.docker.com/get-docker/)
* [Minikube Installation Guide](https://minikube.sigs.k8s.io/docs/start/)

### 4. Run Locally (Development Mode)

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to see the app.

---

## 🐳 Docker Commands

### 1. Build the Docker Image

```bash
docker build -t nextjs-app .
```

### 2. Run the Container

```bash
docker run -d -p 3000:3000 nextjs-app
```

Visit [http://localhost:3000](http://localhost:3000) to see it running.

---

## ⚙️ GitHub Actions & GHCR

* The workflow `.github/workflows/docker-build.yml` automatically:

  1. Builds the Docker image on push to the `main` branch.
  2. Pushes the image to **GitHub Container Registry (GHCR)**.
  3. Tags images as `latest` and with commit SHA.

* GHCR Image URL:

```
ghcr.io/raju200539/nextjs-app:latest
```

---

## 🏗️ Deployment on Minikube

### 1. Start Minikube

```bash
minikube start
```

### 2. Apply Kubernetes Manifests

```bash
kubectl apply -f k8s/
```

### 3. Verify Pods and Service

```bash
kubectl get pods
kubectl get svc
```

### 4. Access the Application

```bash
minikube service nextjs-service
```

This command opens your browser at the correct URL for the app running inside Minikube.

---

## 📂 Project Structure

```
nextjs-docker-k8s-app/
├── .github/
│   └── workflows/docker-build.yml
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
├── Dockerfile
├── package.json
├── README.md
└── ...
```

---

## ✅ Notes

* Multi-stage Dockerfile used for optimized image size.
* Liveness and readiness probes ensure healthy Kubernetes pods.
* GHCR handles image storage securely with GitHub Actions automation.


* Repository URL: `https://github.com/raju200539/nextjs-app`
* GHCR Image URL: `ghcr.io/raju200539/nextjs-app:latest`
