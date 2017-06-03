# DOCKER NOTES
Notes I've accumulated while getting started with Docker

---

# Dockerfile

Instructions on how to build the image

`ARG`
- "The ARG instruction defines a variable that users can pass at build-time to the builder with the docker build command using the --build-arg <varname>=<value> flag"

```
ARG USERNAME=exampleusername
RUN useradd $USERNAME
```

`FROM`

`COPY example.js .`
- Copies `./example.js` from project into our image

`EXPOSE PORT`
- Like forwarding a PORT through Docker's built in 'firewall'
- Docker container listens on PORT 8000 by default

`CMD`
- Excutable command to run usually found at the end of our Dockerfile
- Common command is `node index.js`

## Build The Container

`docker build -t EXAMPLE ./EXAMPLE-DOCKERFILE-PATH` // <== docker containers require a relative path as the final parameter. You will forget this and struggle to figure out why nothings working.. And that's okay.. Welcome to Docker

# ******* #
# WARNING #
# ******* #

- `-t` means different things to differnt events in a Docker container's lifecycle, as do other shorthand flags, such as `-p`, `-d`, `-Esf` (shorthand for `--EXAMPLE-shorthand-flag`)

- we may also chain together shorthand commands, but i advise against doing so, and suggest you instead type out the commands verbatim

## Run the container

`docker run -d -p PORT:PORT --name EXAMPLE`
- `-p` maps a host port to a container port
- `-d` run docker image as background daemon
- `--name` assigns name to container

Verify container was built locally by opening `http://localhost:PORT`

## Container Lifecycle

`run`
 - image --> container

`start`
 - container --> running container

`stop`
 - running container --> container

`attach`
  - make changes

`commit -m "commit message here" DOCKER_TAG_ID`

`tag`
  - `docker tag IMAGE-REPOSITORY:IMAGE-TAG GCLOUD_REGION.gcr.io/GCLOUD_PROJECT_NAME/IMAGE-REPOSITORY:IMAGE-TAG`
  - see `push` for next step

`push`
  - to your preferred Docker container registry
  - `gcloud docker -- push GCLOUD_REGION.gcr.io/GCLOUD_PROJECT_NAME/IMAGE-REPOSITORY:IMAGE-TAG`
  - see `tag` for previous step

---

# Tools

- [dockviz](https://github.com/justone/dockviz) cli for simpler, less noisy docker inspection, and visualization

-[Docker-logs bash script](https://gist.github.com/yarcowang/370e63e68972afbff970)

---

# Questions

Where does kubernetes fit into the picture?

A Docker container has how many nodes/pods/clusters/pools? and what are the relationship(s) between these terms?

What does the lifecycle of a container look like?
  - image <-> container <-> started container <-> attached container <-> stopped container <-> etc.

---

# Docker Components
(documenting on an on-going basis. May not be accurate explanation(s)

- `Id`
  - key

- `Container`
  - key

- `Hostname`
  - key

- `layers`
  - chronological many sha hashes

---

# Docker CLI

(all commands have to be prepended with `docker `)

`attach`

`build`

`commit`

`container`

`diff`

`history`

`image`

`images`

`inspect`

`kill`

`logs`

`ps`

`ps -a`

`pull`

`push`

`rename`

`rm`

`rm -f` \\ or `--force`

`run`

`start`

`tag`

`stop`

---

Following attachment to Docker container.. Here are some useful linux commands

`adduser --disabled-password --gecos '' NAME_OF_NEW_USER`

`apt-get install vim`

`apt-get update`

`exit`

`npm install --quiet`

`touch .env`

---

# Docker File Structure

-- `.docker-compose.yaml` (may also be .docker-compose.yml)

-- `.dockercfg` (Kubernetes exclusive?)

-- `.dockerignore`

-- `Dockerfile`

-- `app.yaml` (Google Cloud)

---

# ----------------------- #
# Common `image` Commands #
# ----------------------- #

-- `docker images`                             // note the second argument, `image__s__` is plural && lists all local images

-- `docker image rm EXAMPLE-IMAGE-REPOSITORY` // note the second argument, `image`, is singular

-- `docker image rm __-f__ EXAMPLE-IMAGE-REPOSITY` // __force__ remove image

# ------- #
# WARNING #
# ------- #

- You will repeatedly run the wrong force remove command (`docker -rm -rf`) // the `-r` being extrenuous

 - This happens because we've developed a bad habit of force removing all the things. Be careful force removing anything inside containers as irreconcilable damage to critical infastruture isn't hard to come by if you don't know what you're doing


---

---

# Other useful commands

`docker images -f "dangling=true" -q`
- print dangling, useless images to console
- useful for exposing cached images with `<none>` tag following image cleanups

`docker image prune`
- remove all dangling images

`docker exec -it "EXAMPLE-ID-OF-RUNNING-CONTAINER" bash` // run `docker ps` to see a list of running containers, and `docker ps -a` to see a list of all containers, running, or static
