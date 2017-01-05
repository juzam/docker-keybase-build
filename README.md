# docker-keybase-build
Dockerfiles to build keybase.io clent

Inspired by [keybase client issue #2938](https://github.com/keybase/client/issues/2938)

- Dockerfile: Docker file to build keybase client for linux/x86
- Dockerfil.arm: Docker file to build keybase client for linux/ARM (native) tested on Raspberry PI 3. 
- Dockerfile.xcompile-arm: Dockerfile to build keybase cliente for linux/Arm (crosscompile from x86)

# Usage with docker-compose

A `docker-compose.yml` file is provided, so after cloning the repository you can: 
`docker-compose up <servicename>`  and the keybase binary will get copied to
the repository directory after a successful build.


Services:
 - keybase-native-x86 (to be used on a x86 Docker host, compiles an x86 binary)
 - keybase-xcompile-arm (to be used on a x86 Docker host, cross compiles an ARM
   binary)
 - keybase-native-arm (to be used on an ARM Docker host, compiles an ARM binary
   see later for specific build notes)


# Special notes for native ARM build

In order to build you need `docker-compose` and a golang docker image wit golang
version >= 1.7.x

Instructions to install an ARM compatible `docker-compose` are provided [here]
(https://github.com/hypriot/arm-compose) courtesy of Hypriot.

In order to build the golang docker image that is required you have to init the 
relevant submodule first: `git submodule update --init --recursive`

after that simply do: `doker-compose up keybase-native-arm` 

(the golang image is marked as a requirement in the compose file, so it will get
built the first time if it's not present)

# Cleanup and rebuild

The included `cleanup.sh` removes old containers, and keybase-build image in
order to start from scratch. (note that it doesn't remove the golang image so
you don't have to rebuild that every time)



# OLD Usage (docker-compose is preferred):

```
docker build -t keybase-build -f Dockerfilename .
```

after the build is finished you can copy keybase binary with

```
docker run -it -v $(pwd):/tmp keybase-build /bin/bash 
```

and then inside the container ``cp keybase /tmp``
