FROM ubuntu:14.04

MAINTAINER jas-

RUN apt-get update && apt-get -y upgrade
RUN apt-get install -y git npm


ADD ./dowork /
ENTRYPOINT ./dowork
