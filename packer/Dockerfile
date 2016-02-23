FROM ubuntu:14.04

ENV PACKER_VERSION 0.9.0

## echo "Acquire::http::Proxy \"http://10.80.0.15:3142/\";" >> /etc/apt/apt.conf.d/99apt-proxy && \
RUN export DEBIAN_FRONTEND=noninteractive && \
    echo "deb http://download.virtualbox.org/virtualbox/debian trusty contrib" >> /etc/apt/sources.list.d/oracle-virtualbox-trusty.list && \
    apt-get update && apt-get install -y wget && \
    wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add - && \
    apt-get update && \
    apt-get install -y bash curl zip unzip linux-headers-4.2.0-27-generic build-essential virtualbox-5.0 dkms && \
    apt-get install --reinstall virtualbox-5.0 && \
    wget -q -O /packer.zip "https://releases.hashicorp.com/packer/${PACKER_VERSION}/packer_${PACKER_VERSION}_linux_amd64.zip" && \
    unzip /packer.zip -d /bin && \
    rm -rf /var/cache/apt/* /packer.zip && \
    mkdir /data

## Expose some volumes
VOLUME ["/data"]

WORKDIR /data

ENTRYPOINT ["/bin/packer"]
CMD ["--help"]
