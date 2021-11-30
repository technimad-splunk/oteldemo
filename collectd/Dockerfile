FROM debian:stable-slim 

RUN apt-get update 
RUN apt-get --no-install-recommends install -y \
    collectd
ENTRYPOINT [ "/usr/sbin/collectd", "-f" ]

