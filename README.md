# Jenkins JNLP Slave with Docker in Docker

A JNLP Slave Docker image with docker and docker-compose installed.

## Install

[![Build Status](https://travis-ci.org/yanqd0/jnlp-dind-slave.svg?branch=master)](https://travis-ci.org/yanqd0/jnlp-dind-slave)
[![Docker Build Status](https://img.shields.io/docker/build/yanqd0/jnlp-dind-slave.svg)](https://hub.docker.com/r/yanqd0/jnlp-dind-slave/builds/)
[![Docker Stars](https://img.shields.io/docker/stars/yanqd0/jnlp-dind-slave.svg)](https://hub.docker.com/r/yanqd0/jnlp-dind-slave/)
[![Docker Pulls](https://img.shields.io/docker/pulls/yanqd0/jnlp-dind-slave.svg)](https://hub.docker.com/r/yanqd0/jnlp-dind-slave/)

```sh
docker pull yanqd0/hugo
```

## Usage

You can either connect via the Docker socket like this:

```sh
docker run \
    -v /var/run/docker.sock:/var/run/docker.sock \
    --rm \
    --entrypoint bash \
    yanqd0/jnlp-dind-slave \
    -c 'docker version'
```

Or better, connect to some external Docker deamon via TCP:

```sh
docker run --rm --name dind -d --privileged --net host docker:dind
docker run \
    --rm \
    -e DOCKER_HOST=localhost \
    --net host \
    --entrypoint bash \
    yanqd0/jnlp-dind-slave \
    docker ps
```

There is a reference file [docker-compose.yml](docker-compose.yml),
which is not working directly.

## Version

| Name          | Version |
| ----          | ------: |
| Debian        | Stretch |
| OpenJDK       | 8       |
| Git           | 2.11.0  |
| Jenkins slave | 3.27    |
| Docker        | 18.09.0 |
| docker-cmpose | 1.23.2  |

It is welcome to remind me to update by [issues].

[issues]:https://github.com/yanqd0/jnlp-dind-slave/issues/new

## License

[![License](https://img.shields.io/github/license/yanqd0/jnlp-dind-slave.svg)](https://github.com/yanqd0/jnlp-dind-slave/blob/master/LICENSE)

This repository is forked from [ninech/jnlp-slave-with-docker], which is not maintained.

> Copyright (c) 2018~2019 Yan QiDong
> Copyright (c) 2018 nine

[ninech/jnlp-slave-with-docker]:https://github.com/ninech/jnlp-slave-with-docker
