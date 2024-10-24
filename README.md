# Docker Compose files

Various Docker Compose files.

- [Kafka](./kafka/)
- [MySQL](./mysql)
- [NATS](./nats)
- [Redis](./redis)

## Setup

- `docker` - https://docs.docker.com/get-docker/
- `docker-compose` - https://docs.docker.com/compose/install/

## Commands

1. Start the container(s)

**NOTE: Optionally use the flag `-d` to run in the background and then `docker-compose down` to stop**

```bash
docker-compose up
```

2. Remove the container(s)

```bash
docker-compose rm
```

## License

The code has been licensed under [The Unlicense](https://opensource.org/license/unlicense) license.
