FROM ubuntu:14.04
MAINTAINER Amit Aharoni <amit.sites@gmail.com>

# Upgrade system
RUN \
  apt-get update && \
  apt-get dist-upgrade -y --no-install-recommends && \
  apt-get autoremove -y && \
  apt-get clean

# Install packages
RUN \
  apt-get install -y --no-install-recommends curl supervisor privoxy openvpn && \
  apt-get autoremove -y && \
  apt-get clean

# Add custom supervisor config
ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Add custom config
ADD ./privoxy/config /etc/privoxy/config

# Add HMA
ADD ./hma/hma-runner.sh /usr/bin/hma-runner.sh
ADD ./hma/hma-vpn.sh /usr/bin/hma-vpn.sh

# Ports
EXPOSE 8118

ADD run /usr/local/bin/run

CMD ["/usr/local/bin/run"]
