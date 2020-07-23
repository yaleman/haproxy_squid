FROM ubuntu:latest

# proxy stuff
RUN echo 'Acquire::http::Proxy "http://proxy.housenet.yaleman.org:3128";' > /etc/apt/apt.conf.d/95proxy

#timezone stuff
ARG DEBIAN_FRONTEND=noninteractive
RUN ln -fs /usr/share/zoneinfo/UTC /etc/localtime

ENV SQUID_CACHE_DIR=/var/spool/squid \
    SQUID_LOG_DIR=/var/log/squid \
    SQUID_USER=proxy
# update things
RUN apt-get update
# get to the point
RUN apt-get install -y squid3

COPY entrypoint.sh /usr/local/sbin/
RUN chmod +x /usr/local/sbin/entrypoint.sh

RUN echo "http_access allow localnet" >> /etc/squid/conf.d/allow.conf

CMD /usr/local/sbin/entrypoint.sh