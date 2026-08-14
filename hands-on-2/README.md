# Hands on demo 2

For this demo we pull the public alpine image directly — it doesn't require a custom Dockerfile, since no docker build step is used.

1. Create a new volume `cd hands-on-2` and `docker volume create app-data`

2. Write the content "hi" to a file in the volume `docker run -v app-data:/data alpine sh -c "echo hi > /data/f.txt"`

3. Print out the content of the file `docker run -v app-data:/data alpine cat /data/f.txt`

4. Run `docker volume ls`

## Additional commands to try

1. Look at the content of a folder:
`docker run -v app-data:/data alpine ls -la /data`

2. Run `docker ps -a`. Why so many containers?

3. Mount a local folder as a volume, then copy the content of the file in the data volume to the local folder
`docker run --rm -v app-data:/data -v ./my-local-machine-folder/:/backup alpine cp /data/f.txt /backup/f.txt`

4. Why the `--rm` command? Run `run docker ps -a` again to see what changed

5. Cleanup `docker container rm <container-id>` and `docker volume rm app-data`

## Using docker cp

Alternative using docker cp (no bind mount needed, works off any container that has the volume attached):

```bash
docker create --name temp -v app-data:/data alpine
docker cp temp:/data/f.txt ./f.txt
docker rm temp
```

docker cp is useful when you need to pull logs off a running container, but it needs an extra create/remove step since the volume isn't attached to any existing container yet.
