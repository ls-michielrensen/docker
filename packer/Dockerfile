FROM alpine:latest

ENV PACKER_VERSION 0.8.6

RUN apk add --no-cache --update wget ca-certificates unzip gzip && \
    wget -q -O /packer.zip "https://releases.hashicorp.com/packer/${PACKER_VERSION}/packer_${PACKER_VERSION}_linux_amd64.zip" && \
    unzip /packer.zip -d /bin && \
    apk del --purge wget ca-certificates unzip gzip && \
    rm -rf /var/cache/apk/* /packer.zip && \
    mkdir /data

## Expose some volumes
VOLUME ["/data"]

WORKDIR /data

ENTRYPOINT ["/bin/packer"]
CMD ["--help"]
