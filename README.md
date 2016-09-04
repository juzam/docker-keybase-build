# docker-keybase-build
Dockerfiles to build keybase.io clent

- Dockerfile-arm

Docker file to build keybase client on ARM, tested on Raspberry PI 3. 

clone repository,  then:

```
docker build -t keybase-build -f Docker-arm .
```

after the build is finished you can copy keybase binary with

```
docker run -it test -v $PWD:/tmp /bin/bash 
```

and then inside the container cp keybase /tmp
