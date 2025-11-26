# server

WIP - even the readme and the repo's name

A small, personal server project to run w/ Docker Compose.

Off the top of my head, should have these:

- Homarr (dashboard)
- Radarr (movies)
- Sonarr (tv shows)
- Nginx (lowkey no clue; still learning)
- Prowlarr & Privoxy (indexer manager)
- qBittorrent (download)
- Jackett (forgot)
- Gluetun (use qBittorrent w/ Mullvad, i think)

w/ plans to add:

- Images
- idk maybe store games

Table of Contents

- [Quick Start (Docker Compose)](#quick-start-docker-compose)
- [Configuration](#configuration)
- [Some Docker Compose Commands](#some-docker-compose-commands)
- [Deployment](#deployment-tips)

## Quick Start (Docker Compose)

Prerequisites:

- Docker (latest stable)
- Docker Compose (v2+; accessible through the docker CLI as `docker compose`)

Run the service:

1. Clone the repo:
   git clone <https://github.com/mintoleda/server2.git>
   cd server2

2. Start the service with Docker Compose (rebuild images if needed):
   docker compose up --build

   To run in the background:
   docker compose up -d --build

3. Stop the services:
   docker compose down

## Configuration

Configuration is provided via environment variables. You can supply them using a `.env` file in the project root or through your environment.

Note: Docker Compose automatically reads `.env` in the same directory as your `docker-compose.yml`. You can also use a `docker-compose.override.yml` for local overrides.

## Some Docker Compose Commands

- Start and build:
  docker compose up --build

- Start in background:
  docker compose up -d

- View logs:
  docker compose logs -f

- Recreate a single service:
  docker compose up -d --no-deps --build <service-name>

- Run a shell inside the running container (replace <service-name>):
  docker compose exec <service-name> sh
  docker compose exec <service-name> bash

- Stop and remove containers, networks:
  docker compose down

## Deployment

This project is container-first. Build images and push to your registry, then deploy using your orchestration platform (Kubernetes, ECS, etc.). Ensure environment variables and secrets are configured in your deployment environment.
