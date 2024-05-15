---
title: 50 Most Useful Docker CLI Commands
tags:
    - docker 
    - programming 
    - command
---

Here is a list of the 50 most useful Docker CLI commands: 

docker --version - Display the Docker version

docker images - List all Docker images

docker pull IMAGE_NAME - Pull a Docker image

docker run IMAGE_NAME - Run a Docker image

docker stop CONTAINER_ID - Stop a Docker container

docker start CONTAINER_ID - Start a Docker container

docker restart CONTAINER_ID - Restart a Docker container

docker kill CONTAINER_ID - Kill a Docker container

docker rm CONTAINER_ID - Remove a Docker container

docker ps - List all running Docker containers

docker ps -a - List all Docker containers, including stopped ones

docker inspect CONTAINER_ID - Get information about a Docker container

docker logs CONTAINER_ID - Get the logs for a Docker container

docker build -t IMAGE_NAME . - Build a Docker image from a Dockerfile

docker push IMAGE_NAME - Push a Docker image to a registry

docker tag IMAGE_NAME NEW_IMAGE_NAME - Tag a Docker image with a new name

docker login - Log in to a Docker registry

docker logout - Log out of a Docker registry

docker save IMAGE_NAME > IMAGE_NAME.tar - Save a Docker image to a tar file

docker load < IMAGE_NAME.tar - Load a Docker image from a tar file

docker volume create VOLUME_NAME - Create a Docker volume

docker volume ls - List all Docker volumes

docker volume inspect VOLUME_NAME - Get information about a Docker volume

docker volume rm VOLUME_NAME - Remove a Docker volume

docker network create NETWORK_NAME - Create a Docker network

docker network ls - List all Docker networks

docker network inspect NETWORK_NAME - Get information about a Docker network

docker network rm NETWORK_NAME - Remove a Docker network

docker swarm init - Initialize a Docker swarm

docker swarm join MANAGER_IP:2377 - Join a Docker swarm

docker swarm leave - Leave a Docker swarm

docker stack deploy STACK_NAME - Deploy a Docker stack

docker stack ps STACK_NAME - List all services in a Docker stack

docker stack services STACK_NAME - List all services in a Docker stack

docker stack deploy -c COMPOSE_FILE STACK_NAME - Deploy a Docker stack from a compose file

docker stack update STACK_NAME - Update a Docker stack

docker stack rollback STACK_NAME - Rollback a Docker stack

docker stack remove STACK_NAME - Remove a Docker stack

docker secret create SECRET_NAME SECRET_VALUE - Create a Docker secret

docker secret ls - List all Docker secrets

docker secret inspect SECRET_NAME - Get information about a Docker secret

docker secret rm SECRET_NAME - Remove a Docker secret

docker config create CONFIG_NAME CONFIG_VALUE - Create a Docker config

docker config ls - List all Docker configs

docker config inspect CONFIG_NAME - Get information about a Docker config

docker config rm CONFIG_NAME - Remove a Docker config

docker plugin install PLUGIN_NAME - Install a Docker plugin

docker plugin ls - List all Docker plugins

docker plugin inspect PLUGIN_NAME - Get information about a Docker plugin

docker plugin rm PLUGIN_NAME - Remove a Docker plugin