FROM ubuntu:12.04
MAINTAINER Matt Bentley <mbentley@mbentley.net>

RUN echo "deb http://us.archive.ubuntu.com/ubuntu precise main universe multiverse" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get -y upgrade

ENV LANGUAGE en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8
RUN DEBIAN_FRONTEND=noninteractive locale-gen en_US.UTF-8
RUN DEBIAN_FRONTEND=noninteractive dpkg-reconfigure locales
RUN update-locale LANG=en_US.UTF-8

RUN RUNLEVEL=1 DEBIAN_FRONTEND=noninteractive apt-get -y install python-software-properties software-properties-common wget supervisor
RUN wget --quiet --no-check-certificate -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main" > /etc/apt/sources.list.d/pgdg.list
RUN apt-get update
RUN RUNLEVEL=1 DEBIAN_FRONTEND=noninteractive apt-get -y install postgresql-9.3 postgresql-client-9.3 postgresql-contrib-9.3

ADD postgres.conf /etc/supervisor/conf.d/postgres.conf
ADD run.sh /usr/local/bin/run

VOLUME ["/var/lib/postgresql/9.3/main", "/var/log/postgresql"]
EXPOSE 5432
CMD ["/usr/local/bin/run"]
