# Microservices with Node JS, React, Docker and Kubernetes
This project aims to set up the mini microservice with **Node JS, React, Docker and Kubernetes**.

## Microservices
Microservice architecture, or simply microservices, is a distintive method of developing software systems that tries to focus on building single-function modiels with well-defined interfaces and operatrions. The trend has grown popular in recent years as Enterprises look to become more Agile and move towards a DevOps and continuous testing.

## Docker
<p align="center">
    <img src="images/docker.png" width="324" height="280">
</P>

**[Docker](https://www.docker.com/)** is a set of platform as a service (PaaS) products that uses OS-level virtualisation to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries and configuration files; they can communicate with each other through well-defined channels. All containers are run by a single operating system kernel and therefore use fewer resources than virtual machines.

## Kubernetes
<p align="center">
    <img src="images/kubernates.png" width="324" height="280">
</P>

**[Kubernetes](https://kubernetes.io)**(K8s) is an open-source container-orchestration system for automating deployment, scaling and management. It was originally designed by Google, and is now maintained by the Cloud Native Computing Foundation. It aims to provide a "platform for automating deployment, scaling and operations of application containers across cluster of hosts. It works with a range of container tools, including Docker. Many cloud services offer a Kubernetes-based platform or infrastructure as a service (PaaS or laaS) on which Kubernetes can be deployed as a platform-providing service. Many vendors also provide their own branded Kuberneted distributions.

<!-- GETTING STARTED -->
## React Project
1. Download the project
```sh
git clone https://github.com/sseongha11/microservice-blog.git blog
```
2. move to client folder and check the files

## Docker files
1. Set up **Docker**

```sh
touch Dockerfile
touch .dockerignore
```
2. set up **Dockerfile (Case1: client folder [React App])**

| FROM | node:alpine | : Specify base image |
| WORKDIR | /app | : Set the working directory to '/app' in the container. All following commands will be issued relative to this dir |
| COPY | package.json ./ | : Copy over only the package.json file |
| RUN | npm install |: Install all dependencies |
| COPY | ./ ./ |: Copy over all of the remaining source codes |
| CMD | ["npm", "start"] |: Set the command to run when the container starts up |

```bash
FROM node:alpine

ENV CI=true

WORKDIR /app
COPY package.json ./
RUN npm install
COPY ./ ./

CMD ["npm", "start"]
```

3. Set up **Dockerfiles (Case2: comments, event-bus, moderation, posts and query folders)**

```bash
FROM node:alpine

WORKDIR /app
COPY package.json ./
RUN npm install
COPY ./ ./

CMD ["npm", "start"]
```

4. Set up **.dockerignore**

```bash
node_modules
```