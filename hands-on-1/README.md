# Hands on demo 1

1. CD to this directory `cd hands-on-1`

2. Build the image `docker build -t hello-docker .`

3. Run the image `docker run hello-docker`

## Use some of the docker commands shown to inspect what happened

1. `docker ps` shows nothing, why?

2. run `docker ps -a` instead

3. `docker logs hello-docker` gives an error, why?

4. use `docker logs <container-id>` or `docker logs <name>` instead
