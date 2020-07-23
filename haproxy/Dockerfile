FROM ubuntu:latest

# proxy stuff
RUN echo 'Acquire::http::Proxy "http://proxy.housenet.yaleman.org:3128";' > /etc/apt/apt.conf.d/95proxy

#timezone stuff
ARG DEBIAN_FRONTEND=noninteractive
RUN ln -fs /usr/share/zoneinfo/UTC /etc/localtime

# update things
RUN apt-get update

# get to the point
RUN apt-get install -y haproxy
COPY haproxy.cfg /etc/

CMD /usr/sbin/haproxy -f /etc/haproxy.cfg