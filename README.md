# docker-keybase-build
Dockerfiles to build keybase.io clent

Inspired by [keybase client issue #2938](https://github.com/keybase/client/issues/2938)

- Dockerfile: Docker file to build keybase client for linux/x86
- Dockerfil.arm: Docker file to build keybase client for linux/ARM (native) tested on Raspberry PI 3. 
- Dockerfile.xcompile-arm: Dockerfile to build keybase cliente for linux/Arm (crosscompile from x86)

# Usage

clone repository,  then:

```
docker build -t keybase-build -f Dockerfilename .
```

after the build is finished you can copy keybase binary with

```
docker run -it -v $(pwd):/tmp keybase-build /bin/bash 
```

and then inside the container ``cp keybase /tmp``
