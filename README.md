# Hello World ArgoCD Demo

A simple Hello World application to demonstrate ArgoCD deployment.

## Repository Structure

This repository contains a simple Kubernetes application deployed via ArgoCD.

```
hello-world/
├── namespace.yaml   # Creates the hello-world namespace
├── deployment.yaml  # Deploys NGINX pods with custom HTML
├── service.yaml     # Exposes the NGINX pods within the cluster
└── configmap.yaml   # Contains the HTML content for the hello world page
```

## How to use with ArgoCD

1. In the ArgoCD UI, click "+ NEW APP"
2. Fill in the application details:
   - **Application Name**: hello-world
   - **Project**: default
   - **Sync Policy**: Automatic (check "Prune Resources" and "Self Heal" for full automation)

3. For the source:
   - **Repository URL**: https://github.com/YOUR_USERNAME/hello-world-demo.git
   - **Revision**: HEAD (or main, or master)
   - **Path**: hello-world

4. For the destination:
   - **Cluster URL**: https://kubernetes.default.svc
   - **Namespace**: hello-world

5. Click "CREATE"

## Accessing the application

Once deployed, you can access the application by port-forwarding:

```bash
kubectl port-forward svc/hello-world-service -n hello-world 8080:80
```

Then visit http://localhost:8080 in your browser.

## Customization

Feel free to modify the HTML in `configmap.yaml` to personalize your Hello World page.