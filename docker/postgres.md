# Docker Postgres Commands

---

## General

### Pull Image

docker pull [OPTIONS] NAME[:TAG|@DIGEST]

**Example:**
```docker pull postgres:latest```

<br>

### How To Create Image Container

docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

**Example** `docker run --name [my_container] -p [0000:0000] -d [image:version]`

- ```--name: give container a name```
- ```-p: port of container```
- ```-e: set env variable```
- ```-d: detach from container```

<br>

## How To List Containers

### Running Containers

**Example** `docker ps`

### Hidden Containers
**Example** `docker ps -a`

<br>

## How To Start Container

docker start [OPTIONS] CONTAINER [CONTAINER...]

**Example:** ```docker start my_container```

<br>

## Stop Docker Container

docker stop [OPTIONS] CONTAINER [CONTAINER...]

Example: ```docker stop my_container```

<br>

## Remove Docker Container

docker rm [OPTIONS] CONTAINER [CONTAINER...]

**Example:** ```docker rm my_container```

<br>

## See Docker Images

```docker image ls```

<br>

## Remove Docker images

docker image rm [OPTIONS] IMAGE [IMAGE...]

**Example:** ```docker image rm postgres```

<br>

## Postgres

### Create Container

```docker run --name local-db -p 5432:5432 -e POSTGRES_PASSWORD=revature -d postgres```

- ```--name: give container a name```
- ```-p: port of container```
- ```-e: set env variable```
- ```-d: detach from container```