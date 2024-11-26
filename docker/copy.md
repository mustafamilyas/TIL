# Copy Files from Docker Container to Host Machine or Vice Versa

To copy files from a Docker container to the host machine or vice versa, you can use the `docker cp` command.

## Copy Files from Docker Container to Host Machine

To copy files from a Docker container to the host machine, you can use the following command:

```bash
docker cp <container_id>:/path/to/file/on/container /path/to/file/on/host
# example
docker cp 1234567890:/app/package.json /tmp/package.json
```

You can also use the container name instead of the container ID.

```bash
docker cp <container_name>:/path/to/file/on/container /path/to/file/on/host
# example
docker cp my-container:/app/package.json /tmp/package.json
```

## Copy Files from Host Machine to Docker Container

To copy files from the host machine to a Docker container, you can use the following command:

```bash
docker cp /path/to/file/on/host <container_id>:/path/to/file/on/container
# example
docker cp /tmp/package.json 1234567890:/app/package.json
```

## References

- [Docker Documentation](https://docs.docker.com/engine/reference/commandline/cp/)
