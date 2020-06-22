# Docker Notes

## What Is Docker

- Package applications into containers
- Runs applications in isolated environments.
- Similar to virtual machines but light weight and doesn't need an entire operating system.
- Guaranteed to work in other environments.

## Containers VS Virtual Machines

### Containers

- Abstraction at app layer that package code and dependencies together.
- Multiple containers can run on the same machine.
- Share OS kernel but runs as an isolated process in user space.
- Can boot up in seconds.
- Uses less disk space and memory whilst running.

### Virtual Machines

- Abstraction of physical hardware turning one server into many servers.
- Hypervisors allow multiple VMs on one machine.
- They include a full copy of the operating system and thus are slow to boot.

## Docker Image

- A template for creating an environment of your choice.
- Images can have snapshots (version).
- It has everything needed to run your app.
  - OS, software, dependencies.
- Registries are places where you can download images.
- Tags are used to define snapshots.

## Containers

- A running instance of an image.

## Volumes

- Allows us to share data between the host and container as well as between containers.

## Commands

- `docker images`: displays downloaded images.
- `docker run imageName:tag`: run an instance of an image using a specific tag.
- `docker run -d ...`: run an instance of an image in detached mode. This returns the container ID.
- `docker container ls`: displays running container.
- `docker ps`: does the same as above.
- `docker exec -it containerName command`: execute a command interactively within the specified container. To enter a bash shell you would do `docker exec -it containerName bash`.

## Gotchas

- If you get an error saying that the Docker daemon can't be connected to, you probably need to make sure the Docker application (daemon) is running.
  