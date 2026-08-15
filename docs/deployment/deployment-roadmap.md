# Deployment Roadmap

## Local Development

Developer machine:

```text
Java 21
Spring Boot
PostgreSQL
Podman
Podman Compose
```

The application must be runnable locally without Azure.

## Containerization

Each deployable service will have an OCI-compatible container image.

Local workflow:

```text
Source
  |
Gradle Build
  |
Container Image
  |
Podman
```

## Azure Container Registry

Future workflow:

```text
Podman Build
     |
Tag
     |
Push
     v
Azure Container Registry
```

Image tags should be immutable/versioned where possible.

## AKS

Future deployment:

```text
ACR
 |
 v
AKS
 |
 +-- Auth Service
 +-- Problem Service
 +-- Submission Service
 +-- Execution Service
 +-- Future Services
```

Kubernetes resources will include:

- Deployment
- Service
- ConfigMap
- Secret integration
- Ingress
- HPA
- Probes
- Resource requests/limits

## API Management

APIM will become the controlled external API entry point.

Responsibilities may include:

- API routing.
- Authentication/token validation.
- Rate limiting.
- API versioning.
- Request/response policies.
- Observability integration.

Internal services should not all be directly exposed to the public internet.

## Key Vault

Production secrets should be retrieved through Azure identity-based access rather than committed configuration.

## CI/CD

Pipeline:

```text
Git Push
   |
Build
   |
Unit Tests
   |
Integration Tests
   |
Container Build
   |
Push to ACR
   |
Deploy to AKS
   |
Smoke Test
```

## Rollback

Deployment strategy must support rollback to a known good application version.

Helm releases will be used in the Kubernetes phase.
