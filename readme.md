# URL Shortener on AWS EKS

A small URL-shortening API, deployed to AWS the way a production service would be: infrastructure as code, GitOps delivery, observability, security scanning and cost control.

The app is deliberately simple. The focus of this project is the platform around it.

> **Status:** 🚧 In progress. See the [roadmap](#roadmap).

## What it does

- `POST /api/links`: shorten a URL
- `GET /{code}`: redirect to the original URL
- `GET /api/links/{code}`: click statistics

## Stack (planned)

| Area | Tools |
|---|---|
| App | Python, FastAPI, PostgreSQL, pytest, ruff, mypy |
| Containers | Docker (multi-stage, non-root), Amazon ECR, Trivy, hadolint |
| Infrastructure | Terraform (S3 remote state), VPC, EKS, RDS, IAM, tflint, checkov |
| CI/CD | GitHub Actions (OIDC to AWS, no stored keys), ArgoCD (GitOps), Helm |
| Kubernetes | AWS Load Balancer Controller, External Secrets, EKS Pod Identity, HPA, Karpenter, Kyverno |
| Observability | Prometheus, Grafana, Loki, Alertmanager |
| Testing | pytest, k6 load tests, kind for local clusters |


## Repository layout

```
app/       application code, tests, Dockerfile
infra/     Terraform: bootstrap, modules, envs/{dev,prod}
deploy/    Helm chart, ArgoCD apps, cluster add-ons
loadtest/  k6 scripts
docs/      architecture decisions, runbook
```

## Roadmap

- [ ] Application with tests and linting
- [ ] Container image with security scanning
- [ ] CI pipeline (GitHub Actions)
- [ ] Infrastructure as code (Terraform: VPC, EKS, RDS)
- [ ] GitOps deployment (Helm + ArgoCD)
- [ ] Observability (metrics, logs, alerts)
- [ ] Security hardening (policies, least-privilege IAM)
- [ ] Autoscaling and load testing
- [ ] Documentation (architecture diagram, ADRs, runbook)

## Cost

The project runs on a limited AWS budget. Environments are created for working sessions and destroyed afterwards.
