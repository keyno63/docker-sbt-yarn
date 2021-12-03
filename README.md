# docker-sbt-yarn

This is for using sbt and yarn commands in docker image.
When if we develop Scala projects with JS (managed br yarn).

## Docker Hub
This Docker images is published to Docker Hub.
- [keyno63/sbt](https://hub.docker.com/r/keyno63/sbt)
- [keyno63/sbt-yarn](https://hub.docker.com/r/keyno63/sbt-yarn)

## Using Library Version

- sbt: 1.5 (1.5.5)
- jdk: 8, 11, or 17
  - jdk8, jdk11: adopt
  - jdk17: openjdk

## To Build Local

If you want to build and use this on local,  
you get this repository and build with docker (command). 

e.g. In the case of using image of sbt-yarn with jdk8:
```shell
# clone repository
git clone <this repository>
cd docker-sbt-yarn

# build docker image
docker build jdk8/alpine/sbt-yarn -t sbt-yarn:1.5-jdk8-alpine

# change directory/folder of your working scala projects.
# to run
docker run -it --rm -v ${PWD}:/work -w /work sbt-yarn:1.5-jdk8-alpine /bin/bash

# to run with sbt (batch mode).
docker run -it --rm -v ${PWD}:/work -w /work --entrypoint "sbt" sbt-yarn:1.5-jdk8-alpine
```

## LICENSE

This repository is licensed under [Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0) License.  
See [License](./LICENSE) file.
