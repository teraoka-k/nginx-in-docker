# How to Set up Nginx in Docker

serve static resources effectively in nginx

## Download

download nginx image built on alpine

`docker pull nginx:alpine`

> alpine is one of linux distro which is known as the smallest linux distro

## Run

`docker run --name test -v absolute-path-to-the-local-git-repository\data:/data:ro -v absolute-path-to-the-local-git-repository\nginx.conf:/etc/nginx/nginx.conf:ro -d -p 8080:80 nginx:alpine`

- `docker run nginx:alpine` run nginx.
- `--name test` name the created docker container as `test`.
- `-v absolute-path-to-the-local-git-repository\data:/data:ro` override docker container's `/data` dir with local data dir.
- `ro` means `read only`, which disables changing that dir from inside the container.
- `-v absolute-path-to-the-local-git-repository\nginx.conf:/etc/nginx/nginx.conf:ro` override container's `/etc.../nginx.conf` with local conf file.
- `ro` means `read only`, which disalbes changing the conf file from inside the container.
- `-d` launch the container in detached mode.
- `-p 8080:80` expose alpine's port 80 to local port 8080.

## Served Resources

access files via browser by requesting

- `localhost:8080/index.html`
- `localhost:8080/test.html`
- `localhost:8080/test/index.html`
- `localhost:8080/js/test.js`

## Control

- reload nginx.conf by name of container

  `docker kill -s HUP test`

- restart container by name of container

  `docker restart test`

- kill container by name of container

  `docker rm -f test`

- look inside running container by name

  `docker exec -it test /bin/ash`

  > `ash` is not a typo, this is alpine version of `bash`

## Reference

- [Tips](https://www.docker.com/blog/tips-for-deploying-nginx-official-image-with-docker/6)
- [Nginx Beginner's Guide](http://nginx.org/en/docs/beginners_guide.html#static)
- [Nginx Caching (advanced)](https://serversforhackers.com/c/nginx-caching)
- [Collaborate with Node.js app 1](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-16-04)
- [Collaborate with Node.js app 2](https://www.tecmint.com/nginx-as-reverse-proxy-for-nodejs-app/)
