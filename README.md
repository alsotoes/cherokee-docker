# cherokee-docker
Images to build cherokee webserver
```
$ podman run --rm -detach --publish 80:80 --volume /tmp/www:/var/www --name cherokee localhost/cherokee:latest
```
# creating a podman pod
```
$ podman play kube mirrors.yaml  
Pod:  
081b8871994ac79bb4035cf97d963f1bce6cabad46eb18e7ee9d2b6c3c222d57  
Container:  
9c211f9e1272cdda9b040238852c8f002e8eed1976e11d53d58648ae0db1f547  
```
  
```
$ podman pod list  
POD ID        NAME        STATUS      CREATED         INFRA ID      # OF CONTAINERS  
081b8871994a  mirror      Running     26 seconds ago  906d926a4ea2  2  
$  
$ podman ps -a  
CONTAINER ID  IMAGE                      COMMAND               CREATED         STATUS             PORTS                 NAMES  
906d926a4ea2  k8s.gcr.io/pause:3.5                             33 seconds ago  Up 33 seconds ago  0.0.0.0:8080->80/tcp  081b8871994a-infra  
9c211f9e1272  localhost/cherokee:latest  /usr/sbin/cheroke...  33 seconds ago  Up 33 seconds ago  0.0.0.0:8080->80/tcp  mirror-cherokee  
```
