# homelab

Production-inspired Kubernetes homelab managed with GitOps principles.

This repository contains the manifests, infrastructure configuration, and automation powering a self-hosted Kubernetes environment.

## Tooling

| Category | Stack |
|---|---|
| GitOps | FluxCD |
| Secrets | SOPS + age |
| Monitoring | Prometheus + Grafana |
| Automation | Renovate |
| Services | Linkding, Audiobookshelf |

## Design Principles

- Git as the source of truth
- Declarative infrastructure
- Encrypted secrets
- Automated maintenance
- Observable systems

## Notes

This environment is intentionally used to experiment with Kubernetes operations, automation workflows, and self-hosted services.
