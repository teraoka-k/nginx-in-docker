# How to Set up Nginx in Docker

serve static resources effectively in nginx

## Download

download nginx image built on alpine

`docker pull nginx:alpine`

> alpine is one of linux distro which is known as the smallest linux distro

## Run

run nginx:alpine, name the process as test, mount local data dir to alpine's `/data` dir, mount local `nginx.conf` file to alpine's `/etc.../nginx.conf` , run the process in detached mode, expose alpine's port 80 to local port 8080

`docker run --name test -v D:\workspace\nginx\data:/data:ro -v D:\workspace\nginx\nginx.conf:/etc/nginx/nginx.conf:ro -d -p 8080:80 nginx:alpine`

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
