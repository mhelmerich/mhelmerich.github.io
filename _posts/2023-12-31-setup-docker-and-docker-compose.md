---
title: Setup docker, docker-compose and Dockge
author: max
date: 2023-12-31 15:30
categories: [homelab, documentation]
tags: [docker, docker-compose, portainer]
img_path: /assets/images/docker
image:
  path: /docker.png
  alt: Docker is a powerful Container solution
---

# Why we want to use docker
A little philosophy first. One of the key principles of effective homelabbing is to separate different groups of tasks into their own virtual machines (VMs). This approach makes it easier to manage and troubleshoot issues. For instance, you might have one VM dedicated to networking tasks, another for storage, a third for your media center, and yet another for your home assistant. Each VM operates independently, ensuring that one task doesn't interfere with another.

# Adding the docker repository to apt sources

To install docker we're adding docker to the apt repository:

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

# What is docker-compose?

Docker Compose is a tool for defining and managing multi-container Docker applications. It uses a YAML file (usually named docker-compose.yml) to specify the configuration of all the services in your application. This includes things like the Docker images to use, the ports to expose, the networks to connect to, and any environment variables needed.

# Install docker and docker compose

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

# Installing Dockge
Dockge is a good looking, lightweight and reactive stack oriented docker-compose manager.

```bash
# Create directories that store your stacks and stores Dockge's stack
mkdir -p /opt/stacks /opt/dockge
cd /opt/dockge

# Download the compose.yaml
curl https://raw.githubusercontent.com/louislam/dockge/master/compose.yaml --output compose.yaml

# Start the server
docker compose up -d
```

Dockge is now running on [http://localhost:5001](http://localhost:5001)

![Settings](dockge.png)


### How to update Dockge

```bash
cd /opt/dockge
docker compose pull && docker compose up -d
```

Now we're up and running to setup more services using docker-compose  neat! 