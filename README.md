# prod-lab-frontend
Statis frontend served by nginx

# Description
Simple HTML page that connects to backend API

# Build
`podman build -t prod-lab-frontend:0.1`

# Run
`podman run --rm -p 8081:80 prod-lab-frontend:0.1`

# Open:
`http://localhost:8081`

---

# CI
This repository uses GitHub Actions to automatically build and publish the frontend container image.

**What happens on every push to main?**
1. Repository is checked out on a GitHub runner.
2. Docker image is built from the Nginx-based Dockerfile.
3. Te image is tagged using the commit SHA.
4. The image is pushed to GitHub container Registry (GHCR)

Example image format:
`ghcr.io/<github-userbame>/prod-lab-frontend:<commit-sha>`

This allows:
* Reproducible builds
* Immutable versioning
* Deployment to Kubernetes without local builds

**Workflow file**
.github/workflows/frontend.yml


This CI pipeline ensures that container images are built in clean Ubuntu environment provided by GitHub Actions. 
This guarantees that builds are reproducible and independent from the developer's local machine.