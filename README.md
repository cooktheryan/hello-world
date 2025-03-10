# HTTP Server for OpenShift

This repository contains Kubernetes manifests for deploying an HTTP server in OpenShift.

## Components

- **Deployment**: Apache HTTP Server (HTTPD) based on Red Hat UBI 8
- **Service**: Exposes the HTTP server within the cluster
- **Route**: Exposes the service externally
- **ConfigMap**: Provides the custom index.html content

## Deployment Instructions

To deploy this application to an OpenShift cluster using GitOps:

1. Make sure you have access to an OpenShift cluster
2. Apply the manifests using your GitOps operator (ArgoCD, etc.) or directly with `oc apply`:

```bash
# Create all resources
oc apply -k manifests/httpd
```

## Accessing the Application

After deployment, the application will be available at the route URL.

```bash
# Get the route URL
oc get route httpd-route -n rcook -o jsonpath='{.spec.host}'
```

The HTTP server runs on port 8080 and serves a custom welcome page.