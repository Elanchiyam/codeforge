# ADR-0002: Use Podman for Local Container Development

## Status

Accepted

## Context

The development environment is an organization-managed laptop where Docker Desktop licensing/policy may prevent its use.

## Decision

Use Podman as the local container engine.

## Rationale

Podman supports OCI-compatible images and provides a Docker-compatible workflow for the core container operations required by the project.

The target runtime is Kubernetes/AKS, which consumes OCI-compatible container images.

## Consequences

Positive:

- Fits the development environment.
- No dependency on Docker Desktop.
- Builds transferable container knowledge.
- Images can be pushed to Azure Container Registry.

Considerations:

- Some Docker-specific compose/tooling behavior may differ.
- Team documentation must clearly identify Podman commands.
- CI tooling may use a different container builder if required by the pipeline.

## Principle

Learn container concepts first; treat Docker and Podman as implementations of the container workflow rather than the learning objective itself.
