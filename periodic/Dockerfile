FROM ubuntu:14.04
MAINTAINER Li Meng Jun "lmjubuntu@gmail.com"

# Set the env variable DEBIAN_FRONTEND to noninteractive
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y && \
    apt-get install --no-install-recommends -y -q curl build-essential \
        ca-certificates git mercurial bzr

RUN mkdir /goroot && \
    curl https://storage.googleapis.com/golang/go1.3.3.linux-amd64.tar.gz | tar xvzf - -C /goroot --strip-components=1

RUN mkdir /gopath

ENV GOROOT /goroot
ENV GOPATH /gopath
ENV PATH $PATH:$GOROOT/bin:$GOPATH/bin

RUN go get -v github.com/Lupino/periodic/cmd/periodic

ENV PERIODIC_PORT tcp://:5000

EXPOSE 5000

CMD periodic -d
