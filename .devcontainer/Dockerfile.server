FROM ubuntu:latest

ENV DEBIAN_FRONTEND noninteractive
RUN echo 'root:root' | chpasswd
RUN printf '#!/bin/sh\nexit 0' > /usr/sbin/policy-rc.d
RUN apt update \
    && apt install --no-install-recommends -y rsyslog systemd systemd-cron dbus sudo wget curl nano software-properties-common  \
    # Fix a bug with common-debian script
    && rm -f /usr/local/bin/systemctl \
    #  Clean up
    && apt clean && rm -rf /var/lib/apt/lists/* 
RUN printf "systemctl start systemd-logind" >> /etc/profile

ENTRYPOINT ["/sbin/init"]
