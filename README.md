# Docker Utility Containers & Executing Commands

This docker utility container will help us execute npm commands without installing node in our machine. I've used node 20.10-alpine version in this project.

## How to run node in interactive mode as shell in our machine

```shell
docker run -it --rm --name node-util node:20.10-alpine
```

![image](https://github.com/actionanand/node-util/assets/46064269/0e99e84b-5c5a-4f87-880b-dda5e5e3526f)


## How to run node in interactive mode without any Dockerfile in terminal to use npm commands

```bash
docker run -it -d --rm --name node-util node:20.10-alpine
```

- Executing npm command (say `npm init`)

```bash
docker exec -it node-util npm init
```

The docker `exec` command helps us to execute(run) a new command inside the running container. 

![image](https://github.com/actionanand/node-util/assets/46064269/873a981b-fbdd-4a88-9b09-8971fbddbfde)

## Set-up using Dockerfile

1. Build the image

```shell
docker build . -t actionanand/node-util
```

2. You can run any command begining with `npm` (leave `npm` and add remaining at the end of following command)

```bash
docker run -it --rm --name node-util -v "D:\AR_extra\rnd\docker\node-util:/app" actionanand/node-util
```

For wsl2, mac and linux

```bash
docker run -it --rm --name node-util -v $(pwd):/app actionanand/node-util
```

To run `npm init` command

```bash
docker run -it --rm --name node-util -v $(pwd):/app actionanand/node-util init
```

To run `npm install express`

```shell
docker run -it --rm --name node-util -v $(pwd):/app actionanand/node-util install express
```

![image](https://github.com/actionanand/node-util/assets/46064269/76df332e-3c6f-483f-a7f7-9e44975eac4c)


## Set-up using docker-compose

* `docker-compose run` is used to run **single service** from multiple services present indide `docker-compose.yaml`

Usage

```bash
docker-compose run --rm <service_name>
```

Consider `npm-util` is the registered service name in `docker-compose.yaml` and If you want to execute `npm init`, the following will be the command to be executed!

```bash
docker-compose run --rm npm-util init
```

So if `npm` is the registered service name,

```bash
docker-compose run --rm npm init
```

### Docker Image's public URL

* [actionanand/node-util](https://hub.docker.com/r/actionanand/node-util)


## Associated repos:

1. [Docker Basics](https://github.com/actionanand/docker_playground)
2. [Managing Data and working with volumes](https://github.com/actionanand/docker_data_volume)
3. [Docker Communication](https://github.com/actionanand/docker_communication)
4. [Docker Multi-container with docker-compose](https://github.com/actionanand/docker_multi-container)
5. [Docker Utility Containers & Executing Commands](https://github.com/actionanand/node-util)
