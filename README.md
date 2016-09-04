# docker-keybase-build
Dockerfiles to build keybase.io clent

Inspired by [keybase client issue #2938](https://github.com/keybase/client/issues/2938)

- Dockerfile-arm: Docker file to build keybase client on ARM, tested on Raspberry PI 3. 

# Usage

clone repository,  then:

```
docker build -t keybase-build -f Dockerfilename .
```

after the build is finished you can copy keybase binary with

```
docker run -it test -v $PWD:/tmp /bin/bash 
```

and then inside the container ``cp keybase /tmp``
