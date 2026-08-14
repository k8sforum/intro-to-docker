# Hands on demo 3

1. `cd hands-on-3`

2. Build the "before" — bloated single-stage image
`docker build -f Dockerfile-single-stage -t hello-go:single .`

3. Build the "after" — slim multi-stage image
`docker build -f Dockerfile-multistage -t hello-go:multi .`

4. compare sizes side by side
`docker images | grep hello-go`

5. Look at the images. They have the same name but different tags.
Add a new tag to one of them
`docker tag hello-go:multi hello-go:latest`

6. Run the app to show it works.
Here we use `--rm` to cleanup after the containers exists.
We also make use of port forwarding

```bash
docker run --rm -p 8080:8080 hello-go:multi
curl localhost:8080
```
