# Docker image ak-ehn-checker

An experimental project to build a Docker container image with pre-installed Akamai tool EHN CNAME Checker developped. 

Base Linux distribution: [Alpine 3.9|https://alpinelinux.org/posts/Alpine-3.9.3-released.html]

Main packages included:
* Python v3.6.8
* wget v1.20.3
* Akamai edgegrid-python

## Build instructions

First you need to retrieve the source code from Miko's Git:

```
$ git clone https://github.com/mikolajswider/akamai_script_edge_hostname_cname_checker.git
```

Then you build the image: 

```
$ docker build . -t ak-ehn-checker
```

## Usage 

Create a permanent Docker volume to store your credentials:
```
$ docker volume create ak-ehn-checker-volume
```

Run the container:

```
docker run --mount source=ak-ehn-checker-volume,target=/root/data -it ak-ehn-checker
```

NB: the file /root/.edgerc is a symbolic link to /root/data/.edgerc on the persistent volume.

