# Docker Swarm Installation with Ansible

This repository contains an Ansible playbook to set up a Docker Swarm cluster on any number of nodes. The playbook handles the installation of Docker, configuration of the nodes, and the initialization of the Docker Swarm manager.

## Prerequisites

- Ansible installed on your control machine.
- SSH access to all the nodes that will be part of the Swarm cluster.
- Ensure that all nodes have their hostnames correctly set and can resolve each other (e.g., via `/etc/hosts` or DNS).

## Inventory

The inventory file `hosts` is used to define the nodes that will participate in the Docker Swarm cluster. Modify this file to include your nodes.

### Example `hosts` file:

```ini
[docker_managers]
  docker-p01
  docker-p03
[docker_workers]
  docker-p01
  docker-p02
[docker_swarm:children]
  docker_managers
  docker_workers
