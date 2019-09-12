# BIOS Virtualization

* Enable Virtualization in BIOS
* Use toolbox to install docker, it will create VirtualBox default machine (boot2docker.iso)

VirtualBox -> Settings -> Shared Folders

Add

* Folder Path: D:\20190904-Training_Oct
* Folder Name: d/20190904-Training_Oct
* Auto-mount
* Make Permanent

Docker CMD

* docker-machine ssh
* ls /d/20190904-Training_Oct

# Docker

* [Docker Osgeo GDAL](https://hub.docker.com/r/osgeo/gdal)
* [DockerImages](https://wiki.osgeo.org/wiki/DockerImages)
* [Docker Toolbox](https://docs.docker.com/toolbox/overview/)
* [Docker Community Edition](https://docs.docker.com/docker-for-windows/release-notes/)
* [Docker Volume Windows](https://stackoverflow.com/questions/33126271/how-to-use-volume-option-with-docker-toolbox-on-windows)

## cmd window 1

```
cd Docker
docker build -t qpan/jupyter .
```

### Windows 7, VirtualBox

```
cd D:\20190904-Training_Oct
docker run -it --name jupyter -p 8888:8888 -v /d/20190904-Training_Oct:/notebooks qpan/jupyter
```

### Windows 10, Hyper-V

```
cd D:\20190904-Training_Oct
docker run -it --name jupyter -p 8888:8888 -v D:/20190904-Training_Oct:/notebooks qpan/jupyter
```

### Mac, Linux

```
cd /Volumes/SSD/20190904-Training_Oct/
docker run -it --name jupyter -p 8888:8888 -v $(PWD):/notebooks qpan/jupyter
# docker run -d --name jupyter -p 8888:8888 -v $(PWD):/notebooks qpan/jupyter
```

## cmd window 2

```
docker exec -it jupyter bash

jupyter notebook list

cd /notebooks

gdalinfo --version
GDAL 3.1.0dev-650fc42f344a6a4c65f11eefc47c473e9b445a68, released 2019/08/25

python3 qpan_gdalwarp.py 
```

## cmd window others

```
docker cp /20190904-Training_Oct gdal:/
```

## Docker-machine

```
docker-machine ls

docker-machine env

docker-machine start default
docker-machine stop default
```

## Clean docker

```
docker system prune -f && docker volume prune -f && docker container prune -f
```

## Save docker images

```
docker save --output qpan_jupyter.tar qpan/jupyter
```

## Load docker images

```
docker load --input qpan_jupyter.tar
```
