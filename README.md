# cherokee-docker
Images to build cherokee webserver

$ podman run --rm -detach --publish 80:80 --volume /tmp/www:/var/www --name cherokee localhost/cherokee:latest
