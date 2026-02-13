# My Application

Simple static HTML application demonstrating GitOps deployment with ArgoCD.

## Structure

```
<app-name>/
├── src/
│   ├── index.html       # Main HTML page
│   └── nginx.conf       # Nginx configuration
├── .github/
│   └── workflows/
│       └── build.yml    # CI/CD pipeline
├── Dockerfile           # Container image definition
└── .dockerignore        # Files to exclude from build
```

## Local Development

Build and run:

```bash
docker build -t $(basename $PWD):local .
docker run -p 8080:80 $(basename $PWD):local
```

Visit: http://localhost:8080

## CI/CD

GitHub Actions automatically builds and pushes Docker images to GitHub Container Registry on:
- Pushes to `main` branch
- Version tags (e.g., `v1.0.0`)

Images available at: `ghcr.io/johanson1988/<app-name>`

## Deployment

Container images are automatically deployed to Kubernetes via ArgoCD.
See the `infra-live` repository for Kubernetes manifests.
