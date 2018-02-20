# Adsmurai's Dockerized SBT

You can find the published images in
[our own docker repository](https://hub.docker.com/r/adsmurai/sbt/).

This version of dockerized sbt is inspired by the
[official gradle's docker repository](https://hub.docker.com/_/gradle/), but it
has some extra nice features, like UIDs and GIDs mapping.

## Usage instructions

You can execute the dockerized SBT with:

```bash
docker run                                                  \
       --rm                                                 \
       -it                                                  \
       -v "${HOME}:/user"                                   \
       -v /home/user/sourcedir/:/app                        \
       -u "$(id -u):$(id -g)"                               \
       adsmurai/sbt:1.1-jdk8                                \
       sbt
```
