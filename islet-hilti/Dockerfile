# HILTI
#
# VERSION               1.0

FROM rsmmr/clang:3.5
MAINTAINER Jon Schipp <jonschipp@gmail.com>

# Specify container username e.g. training, demo
ENV VIRTUSER demo


RUN apt-get update -q
RUN apt-get install -qy bison flex libpapi-dev libgoogle-perftools-dev gdb
RUN apt-get install -qy ylibpcap-dev libssl-dev python-dev swig zlib1g-dev
RUN apt-get install -qy git vim emacs nano tcpdump gawk
RUN apt-get install -qy --no-install-recommends man-db
RUN adduser --disabled-password --gecos "" $VIRTUSER
ENV PATH $PATH:/usr/local/bro/bin:/opt/bro/aux/btest
ENV PATH $PATH:/opt/hilti/tools:/opt/hilti/build/tools::/opt/hilti/build/tools/pac-driver
RUN echo "export TMOUT=1800; readonly TMOUT" > /etc/profile.d/timeout.sh && chmod 555 /etc/profile.d/timeout.sh
WORKDIR /home/demo
RUN sh -c '/bin/echo -e "module Test;\nprint \"Hello, world!\"" > hello-world.pac2' $VIRTUSER
CMD hilti-config --version; bash
RUN cd /opt && git clone --recursive git://git.bro.org/bro
