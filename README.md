# gluster
glusterfs container

This container is based on the following container.
gluster/gluster-containers

By default the Docker build file will pull the latest version 8 gluster release and build a centos 8 based container.

docker example:
docker run -v /etc/glusterfs:/etc/glusterfs:z -v /var/lib/glusterd:/var/lib/glusterd:z -v /var/log/glusterfs:/var/log/glusterfs:z -v /sys/fs/cgroup:/sys/fs/cgroup:ro -d --privileged=true --net=host -v /dev/:/dev gluster/gluster-centos

docker-compose example:
version: '3.8'
services:
  gluster:
    container_name: "gluster"
    image: glusterfs8:latest
    privileged: true
    volumes:
      - /etc/glusterfs:/etc/glusterfs:z
      - /var/lib/glusterd:/var/lib/glusterd:z
      - /var/log/glusterfs:/var/log/glusterfs:z
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
      - /dev/:/dev
    network_mode: "host"
