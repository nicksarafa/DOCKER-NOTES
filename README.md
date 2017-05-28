# DOCKER NOTES
Notes I've accumulated while getting started with Docker

---

# Dockerfile

Instructions on how to build the image

`FROM`

`COPY example.js .`
- Copies `./example.js` from project into our image

`EXPOSE PORT`
- Like forwarding a PORT through Docker's built in 'firewall'
- Docker container listens on PORT 8000 by default

`CMD`
- Excutable command to run usually found at the end of our Dockerfile
- Common command is `node index.js`

# Building the Dockerfile

`docker build -t mydockerexample`
- `-t` specifies the name of our Docker image

`docker run -p PORT:PORT mydockerexample`
- `-p` maps a host port to a container port

Verify container was built locally by opening `http://localhost:PORT`


# Container Lifecycle

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

# Other useful commands

`docker images -f "dangling=true" -q`
- print dangling, useless images to console
- useful for exposing cached images with `<none>` tag following image cleanups

`docker images prune`
- remove all dangling images
