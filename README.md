# Node.js Demo App (CI/CD with Docker & GitHub Actions)

A simple Node.js and Express application containerized with Docker and automated via GitHub Actions CI/CD.

---

## Features & Changes Made

1. **Dockerfile**
   - Packaged the app into a lightweight Docker image using `node:22-alpine`.
   - Copies app files, installs dependencies, exposes port `5000`, and starts the server.

2. **Docker Ignore (`.dockerignore`)**
   - Excludes unnecessary files (`node_modules`, `.git`, `.env`, etc.) to keep Docker builds fast and slim.

3. **Git Ignore (`.gitignore`)**
   - Prevents local dependencies, environment variables, and build artifacts from being committed.

4. **Automated Testing**
   - Added a syntax check script to `package.json`:
     ```bash
     npm test
     ```
   - Runs `node --check index.js` to catch syntax errors before building.

5. **GitHub Actions Workflow (`.github/workflows/main.yml`)**
   - Automatically triggered on push to the `main` branch.
   - Steps:
     - Check out code.
     - Set up Node.js and install dependencies.
     - Run syntax tests.
     - Build and push the Docker image to Docker Hub.

6. **Secure Credentials**
   - Uses GitHub repository secrets (`DOCKERHUB_USERNAME` and `DOCKERHUB_TOKEN`) for secure authentication with Docker Hub.

---

## Local Development

### 1. Install Dependencies
```bash
npm install
```

### 2. Run Tests
```bash
npm test
```

### 3. Start the Server
```bash
npm start
```
Open [http://localhost:5000](http://localhost:5000) in your browser.

---

## Docker Usage

### Build the Image
```bash
docker build -t nodejs-demo-app .
```

### Run the Container
```bash
docker run -p 5000:5000 nodejs-demo-app
```
