# DockerCloud CLI

A simple alpine image with docker & docker-cloud cli. Contrary to official 
[dockercloud/cli](https://hub.docker.com/r/dockercloud/cli/) image, it has 
docker binaries and has no entrypoint. Another advantage is latest tag 
follows latest Docker version available on Docker Cloud improvisioned 
machines (which is 1.11.2 at the moment of writing) and docker-cloud cli 
tested on real Docker Cloud stacks.

## Usage

Example for listing all stacks in `myorganization`:

```sh
docker run \
    -e DOCKERCLOUD_NAMESPACE=myorganization \
    -e DOCKERCLOUD_USER=username \
    -e DOCKERCLOUD_PASS=password \
    unumotors/dockercloud-cli \
    docker-cloud stack ls
```

### Docker Login

Login is available by either:

- passing `DOCKERCLOUD_USER` and `DOCKERCLOUD_PASS` environment variables
- running `docker login -u username -p password` subsequently before docker-cloud commands
- mounting docker's `config.json` to `/root/.docker/config.json` path

### Other commands

To see all available docker-cloud commands:

```sh
docker run \
    unumotors/dockercloud-cli \
    docker-cloud --help
```

## License

[MIT License](LICENSE)

Copyright (c) 2017 [unu GmbH](https://unumotors.com)
