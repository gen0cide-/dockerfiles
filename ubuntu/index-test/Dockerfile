FROM ubuntu:12.04
MAINTAINER Matt Bentley <mbentley@mbentley.net>

RUN echo "deb http://us.archive.ubuntu.com/ubuntu precise main universe multiverse" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get -y upgrade

RUN RUNLEVEL=1 DEBIAN_FRONTEND=noninteractive apt-get install -y curl
RUN curl https://get.docker.io/builds/Linux/x86_64/docker-latest -o /usr/local/bin/docker
RUN chmod +x /usr/local/bin/docker
ADD run.sh /usr/local/bin/run
ENTRYPOINT ["/usr/local/bin/run"]
