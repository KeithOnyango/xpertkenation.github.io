---
layout: post
title: "The Magic Behind Docker Containerization"
date: 2024-02-03
categories: [DevOps]
tags: [DevOps, Docker]
---

# How Docker Works Internally: Magic Behind Containerization

Docker is a tool designed to simplify the process of creating, deploying, and running applications by using containerization. Containerization is a form of operating system virtualization, through which applications are run in isolated user spaces called containers, all using the same shared operating system (OS).

## Docker's Architecture

Docker uses a client-server architecture. The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers. The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon.

## Docker Internals

Docker uses a technology called namespaces to provide the isolated workspace called the container. When you run a container, Docker creates a set of namespaces for that container.

These namespaces provide a layer of isolation: they hold their own network stack, process tree, mount table, and so on. A container has limited access to its host system, and is essentially a user-space instance of the host machine.

Docker then starts a process in this new namespace. This process is isolated from all other processes running on the host machine.

## Docker Images and Containers

Docker uses a file system that is stacked on top of other file systems. This stackable file system is called a Union File System. Docker images are built up from a series of layers. Each layer represents an instruction in the image’s Dockerfile. When you run an image and generate a container, you add a new writable layer (the "container layer") on top of the underlying layers.

## Docker Registry

Docker Registry is a stateless, highly scalable server side application that stores and lets you distribute Docker images. It's open-source, under the permissive Apache license.

## Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration.

## Architectural Diagram

Here's a simplified architectural diagram of Docker:

```bash
+------------------+
|                  |
|  Docker Client   |
|                  |
+--------+---------+
         |
         v
+--------+---------+
|                  |
|  Docker Daemon   |
|                  |
+--------+---------+
         |
         v
+--------+---------+
|                  |
|  Docker Registry |
|                  |
+--------+---------+
         |
         v
+--------+---------+
|                  |
|  Docker Images   |
|                  |
+--------+---------+
         |
         v
+--------+---------+
|                  |
|  Docker Containers|
|                  |
+------------------+
```
