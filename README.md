# DOCKER NOTES
Notes I've accumulated while getting started with Docker

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
