FROM ubuntu:18.04

ENV DEBIAN_FRONTEND noninteractive
USER root
RUN apt-get update && \
    apt-get -y install gcc mono-mcs gcc-mingw-w64 && \
    rm -rf /var/lib/apt/lists/*

RUN  useradd -ms /bin/bash open62541

RUN mkdir -p /var/open62541-linux64/client \
 && chown -R open62541:open62541 /var/open62541-linux64/client    

USER open62541
    
COPY . /var/open62541-linux64/client

WORKDIR /var/open62541-linux64/client

RUN gcc -std=c99 open62541.c myClient.c -o myClient

CMD ./myClient
