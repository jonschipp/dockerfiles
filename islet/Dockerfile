# ISLET - Runs ISLET in a container
#
# VERSION               0.1
FROM      ubuntu
MAINTAINER Jon Schipp <jonschipp@gmail.com>

RUN apt-get update -qq
RUN apt-get install -yq git sqlite3 pv make openssh-server supervisor
RUN apt-get install -yq git gawk vim emacs nano tcpdump rsyslog
RUN apt-get install -yq --no-install-recommends man-db
RUN mkdir -p /var/run/sshd
ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf
ADD sshd_config /etc/ssh/sshd_config
RUN cd /root && git clone http://github.com/jonschipp/ISLET
RUN cd /root/ISLET && make install && make user-config
CMD ["/usr/bin/supervisord","-c","/etc/supervisor/supervisord.conf"]
