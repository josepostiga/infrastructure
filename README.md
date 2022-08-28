# Basic Infrastructure Repository

This repository contains basic Docker-related files to kickstart my projects.

## Docker Images

All pre-compiled Docker images are only compatible with arm64.


## Start Base Stack

The base stack is composed of a [Traefik Proxy](https://doc.traefik.io/traefik/) instance and allows to quickly connect other containers and route localhost requests to be routed to them.

Before anything, run `docker network create web`, then run `docker compose up -d` (or `docker-compose up -d` if you're not using Docker Compose V2) in the root folder of this repository.

# License

MIT
