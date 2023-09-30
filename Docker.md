# Docker

## What's Docker?

Docker is a tool that lets developers easily create, deploy and run applications in a consistent and reproducible environment. It does this through containers.  

A container is a standalone executable package of software that includes everything needed to run an application, including code, libraries, system tools and settings.  

Docker lets developers create container images that include applications and its dependencies, then deploy those images to systems that have Docker installed.  

A great deep dive into Containers: [Container Security](https://learning.oreilly.com/library/view/container-security/9781492056690/) by Liz Rice  

## The Container Analogy

A shipping container provides a standardized, secure and portable way to transport goods. Similarly, Docker provides a standardized, secure and portable way to transport software applications.

Additionally, just like how shipping containers are sealed and separated from one another, Docker containers provide isolation and ensure that applications are not affected by conflicts with other applications/the host system.

## VMs vs Containers

You may have heard of a Virtual Machine (VM) - a VM is simply a guest operating system that you can run on your host operating system and this is managed by a hypervisor. A container, on the other hand, involves building self-sufficient software packages that perform consistently, regardless of the machines they run on. Software developers create and deploy container images—files containing the necessary information to run the application. Container images are read-only and cannot be altered by the computer system.  

## Getting Started

Install Docker [here](https://www.docker.com/).

The Docker [getting-started](https://docs.docker.com/get-started/02_our_app/) tutorial is an excellent introduction to Docker.  

## A simple Dockerfile

```
FROM ubuntu:22.04
COPY . /app
RUN make /app
CMD python /app/app.py
```

What does this do?  

- `FROM` creates a layer from the `ubuntu:22.04` Docker image.
- `COPY` adds files from your Docker client's current directory.
- `RUN` builds your application with `make`.
- `CMD` specifies what commands you want to run within the container.

## Advice

- Learn how to write Dockerfiles, they will come in handy during projects / internships.
- A good resouce you can follow would be these [tutorials](https://www.bogotobogo.com/index.php).
- Starting with Docker is a good first step in learning Kubernetes, which is used by most major companies. I'd recommend spending some time learning about [what Kubernetes is](https://kubernetes.io/docs/concepts/overview/) and how companies use it, for general awareness.

