# docker-interview-questions

# Docker Interview Questions

## 1. What is the difference between an Image, Container and Engine?

### Docker Engine

Docker Engine, now known as Docker Desktop or simply Docker, is a platform for developing, shipping, and running applications inside containers. Containers are lightweight and portable environments that package applications and their dependencies, allowing them to run consistently across different environments.

Docker engine comprises the docker daemon, an API interface, and Docker CLI.

### The Docker daemon

The Docker daemon (`dockerd`) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons (containerd) to manage Docker services. Docker daemon (dockerd) runs continuously as `dockerd` systemd service.

### The Docker client

The Docker client (`docker`) is the primary way that many Docker users interact with Docker. When you use commands such as `docker run`, the client sends these commands to `dockerd`, which carries them out. The `docker` command uses the Docker API. The Docker client can communicate with more than one daemon.

![dockerArchitecture1](https://github.com/kunal-gohrani/docker-interview-questions/assets/47574597/d8e62301-574e-4215-877d-0e6848c6edf6)


Credits: [devopscube.com](https://devopscube.com/what-is-docker/)

![dockerArchitecture2](https://github.com/kunal-gohrani/docker-interview-questions/assets/47574597/7619aa20-ce46-4ff1-8cb6-84b0126d6aef)

Credits: [devopscube.com](https://devopscube.com/what-is-docker/)

### Difference between Docker Images and Containers

| Docker Image | Docker Container |
| --- | --- |
| It is a blueprint of the Container. | It is an instance of the Image. |
| Image is a logical entity. | The container is a real-world entity. |
| Images are created only once. | Containers are created any number of times using an image. |
| Images are immutable. One cannot attach volumes and networks. | Containers change only if the old image is deleted and a new one is used to build the container. One can attach volumes, networks, etc. |
| Images do not require computing resources to work. | Containers require computing resources to run as they run with a Docker Virtual Machine. |
| To make a docker image, you have to write a script in a Dockerfile. | To make a container from an image, you have to run the “docker run <image>” command |
| Docker Images are used to package up applications and pre-configured server environments. | Containers use server information and a file system provided by an image in order to operate. |
| Images can be shared on Docker Hub. | It makes no sense in sharing a running entity, always docker images are shared. |
| There is no such thing as a running state of a Docker Image. | Containers use RAM when created and in a running state. |
| An image must not refer to any state to remove the image. | A container must be in a running state to remove it. |
| One cannot connect to the images as these images are like snapshots. | In this, one cannot connect them and execute the commands. |
| Sharing of Docker Images is possible. | Sharing of containers is not possible directly. |
| It has multiple read-only layers. | It has a single writable layer. |
| These image templates can exist in isolation. | These containers cannot exist without images. |

Credits: [GeeksForGeeks](https://www.geeksforgeeks.org/difference-between-docker-image-and-container/)

## 2. What is runC shown in this diagram?

![dockerArchitecture2](https://github.com/kunal-gohrani/docker-interview-questions/assets/47574597/787530e9-e81e-468f-9de7-98091626500f)


runC is a lightweight, portable container runtime. It includes all of the plumbing code used by Docker to interact with system features related to containers. It is designed with the following principles in mind:

- Designed for security.
- Usable at large scale, in production, today.
- No dependency on the rest of the Docker platform: just the container runtime and nothing else.

The goal of runC is to make standard containers available everywhere

Click [here](https://www.docker.com/blog/runc/#:~:text=Introducing%20runC%3A%20The%20universal%20container%20runtime) to get full overview of runC.

## 3. What is containerd? Explain the difference between dockerd and containerd.

**Explanation with analogy**

Think of **`dockerd`** as the captain of a ship, and **`containerd`** as the crew members who handle the cargo.

- **dockerd**: This is like the main manager in charge of everything related to containers. It's like the boss that takes care of creating, managing, and running containers. Just as a captain navigates the ship, **`dockerd`** navigates the world of containers.
- **containerd**: This is like the crew that actually handles the containers. It's responsible for the low-level operations of containers, like starting them up, stopping them, and managing their resources. Containerd works under the guidance of **`dockerd`**, similar to how deckhands work under the captain's instructions.

**Technical Explanation:**

- **dockerd**: **`dockerd`** is the Docker daemon, which is a background service that manages Docker containers on a system. It listens to the Docker API and handles tasks like building images, creating and running containers, networking, and storage. It's responsible for the high-level container management tasks and provides a convenient user interface through the Docker command-line interface (CLI) or APIs.
- **containerd**: **`containerd`** is a container runtime that is used by **`dockerd`** to manage container operations. It is responsible for lower-level container operations, such as pulling container images, starting and stopping containers, and managing their lifecycle. **`containerd`** provides a set of APIs that allow higher-level tools, like **`dockerd`**, to interact with containers without needing to deal with the nitty-gritty details.

In summary, **`dockerd`** is the overarching manager that handles user interactions and high-level container management, while **`containerd`** is the engine that performs the actual container operations under the guidance of **`dockerd`**.

Read more about containerd [here](https://www.docker.com/blog/what-is-containerd-runtime/)

Read more about difference between dockerd and containerd [here](https://kodekloud.com/blog/docker-vs-containerd/#)

## 4. Why and when to use Docker?

Docker can be highly useful in organizations for various reasons:

- Consistency: Docker containers package applications and their dependencies into a standardized unit. This ensures that applications run consistently across different environments, from a developer's laptop to production servers. This consistency reduces the "it works on my machine" problem, making it easier to deploy and manage applications.
- Isolation: Docker containers provide process and file system isolation, allowing multiple applications to run securely on the same host without interfering with each other. This isolation is particularly valuable in a shared infrastructure or multi-tenant environment.
- Resource Efficiency: Containers are lightweight and share the host OS's kernel, which means they consume fewer resources compared to traditional virtual machines. This efficient resource usage can lead to cost savings in terms of hardware and cloud resources.
- Rapid Deployment: Docker containers can be started and stopped quickly, enabling rapid application deployment and scaling. This agility is essential for modern, fast-paced development and deployment pipelines.
- Version Control: Docker images can be versioned, providing a clear and reproducible history of an application's changes over time. This helps in tracking changes, rolling back to previous versions, and ensuring consistency in different environments.
- Collaboration: Docker images and containers can be easily shared. Developers can create a Docker image of their application, share it with colleagues or team members, and ensure that everyone is working with the same environment.
- Continuous Integration and Continuous Deployment (CI/CD): Docker containers are often used in CI/CD pipelines to automate testing, integration, and deployment processes. This accelerates development cycles and ensures that code changes can be quickly and reliably delivered to production.
- Microservices Architecture: Docker is well-suited for microservices architecture, where applications are broken down into smaller, independently deployable services. Each service can run in its own container, making it easier to develop, scale, and maintain complex applications.
- DevOps Practices: Docker supports DevOps practices by enabling collaboration between development and operations teams. Developers can define the application's environment in a Dockerfile, and operations teams can use Docker Compose or orchestration tools like Kubernetes to manage and scale containers in production.
- Hybrid and Multi-Cloud: Docker's portability allows organizations to deploy containers across hybrid and multi-cloud environments. This flexibility is valuable for organizations that want to avoid vendor lock-in and have the freedom to choose their infrastructure providers.
- Security: Docker provides security features such as container isolation, user namespaces, and image signing. These features help organizations run applications securely in containers.
- Scalability: Containers can be easily scaled up or down to meet changing workloads. Docker orchestration tools like Kubernetes and Docker Swarm simplify container scaling and management.
- Cost Savings: Docker's efficient resource usage can lead to cost savings, both in terms of hardware and cloud infrastructure. Organizations can optimize their infrastructure spending by using containers effectively.

Overall, Docker Engine can significantly improve an organization's agility, reliability, and efficiency in application development, deployment, and management. However, it's essential to implement Docker best practices and consider factors like security, monitoring, and container orchestration when using Docker in a production environment.

## 5. What is the difference between the docker file commands COPY & RUN?

- **COPY**: The **`COPY`** instruction in a Dockerfile copies files or directories from the host machine to the container's filesystem at a specified location. This is mainly used to include files that are needed for the application to run correctly. For example:
    
    ```docker
    COPY ./src/app /app
    ```
    
    This would copy the contents of the **`./src/app`** directory from the host to the **`/app`** directory within the container.
    
- **RUN**: The **`RUN`** instruction is used to execute commands while building the Docker image. These commands can be used to install packages, configure settings, or perform any other necessary tasks. For example:
    
    ```docker
    
    RUN apt-get update && apt-get install -y python3
    ```
    
    This command would update the package list and then install Python 3 during the image build process.
    

## 6. What is the Difference between the Docker command CMD vs RUN?

The **`CMD`** instruction in a Dockerfile specifies the default command and its arguments that will be executed when a container is started from the image. It's not run during image build; rather, it defines what the container should run when it's started. For example:

```docker
CMD ["python", "app.py"]
```

This sets the default command to run the **`app.py`** script using the Python interpreter when the container starts.

- **RUN**: The **`RUN`** instruction, as mentioned before, is used during image build. It specifies commands that are executed inside the container during image construction. These commands are used to prepare the environment, install software, set up configurations, and perform other tasks that are necessary for the image to work correctly when containers are run from it. For example:

```docker
RUN apt-get update && apt-get install -y python3
```

This command is executed during image build to install Python 3 and its dependencies.

## 7. Can you explain the concepts of namespaces and cgroups and how is it used in docker?

**Simple Explanation with Examples:**

**Namespaces** can be thought of as virtual compartments that isolate different aspects of a container, like rooms in a house. For example, each container might have its own "room" for processes, "room" for networking, "room" for file systems, and so on. This keeps things separate so that containers don't interfere with each other.

**cgroups** are like traffic cops for resources. Imagine you're at a buffet with many people. Each person (process) can eat only a certain amount of food (resources) so that no one person hogs everything. Similarly, cgroups control how much CPU, memory, and other resources a container can use.

**Technical Explanation:**

- **Namespaces**: In the context of Docker, namespaces are a Linux kernel feature that provide isolation by creating separate instances of global resources for each container. These namespaces include:
    - **PID namespace**: Isolates the process IDs, so processes inside a container have their own isolated view of the process tree.
    - **Network namespace**: Separates network interfaces and routing tables, allowing containers to have their own network configurations.
    - **Mount namespace**: Provides an isolated file system view, allowing each container to have its own root file system.
    - **UTS namespace**: Isolates hostname and domain name, ensuring containers can have their own hostname.
    - **IPC namespace**: Separates inter-process communication resources, like shared memory and message queues, keeping containers independent.
    - **User namespace**: Allows containers to have their own range of user and group IDs, enhancing security.
- **cgroups**: Control Groups (cgroups) are a Linux kernel feature that manage and limit the resources used by processes or groups of processes. Docker uses cgroups to allocate resources to containers, preventing one container from consuming all available resources and impacting others. Cgroups can limit CPU usage, memory usage, disk I/O, and more. For instance, you can specify that a container should only use 50% of the CPU and a certain amount of memory, ensuring fair resource allocation.

In summary, namespaces provide isolation by creating separate environments for containers, and cgroups manage and limit the resources that containers can use.

## 8. How will you reduce the size of the Docker image? Why do we prefer to reduce image size?

There’s a great blog [here](https://devopscube.com/reduce-docker-image-size/) which explains this in detail.

## 9. What is a hypervisor? can you explain the difference between docker & hypervisor?

**Hypervisor:**

A hypervisor is a software or hardware component that creates and manages virtual machines (VMs) on a physical host machine. It allows you to run multiple operating systems and their applications on a single physical server. Hypervisors provide isolation between VMs, enabling each VM to have its own dedicated resources, such as CPU, memory, storage, and network. There are two main types of hypervisors:

1. **Type 1 Hypervisor (Bare Metal Hypervisor):** This hypervisor runs directly on the physical hardware without the need for an underlying operating system. It provides better performance and security as it has direct control over hardware resources. Examples include VMware vSphere/ESXi, Microsoft Hyper-V, and Xen.
2. **Type 2 Hypervisor (Hosted Hypervisor):** This hypervisor runs on top of an existing operating system and manages VMs as processes. It is easier to set up and use but comes with some performance overhead due to its reliance on the underlying host OS. Examples include VMware Workstation, Oracle VirtualBox, and Parallels Desktop.

**Differences between Hypervisor and Docker:**

While both hypervisors and Docker provide virtualization and isolation, they operate at different levels and are designed for different use cases:

1. **Level of Abstraction:**
    - **Hypervisor:** Hypervisors create full virtual machines, each with its own operating system and kernel. This approach provides strong isolation but can be resource-intensive due to the need for multiple OS instances.
    - **Docker:** Docker uses containerization, where containers share the host operating system's kernel and libraries. This makes containers lightweight and enables them to start faster and consume fewer resources compared to full VMs.
2. **Resource Efficiency:**
    - **Hypervisor:** VMs in a hypervisor environment consume more resources because each VM includes its own full operating system.
    - **Docker:** Containers share the host OS kernel and libraries, making them more efficient in terms of resource utilization.
3. **Performance:**
    - **Hypervisor:** VMs can introduce performance overhead due to the need to manage multiple operating systems.
    - **Docker:** Containers perform better due to their lightweight nature and shared kernel.
4. **Isolation:**
    - **Hypervisor:** VMs provide stronger isolation between instances as they have their own separate kernels and OS instances.
    - **Docker:** Containers are less isolated compared to VMs because they share the host OS kernel. However, Docker provides sufficient isolation for most use cases.
5. **Use Cases:**
    - **Hypervisor:** Hypervisors are ideal for scenarios where strong isolation between multiple OS instances is required, such as running different operating systems on the same physical hardware.
    - **Docker:** Docker is suited for deploying and managing applications in a consistent and reproducible manner. It's commonly used in DevOps, microservices architecture, and application deployment.
    
    ## 10. What is the difference between CMD & ENTRYPOINT?
    
    **CMD**: **Sets default parameters that can be overridden from the Docker command line interface (CLI) while running a docker container.** The **`CMD`** instruction in a Dockerfile specifies the default command to run when a container starts based on the image. If a command is provided to the **`docker run`** command, it overrides the **`CMD`**. For example:
    
    ```docker
    CMD ["python", "app.py"]
    ```
    
    If you run the container without specifying a command, it will run **`python app.py`** by default.
    
    **ENTRYPOINT**: **Sets default parameters that cannot be overridden while executing Docker containers with CLI parameters.** The **`ENTRYPOINT`** instruction is similar to **`CMD`**, but it defines the main command that is always executed when the container starts. If a command is provided to the **`docker run`** command, it becomes additional arguments to the **`ENTRYPOINT`**. For example:
    
    ```docker
    ENTRYPOINT ["python", "app.py"]
    ```
    
    Running the container with **`docker run myimage arg1 arg2`** would execute **`python app.py arg1 arg2`**.
    
    In summary, both **`CMD`** and **`ENTRYPOINT`** specify the command to run when the container starts, but the key difference is that with **`ENTRYPOINT`**, the specified command is not easily overridden by command-line arguments.
    
    ## 11. Explain docker stop, docker restart, docker kill commands and what happens to the data in the container in each case?
    
    **Container Stopped:**
    When a container is gracefully stopped using the **`docker stop`** command, the following happens:
    
    - The main process inside the container receives a termination signal (SIGTERM).
    - The process is given a chance to perform cleanup tasks or save any necessary data.
    - After a grace period (by default, 10 seconds), if the process hasn't exited, Docker will forcefully stop the container.
    
    Data in the container filesystem is retained unless you remove the container explicitly. If you've used volumes, the data in the volume persists beyond the container's lifecycle.
    
    **Container Killed:**
    When a container is forcefully killed using the **`docker kill`** command, the following happens:
    
    - The main process inside the container receives a termination signal (SIGKILL) immediately, without any chance to perform cleanup.
    - The container stops abruptly, and any data changes that weren't written to a volume or bind mount might be lost.
    
    **Container Restarted:**
    When a container is restarted using the **`docker restart`** command or by stopping and starting it again:
    
    - The container is first stopped (a grace period is given for cleanup if using **`docker restart`**).
    - The container is then started again, typically with the same configuration as before.
    
    Data in the container filesystem is retained unless you remove the container explicitly. If you've used volumes, the data in the volume persists beyond the container's restart.
    
    In summary:
    
    - Containers that are gracefully stopped or restarted generally retain their filesystem data unless removed explicitly.
    - Containers that are forcefully killed may lose any data changes that weren't saved to volumes.
    - Data in volumes persists beyond the container lifecycle and can be accessed by other containers even after the original container is removed.
    
    ## 12. List down different network drivers available in docker.
    
    1. Bridge Driver
    2. Host Driver
    3. Overaly Driver
    4. MACVLAN Driver
    5. None
    
    Learn more about docker network drivers in this great tutorial: [https://youtu.be/bKFMS5C4CG0?si=LkcK_oxnVRSkqZBI](https://youtu.be/bKFMS5C4CG0?si=LkcK_oxnVRSkqZBI)
    
    ## 13. If Docker requires a linux kernel to function, If so, how does it work in Windows & MacOS?
    
    Yes, Docker requires a Linux kernel to function. Docker relies on several Linux kernel features to provide its containerization and isolation capabilities. These features are fundamental to how Docker containers work.
    
    Here are some key Linux kernel features that Docker utilizes:
    
    1. **Namespaces:** Docker uses namespaces to create isolated environments for processes, networking, filesystems, and other resources. Namespaces ensure that containers can run independently of each other and do not interfere with each other's operations.
    2. **Control Groups (cgroups):** Docker uses cgroups to manage and limit resource usage for containers. Cgroups allow you to allocate CPU, memory, disk I/O, and other resources to containers, preventing one container from monopolizing resources.
    3. **Union Filesystems (UnionFS):** Docker employs UnionFS or other similar filesystem technologies (like OverlayFS) to layer filesystems and provide efficient image layering, which helps in creating lightweight and shareable container images.
    
    These Linux kernel features are essential for the core functionality of Docker, providing the isolation and resource management that make containers possible. As a result, Docker is primarily compatible with Linux-based systems. However, Docker also provides solutions like Docker Desktop for Mac and Windows that run a lightweight Linux VM to enable Docker usage on non-Linux platforms, effectively providing a Linux environment for Docker to operate within.

   ## 14. What’s the difference between COPY & ADD command? Explain it’s importance
    
    Both the **`COPY`** and **`ADD`** commands in Docker are used to copy files and directories from the host into the image's filesystem. However, there are some differences between them. Let's explore these differences using code snippets:
    
    **COPY Command:**
    
    The **`COPY`** command is used to copy files or directories from the host into the image's filesystem. It is a straightforward way to include local files in the image.
    
    ```docker
    # Dockerfile
    FROM ubuntu:latest
    COPY app.py /app/
    ```
    
    **ADD Command:**
    
    The **`ADD`** command also copies files and directories from the host into the image's filesystem, but it has some additional capabilities. It can handle URLs and automatically extract compressed files.
    
    ```docker
    # Dockerfile
    FROM ubuntu:latest
    ADD https://example.com/my-app.tar.gz /app/
    ```
    
    in this example, the **`my-app.tar.gz`** archive is downloaded from a URL and extracted into the **`/app/`** directory within the image.
    
    **Best Practice:**
    
    - It's recommended to use **`COPY`** for most cases where you want to copy local files into the image.
    - Use **`ADD`** when you specifically need its additional features like URL downloading or automatic extraction.

    ## 15. What is docker compose? When should we use it?
    
    Docker Compose is a tool for defining and running multi-container Docker applications. It allows you to describe your application's     services, networks, and volumes in a single **`docker-compose.yml`** file, and then use a single command to create and manage all the containers required to run your application.
    
    **Key Features of Docker Compose:**
    
    1. **Service Definitions:** You define your application's services, their configurations, and relationships in a YAML file. Each service can consist of one or more containers.
    2. **Networks and Volumes:** Docker Compose allows you to create custom networks and volumes for your application, making it easy to manage communication between containers and persist data.
    3. **Single Command:** With a single command (**`docker-compose up`**), you can start all the containers defined in your **`docker-compose.yml`** file.
    4. **Environment Variables:** You can use environment variables in your Compose file to provide dynamic configuration to your containers.
    5. **Scalability:** Docker Compose also supports scaling services, allowing you to run multiple instances of a service easily.
    6. **Easy Cleanup:** When you're done, you can use **`docker-compose down`** to stop and remove all the containers, networks, and volumes defined in the Compose file.
    
    **When to Use Docker Compose:**
    
    Docker Compose is particularly useful in the following scenarios:
    
    1. **Development Environments:** Docker Compose is great for setting up development environments with multiple interconnected containers. It allows developers to define complex stacks with ease.
    2. **Microservices:** If you're working with a microservices architecture, Docker Compose helps you define, deploy, and manage the different services that make up your application.
    3. **Testing:** Compose makes it easier to run integration tests, as you can define the test environment and dependencies in a single file.
    4. **Local Deployment:** Compose is an excellent choice for quickly deploying your application locally for testing and experimentation.
    5. **Demonstrations and Training:** When you need to showcase or teach the setup and interactions of multiple containers, Docker Compose simplifies the process.
    6. **CI/CD Pipelines:** You can use Docker Compose to define your application's services for testing within continuous integration and continuous deployment pipelines.
    
    ## 16. Write a docker compose yaml file used to run a 2 tier application containing a python backend server, and a mysql database, use networks, and a environment variables file to establish connection between the containers?
    
    Refer to this [file](https://github.com/kunal-gohrani/docker-interview-questions/blob/main/docker-compose.yaml)
