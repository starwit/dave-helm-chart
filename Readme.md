# Deployment tools for DAVe
This repository contains deployment tools for installing the DAVe application. It was started and developed by the city of Munich and you can find more details [here](https://opensource.muenchen.de/de/software/dave.html).
DAVe is a software to collect, analyze and visualize traffic statistics. It is a multi-component software and thus deployment is not without complexity. Therefore you can find in this repository two ways of deployment: Docker compose and Helmfile. Docker compose is great for development setups and Helmfile is a convienient way to deploy & update composed multi-module applications in one go.

## Docker Compose
The `docker-compose` directory contains a `docker-compose.yaml` file that can be used to deploy the DAVe application using Docker Compose. This file defines the services, networks, and volumes needed to run the application. It is intended for local development environments and should __NOT__ be used in productive scenarios.

## Helmfile
Each individual DAVe component has its own Helm chart. In order to deploy them together Helmfile can be used. With Helmfile one can define and set variables, that are used for multiple components e.g. URLs for an identity provider. All necessary info can be found in folder [helmfile](helmfile/Readme.md).

# License 
Everything in this repo is pulblished under [MIT License](LICENSE)
