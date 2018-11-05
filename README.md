# Jenkins JNLP Slave with Docker in Docker

A JNLP Slave Docker image with docker and docker-compose installed. We use this with the Jenkins ECS plugin to
automatically provision Jenkins slaves which then can use Docker to run their jobs.

You can either connect via the Docker socket like this:

```sh
docker run \
    -v /var/run/docker.sock:/var/run/docker.sock \
    yanqd0/jnlp-dind-slave \
    docker ps
```

Or better, connect to some external Docker deamon via TCP:

```sh
docker run \
    -e DOCKER_HOST=dind \
    yanqd0/jnlp-dind-slave \
    docker ps
```

See the [docker-compose.yml](docker-compose.yml) file for reference.

## Version

| Name          | Version |
| ----          | ------: |
| Debian        | Stretch |
| OpenJDK       | 8       |
| Git           | 2.18.0  |
| Jenkins slave | 3.27    |
| Docker        | 17.06.2 |
| docker-cmpose | 1.18.0  |

It is welcome to remind me to update by [issues].

[issues]:https://github.com/yanqd0/jnlp-dind-slave/issues/new

## License

[![License](https://img.shields.io/github/license/yanqd0/jnlp-dind-slave.svg)](https://github.com/yanqd0/jnlp-dind-slave/blob/master/LICENSE)

This repository is forked from [ninech/jnlp-slave-with-docker], which is not maintained.

[ninech/jnlp-slave-with-docker]:https://github.com/ninech/jnlp-slave-with-docker
