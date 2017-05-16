FROM ubuntu:16.04

RUN apt-get clean -y

RUN apt-get update && \
apt-get install -y dnsmasq

EXPOSE 53 53/udp
ENTRYPOINT ["dnsmasq", "-k"]
