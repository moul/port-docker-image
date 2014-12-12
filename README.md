port-docker-image
=================

This script was used to convert a lot of x86_64 images for armhf
See: https://registry.hub.docker.com/repos/armbuild/

Usage
-----

**You need to run this script from an armhf host with Docker**

    $ ./port_docker_image -vi docker/fig
    [...]
    curl -sL https://github.com/docker/fig/archive/master.tar.gz
    [...]
    + cat Dockerfile
    FROM armbuild/debian:wheezy
    [...]
    + docker build -t docker/fig .
    [...]

Under the hood
--------------

The script will :

- clone the matching Github repository
- switch the `FROM image` to `FROM armbuild/image` (to use the armhf port of an image).
- replace the `x86_64`, `i386` strings in the Dockerfile with `armhf` (ie: for hardcoded .deb)
- try to build the container
