# Helmfile Deployment
Helmfile is a great tool to compose multi-component applications. Here you find information on how to deploy DAVe with Helmfile.

If you want to know more about Helmfile see [docs](https://helmfile.readthedocs.io/en/latest/)

## TL;DR

```bash
cp env.sh-template myenvironment-env.sh
# edit values
source myenvironment-env.sh
helmfile -e remote -f dave.yaml.gotmpl diff
# check if everything is correct
helmfile -e remote -f dave.yaml.gotmpl apply
```

## Deployment Overview
TODO

## Component Breakdown
The DAVe application consists of multiple components. Each component has its own Helm chart. The main components are:

| Component        | Repository / URI                                           | Description                  | Docker image | Helm Chart |
| -----------------| -----------------------------------------------------------| -----------------------------| -------------|------------|
| DAVe Backend     | https://github.com/starwit/dave-backend                    | Data Storage & Business Logic| [Link](https://hub.docker.com/r/starwitorg/dave-backend) | [Link](https://hub.docker.com/r/starwitorg/dave-backend-chart) |
| DAVe Frontend    | https://github.com/starwit/dave-frontend                   | Analytics Frontend           | [Link](https://hub.docker.com/r/starwitorg/dave-frontend) | [Link](https://hub.docker.com/r/starwitorg/dave-frontend-chart) |
| DAVe Admin Portal | https://github.com/starwit/dave-admin-portal              | Administration Frontend      | [Link](https://hub.docker.com/r/starwitorg/dave-adminportal) | [Link](https://hub.docker.com/r/starwitorg/dave-admin-portal-chart) |
| DAVe Self Service Portal | https://github.com/starwit/dave-selfservice-portal | Self-Service for data upload | [Link](https://hub.docker.com/r/starwitorg/dave-selfservice) | [Link](https://hub.docker.com/r/starwitorg/dave-selfservice-chart) |
| DAVe Adapter     | https://github.com/starwit/dave-adapter                    | Connects to data platforms   | [Link](https://hub.docker.com/r/starwitorg/dave-adapter) | [Link](https://hub.docker.com/r/starwitorg/dave-adapter-chart) |


## Using Helmfile
The following values are necessary to deploy DAVe.

```bash
# IdP data
export REALM_NAME=realmname
export CLIENT_SECRET=anothersecret

# Strong password for database
export DAVE_DB_PW=dave_db_pw

# Base URL to reach application
export HOSTNAME=cluster.local

# pull landing page from private repo
export GITHUB_TOKEN=token

# DAVe adapter config
export API_CLIENT_ID=dave_api
export API_CLIENT_SECRET=secret
export ANALYTICS_USERNAME=analytics
export ANALYTICS_PASSWORD=analytics
```