## What is a Hypervisor?
**Answer:**  
A hypervisor is software that enables virtualization by dividing the host system and allocating resources to individually separated virtual environments. It is also known as a Virtual Machine Monitor (VMM). Hypervisors are categorized into two types:

- **Bare Metal Hypervisor (Native Hypervisor):** Runs directly on the primary host system and has direct access to the hardware, eliminating the need for a base server operating system.
- **Hosted Hypervisor:** Operates on an underlying host operating system.

## What is a Docker container?
**Answer:**  
Docker containers encapsulate applications and their dependencies, allowing them to run as isolated systems within their host operating system. Containers share the kernel and system resources with other containers, facilitating platform-independent deployment and execution of applications.

## What is a Dockerfile?
**Answer:**  
A Dockerfile is a text file that contains all the commands required to build a Docker image.

## What are Docker images?
**Answer:**  
Docker images are executable packages containing application code, dependencies, and software packages needed to create containers. These images can be deployed in any Docker environment to run containers and start the application.

## What is the Docker command that lists the status of all Docker containers?
**Answer:**  
To list the status of all containers, use the command:
```bash
docker ps -a
```

## What can you tell about Docker Compose?
**Answer:**  
Docker Compose is a tool that allows defining and sharing multi-container applications. You can create a YAML file to define services and manage them with a single command.

## What is Virtualization?
**Answer:**  
Virtualization is the process of creating a virtual version of hardware systems, storage, applications, etc., using a single hardware system. Hypervisor software is used to divide the system into various sections that operate as independent systems.

## What do you know about the Docker namespace?
**Answer:**  
A namespace is a Linux feature that partitions OS resources exclusively. In Docker, namespaces isolate containers, ensuring portability and protecting the underlying host. Docker supports PID, Mount, User, Network, and IPC namespace types.

## Explain Docker Architecture.
**Answer:**  
The Docker architecture consists of a client-server application called the Docker engine, which has three main components:
- **Daemon Process:** A server or long-running program.
- **REST API:** Specifies how programs communicate with daemons.
- **CLI Client:** Interacts with the daemon using REST API through CLI commands or scripts.

## When a Docker container exits, will your data be discarded?
**Answer:**  
No, data inside a container is automatically saved even after the container exits. Data is only deleted intentionally.

## Distinguish between virtualization and containerization.
**Answer:**  
- **Virtualization:** Simulates physical hardware, including a guest OS, kernel, processes, etc. Examples include VirtualBox and VMware.
- **Containerization:** OS-based virtualization that simulates the operating system, allowing multiple applications to share the same OS kernel. Examples include Docker.


## What is Docker Machine?
**Answer:**  
Docker Machine is a tool that allows you to install Docker Engine on virtual hosts. It also enables the management of these hosts using the `docker-machine` command and can create Docker Swarm clusters.

## Differentiate between COPY and ADD commands used in a Dockerfile.
**Answer:**  
Both commands copy files into the container, but:
- **COPY:** Copies local files.
- **ADD:** Copies files and supports additional features like extracting tar files and copying from remote URLs.

## Can a container restart automatically?
**Answer:**  
By default, containers do not restart automatically. However, they can restart automatically if the `--restart` flag is set with an appropriate policy.

## Is it okay to run stateful applications over Docker?
**Answer:**  
Running stateful applications in Docker is not recommended because they store data on the local file system, which makes it difficult to retrieve data if the application is moved to another device.

## Can we use JSON instead of YAML for Docker Compose files?
**Answer:**  
Yes, JSON can be used instead of YAML for Docker Compose files. Use the `-f` flag to specify the JSON file:
```bash
docker-compose -f docker-compose.json up
```

## Does Docker support IPv6?
**Answer:**  
Docker supports IPv6, but IPv6 networking is only available for Docker daemons running on Linux hosts. IPv6 support has been available since Docker Engine 1.5.

## How far do Docker containers scale? Are there any requirements for scaling?
**Answer:**  
Docker containers can scale up to hundreds of thousands or even millions. Requirements include sufficient memory, OS availability, and efficient use of resources.


## Where can you use Docker?
**Answer:**  
Docker is used in various areas such as:
- Application Isolation
- Multi-tenancy
- Debugging Capabilities
- Code Pipeline Management
- Developer Productivity
- Rapid Deployment
- Simplifying Configuration

## Will Docker Compose wait for a container to be ready before starting the next service?
**Answer:**  
Yes, Docker Compose runs according to dependency order, ensuring that containers are ready before starting dependent services.

## How will you monitor Docker in production?
**Answer:**  
Monitoring Docker in production involves using tools such as:
- AppOptics Docker Monitoring with APM
- Sematext
- Dynatrace
- cAdvisor
- Datadog
- Prometheus & Grafana
- Elasticsearch & Kibana
- SolarWinds Server & Application Monitor
- Splunk
- ManageEngine Applications Manager
- Sumo Logic
- Sysdig

## How many containers can run per host?
**Answer:**  
There is no set limit to the number of containers per host, but each container requires CPU, memory, and storage resources from the host system.

## Is it better to remove a container using the `rm` command directly or stop the container first?
**Answer:**  
It is best practice to stop the container first and then remove it using the `rm` command:
```bash
docker stop <container_id>
docker rm -f <container_id>
```
This approach ensures a clean removal process.

## What is the `docker-compose down` command?
**Answer:**  
The `docker-compose down` command stops containers and removes containers, networks, volumes, and images created by `docker-compose up`.

