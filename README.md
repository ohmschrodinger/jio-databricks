# Jio Sales Analytics — Databricks

A Databricks-based sales analytics project demonstrating Databricks SQL dashboards, Databricks Asset Bundles, Git-based version control, and automated CI/CD deployment using GitHub Actions.

## Overview

This project includes:

- Sales data analysis in Databricks
- Interactive Databricks SQL dashboard
- Development and production environments
- Databricks Asset Bundle configuration
- GitHub-based version control
- Automated production deployment with GitHub Actions

## Architecture

```text
GitHub Repository
       │
       │ Push to main
       ▼
GitHub Actions
       │
       ├── Checkout repository
       ├── Setup Databricks CLI
       ├── Validate bundle
       └── Deploy bundle
               │
               ▼
       Databricks Production
               │
               ▼
        Sales Dashboard
```

## Project Structure

```text
jio-databricks/
├── .github/
│   └── workflows/
│       └── deploy-prod.yml
├── databricks.yml
├── dev_staging.lvdash.json
└── README.md
```

## Environments

### Development

The `dev` target uses development mode for testing and development changes.

### Production

The `prod` target uses production mode and is deployed automatically when changes are pushed to the `main` branch.

## CI/CD

GitHub Actions automates the production deployment.

```text
Push to main
     ↓
Checkout repository
     ↓
Setup Databricks CLI
     ↓
Validate Databricks Bundle
     ↓
Deploy bundle to production
```

The workflow is defined in:

```text
.github/workflows/deploy-prod.yml
```

## Databricks Asset Bundles

Deployment configuration is defined in `databricks.yml`.

The bundle contains separate `dev` and `prod` targets, allowing the same project configuration to be deployed to different environments.

## Dashboard

The Databricks dashboard provides sales analysis, including revenue by region.

Current regions include:

- East
- North
- South
- West

The dashboard configuration is stored in:

```text
dev_staging.lvdash.json
```

## Security

Databricks credentials are not stored in the repository.

GitHub Actions uses repository secrets:

```text
DATABRICKS_HOST
DATABRICKS_TOKEN
```

These secrets are injected into the workflow during deployment.

## Technologies

- Databricks
- Databricks SQL
- Databricks Asset Bundles
- Databricks CLI
- GitHub
- GitHub Actions
- YAML

## Manual Deployment

The bundle can also be validated and deployed using the Databricks CLI:

```bash
databricks bundle validate -t prod
databricks bundle deploy -t prod
```

## CI/CD Workflow

A developer makes a change and pushes it to the `main` branch.

GitHub Actions automatically:

1. Checks out the repository.
2. Sets up the Databricks CLI.
3. Validates the Databricks Asset Bundle.
4. Deploys the bundle to the production target.

This removes the need for manual production deployment.

## Author

Om Dhamame

GitHub: https://github.com/ohmschrodinger
