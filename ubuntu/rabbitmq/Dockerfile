FROM ubuntu:12.04
MAINTAINER Matt Bentley <mbentley@mbentley.net>

RUN echo "deb http://us.archive.ubuntu.com/ubuntu precise main universe multiverse" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get -y upgrade

RUN DEBIAN_FRONTEND=noninteractive apt-get -y install wget supervisor
RUN wget --quiet --no-check-certificate -O - http://www.rabbitmq.com/rabbitmq-signing-key-public.asc | apt-key add -
RUN echo "deb http://www.rabbitmq.com/debian/ testing main" > /etc/apt/sources.list.d/rabbitmq.list
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install rabbitmq-server

RUN echo "ulimit -n 1024" >> /etc/default/rabbitmq-server

ADD rabbitmq.conf /etc/supervisor/conf.d/rabbitmq.conf
ADD run.sh /usr/local/bin/run

VOLUME ["/var/lib/rabbitmq"]
EXPOSE 5672
EXPOSE 15672
CMD ["/usr/local/bin/run"]
