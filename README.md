# ubernutty-cluster

Production-inspired Kubernetes homelab that I run entirely as GitOps: every change to what's deployed goes through this repo first, and Flux reconciles the cluster to match it every 10 minutes. No cluster access, no `kubectl apply` by hand. If it's not committed here, it doesn't exist in the cluster, and that's the whole point.

## What's actually running

- **Flux** watches this repo directly and applies whatever's under `clusters/staging`, pulling in `infrastructure`, `monitoring`, and `apps` as layered kustomizations
- **SOPS + age** encrypt every secret in these manifests before they're committed. Nothing sensitive is ever plaintext in git history, even in a private repo
- **kube-prometheus-stack** for metrics and dashboards, so I can actually see what the cluster's doing instead of guessing
- **Renovate** opens PRs automatically whenever a base image or Flux controller has an update, so dependency drift doesn't quietly pile up
- **Cloudflare tunnels** expose the services below without opening a port on my home network

## Services running on it

| Service | What it does |
|---|---|
| Linkding | Self-hosted bookmark manager |
| Audiobookshelf | Self-hosted audiobook/podcast server |

## Why this exists

I wanted a real environment to get hands-on with what separates "I know Kubernetes" from "I run Kubernetes": encrypted secrets, automated reconciliation, actual observability, and dependency hygiene, not a one-time `kubectl create deployment` demo. This is a live cluster, not a tutorial I followed once and abandoned.

## Stack

| Category | Tool |
|---|---|
| GitOps | FluxCD |
| Secrets | SOPS + age |
| Monitoring | Prometheus + Grafana |
| Dependency automation | Renovate |
| Ingress | Cloudflare Tunnel |
