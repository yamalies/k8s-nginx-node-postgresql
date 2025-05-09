# Simple Web Application with Kubernetes

This repository contains a simple web application that can be deployed to Kubernetes. It includes:

- A frontend using Nginx
- A backend using Node.js
- A PostgreSQL database

## Directory Structure

```
├── backend/
│   ├── Dockerfile
│   ├── package.json
│   └── server.js   
├── frontend/   
│   ├── Dockerfile
│   └── html/
│       └── index.html
├── k8s/
│   ├── configmap.yaml
│   ├── deployment.yaml
│   ├── ingress.yaml
│   ├── namespace.yaml
│   ├── service.yaml
│   └── statefulset.yaml
└── docker-compose.yml
```

## Kubernetes Deployment

To deploy the application to Kubernetes:

1. Create a namespace for the application:

```bash
kubectl apply -f k8s/namespace.yaml
```

2. Deploy the k8s resources:

```bash
kubectl apply -f k8s/
```

3. Check the status of the pods:

```bash
kubectl get pods -n simple-web
```

## Docker Compose (for local development)

For local development, you can use Docker Compose:

```bash
docker-compose up -d
```

Access the application at:

- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

## Troubleshooting

If your containers are not starting properly in Kubernetes, check the logs:

```bash
kubectl logs -n simple-web deployment/frontend
kubectl logs -n simple-web deployment/backend
kubectl logs -n simple-web statefulset/db
```
