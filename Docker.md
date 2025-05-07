__The Problem (Without Docker):__
- "It works on my machine!" syndrome.

- Even with the same software versions, differences in:

- Operating systems (Windows vs. macOS)

- CPU architecture (Intel vs. ARM)

- Installed dependencies

- Configuration settings

- Onboarding new team members becomes time-consuming.

- Deployments can behave differently than local environments.

+----------------------------------------+             +----------------------------------------+
|         Windows Environment            |             |          MacOS Environment             |
|----------------------------------------|             |----------------------------------------|
| OS: Windows 11                         |             | OS: MacOS                              |
| CPU: Intel                             |             | Node: v16                              |
| Node: v16                              |             | MongoDB: 5                             |
| MongoDB: 5                             |             | Redis: 6.0                             |
| Redis: 6.0                             |             |                                        |
|                                        |             |                                        |
|       [  Node.js Application  ]        |             |       [  Node.js Application  ]        |
+--------------------+-------------------+             +--------------------+-------------------+
                     |                                                      |
                     v                                                      v  
                   User                                                Another User

__How Docker Solves It:__
- Containerizes your entire application with its dependencies, runtime, and config.

- Runs identically across platforms (Windows, macOS, Linux).

- Simplifies:

  - Development

  - Testing

  - Deployment

- Ensures consistency from local dev to production.

+----------------------------------------------------+
|                 Docker Container: app              |
|----------------------------------------------------|
| Base Image: node:16                                |
| Source Code: /app                                  |
| Command: node index.js                             |
|                                                    |
|      [  Node.js Application (v16) ]                |
+------------------------+---------------------------+
                         |
                         v
          +------------------------------------+
          |    Docker Containers: Dependencies |
          |------------------------------------|
          | - MongoDB 5                        |
          | - Redis 6.0                        |
          +------------------------------------+

               Entire stack runs the same on:
          +--------------------------------------+
          | ✅ Windows   ✅ macOS   ✅ Linux    |
          +--------------------------------------+


### Docker Daemon
A daemon is a background process that runs continuously and handles requests or performs operations without user interaction.

In Docker, the Docker daemon (dockerd) is the core service that:

- Manages containers, images, volumes, and networks

- Listens for Docker API requests

- Runs in the background on your system

Image = Blueprint

Container = Running app based on the blueprint

eg: Windows(OS) is an image and the device you are using like laptop is a container



Commands:-
1. `docker run -it --name nametobe --network=networkname imagename(like ubuntu)` -> It will download the image if not present locally then run the image in a new container.
2. `docker container ls` -> It will show the running containers.
3. `docker container ls -a` -> It will show all the local containers.
4. `docker start/stop containername/containerid` -> It will start and stop the container respectively.
5. `docker exec containername/id command(like ls)` -> It will run the command inside the container and return to original terminal.
6. `docker exec -it containername/id bash` -> It will return us inside the container terminal.
7. `docker run -it -p machineportno:containerportno imagename` -> Map the port
8. `docker run -it -e key=value -e key=value imagename` -> To pass env variable
9. `docker build -t imagename .` -> To build docker image
10. `docker push imagename(same as repo name)` -> To push images to docker hub
11. `docker compose up` -> To run docker compose(-d for bg run)
11. `docker compose down` -> To remove docker compose
12. `docker network create networkname` -> To create custom network
13. `docker network inspect networkname` -> To inspect network
14. `docker run -it -v volname:containerpath imagename` -> To add volume(storage) to the image
15. `docker service create --name servicename --replicas replicanumber --publish port:portservice servicename` -> To create service in swarm
16. `docker service ls` -> To show all services
17. `docker rm servicename` -> To remove service
18. `docker service inspect --pretty servicename`
19. `docker service scale servicename/id=noofreplicas` -> To scale up/down the replicas
20. `docker update --availability drain/active serviceid`

### Docker Network
A Docker network is how containers communicate with each other and the outside world.

1. `Bridge` -> The bridge network is the default network driver when you run a container without specifying a network. This network allows containers on the same host to communicate with each other using IP addresses or container names as DNS resolution. However, it isolates the containers from the host and other containers on different hosts.

2. `Host` -> In this mode, containers share the same network namespace as the host machine, meaning they use the host’s IP address and port mappings. There is no isolation between the host and the container’s network.

3. `None` -> This mode completely disables networking for the container. The container has no access to any network, not even the default localhost. Containers in this mode cannot communicate with other containers or external systems.

4. `Overlay` -> An overlay network is used in Docker Swarm mode for orchestrating multi-host Docker setups. It allows containers running on different Docker hosts to communicate securely over a distributed network. Docker Swarm automatically creates and manages the overlay network, and it encrypts traffic between containers.

5. `Macvlan` -> A macvlan network allows containers to have their own unique MAC addresses, making them appear like separate physical devices on the network. This driver connects containers directly to the physical network, bypassing the Docker host’s virtual network layer.

### Volume Mounting