## Can you explain the Docker networking model?
**Answer:**  
Docker supports several networking drivers:
- **Bridge:** The default network driver, suitable for multiple containers on the same host.
- **Host:** Removes network isolation between the Docker container and the Docker host, making the container use the host’s networking directly.
- **Overlay:** Used for multi-host networking; it enables containers to communicate across different Docker daemons.
- **Macvlan:** Assigns a MAC address to each container, making it appear as a physical device on the network.
- **None:** Disables networking for the container.

## What is the purpose of the `docker exec` command?
**Answer:**  
The `docker exec` command is used to run commands inside an already running Docker container. For example, you can open a bash shell inside a running container using:
```bash
docker exec -it <container_id> /bin/bash
```

## What are Docker Volumes, and how do they work?
**Answer:**  
Docker volumes are used to persist data generated and used by Docker containers. They are stored on the host filesystem and can be shared between multiple containers. Volumes are managed by Docker and provide a better way to persist data than using bind mounts.

## What is the difference between Docker Volumes and Bind Mounts?
**Answer:**  
- **Volumes:** Managed by Docker, stored in a part of the host filesystem that’s managed by Docker, and suitable for sharing data between containers.
- **Bind Mounts:** Linked to a specific directory on the host's filesystem and provide more control over the data location, but they are less portable and harder to manage.

##  What is a Docker Registry?
**Answer:**  
A Docker Registry is a storage and content delivery system that stores Docker images. The public Docker Hub is the default registry, but you can also create a private registry for your organization using Docker’s open-source Registry project.

## What is the purpose of the Docker `ENTRYPOINT` instruction in a Dockerfile?
**Answer:**  
The `ENTRYPOINT` instruction in a Dockerfile defines the command that will always run when the container starts. Unlike `CMD`, which can be overridden by arguments passed to `docker run`, `ENTRYPOINT` is used when you want to ensure that a container executes a specific command.

## What is the difference between `CMD` and `ENTRYPOINT`?
**Answer:**  
- **CMD:** Provides default arguments for `ENTRYPOINT`. Can be overridden when starting a container.
- **ENTRYPOINT:** Specifies a command that is always executed when the container starts, even if arguments are provided with `docker run`.

## What is Docker multi-stage build?
**Answer:**  
Docker multi-stage builds allow you to use multiple `FROM` statements in a Dockerfile. This feature is useful for creating optimized Docker images by copying only the necessary artifacts from one stage to another, reducing the final image size.

## How can you share data between Docker containers?
**Answer:**  
Data can be shared between Docker containers using:
- **Volumes:** Shared storage that can be mounted to multiple containers.
- **Docker Networks:** Containers can share data over a common network.
- **Container Linking:** Legacy method for sharing data and environment variables between containers.

##  What are some Docker security best practices?
**Answer:**  
Some best practices for Docker security include:
- Use the latest Docker version.
- Scan images for vulnerabilities.
- Avoid running containers as root.
- Use signed images.
- Limit container capabilities using seccomp profiles.
- Secure the Docker daemon with TLS.
- Regularly update Docker images.

## What is Docker Overlay Network?
**Answer:**  
A Docker Overlay Network allows containers running on different Docker hosts to communicate with each other as if they were on the same local network. It’s commonly used in Docker Swarm to enable multi-host networking.

## Can you explain Docker Daemon Logs and how to access them?
**Answer:**  
Docker Daemon Logs record the operations and events occurring in the Docker engine. On Linux, you can access them using:
```bash
journalctl -u docker.service
```
On Windows, they are available via the Event Viewer under the Docker service.

## What is the difference between `docker-compose up` and `docker-compose run`?
**Answer:**  
- **`docker-compose up`:** Builds, (re)creates, starts, and attaches to containers for a service.
- **`docker-compose run`:** Runs a one-time command against a service. It doesn’t start linked services, only the specified service.

## What is the purpose of `docker network create`?
**Answer:**  
The `docker network create` command is used to create a new network that Docker containers can connect to. Networks provide a communication layer between containers.

## How does Docker handle environment variables?
**Answer:**  
Docker allows you to pass environment variables to containers using the `-e` flag with `docker run` or through environment files in Docker Compose. Environment variables are used to configure container behavior at runtime.

## What are the benefits of using Docker in CI/CD pipelines?
**Answer:**  
Docker in CI/CD pipelines offers several benefits:
- **Consistency:** Ensures the same environment across development, testing, and production.
- **Speed:** Speeds up builds and deployments by using lightweight containers.
- **Isolation:** Isolates applications, reducing dependency conflicts.
- **Scalability:** Easily scales testing and deployment processes.

## What is the role of Kubernetes with Docker?
**Answer:**  
Kubernetes is an orchestration tool that manages Docker containers in a clustered environment. It automates container deployment, scaling, and management, ensuring that applications run smoothly and efficiently across a cluster of nodes.

## How do you secure Docker images?
**Answer:**  
To secure Docker images:
- Use official images from trusted sources.
- Regularly scan images for vulnerabilities.
- Use minimal base images to reduce the attack surface.
- Apply updates and patches to images.
- Sign images using Docker Content Trust.

## Docker and Docker Compose difference

### Scope:
**Docker:** Manages individual containers and images. It is the foundational tool for containerization.
**Docker Compose:** Manages multi-container applications defined in a single configuration file. It simplifies the orchestration of complex setups involving multiple containers.

### Configuration:
**Docker:** Container configuration and orchestration are typically managed through individual docker run commands or Dockerfile scripts.
**Docker Compose:** Configuration is managed through a docker-compose.yml file, which defines multiple services, networks, and volumes in a declarative manner.

### Use Case:
**Docker:** Ideal for managing single-container applications or for running individual containers.
**Docker Compose:** Ideal for defining and managing multi-container applications, including setting up development environments and deploying complex applications.