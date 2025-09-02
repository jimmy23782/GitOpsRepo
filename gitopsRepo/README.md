# GitOps repo

This repo is watched by Argo CD. It contains:
- `helm-charts/` — Helm charts for apps
- `gitops/environments/` — environment-specific Helm values (dev/stage/prod)
- `argo/` — Argo CD Applications/Projects that tell Argo what to sync

## Flow
1. CI in the app repo builds & pushes an image to ECR, then bumps `values-dev.yaml` tag.
2. Argo CD detects the change and rolls it out to the cluster.