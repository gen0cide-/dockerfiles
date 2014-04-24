FROM ubuntu:12.04
MAINTAINER Alex Levinson <gen0cide.threats@gmail.com>

RUN echo "deb http://us.archive.ubuntu.com/ubuntu precise main universe multiverse" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get install -y bind9 bind9utils supervisor

ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf
ADD named.conf.options /etc/bind/named.conf.options
ENTRYPOINT perl -pi -e 's/_X_/$ENV{"TEAM"}/g' /etc/bind/named.conf.options && rndc reload

EXPOSE 53
CMD ["/usr/bin/supervisord"]
