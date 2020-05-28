FROM debian:stretch-slim

ARG BITCOIND_VERSION=0.19.1
ARG VCS_REF
ARG VCS_URL
ARG BUILD_DATE

LABEL maintainer="Ramses Vidor <ramsvidor@gmail.com>" \
      org.label-schema.schema-version="1.0" \
      org.label-schema.vcs-ref="${VCS_REF}" \
      org.label-schema.vcs-url="${VCS_URL}" \
      org.label-schema.build-date="${BUILD_DATE}" \
      com.ramsesvidor.license="Apache-2.0"

RUN apt-get update; \
    # curl and wget might be usefull for using in combination with blocknotify and walletnotify callbacks
    # ca-certificates is required for calling HTTPS endpoints
    apt-get install -y --no-install-recommends wget curl ca-certificates; \
    adduser --system --group --home /var/lib/bitcoind --shell /bin/bash bitcoind; cd /usr/src; \
    wget -O- "https://bitcoin.org/bin/bitcoin-core-${BITCOIND_VERSION}/bitcoin-${BITCOIND_VERSION}-x86_64-linux-gnu.tar.gz" \
        | tar xzf -; \
    install -v -m 0750 -o bitcoind -g bitcoind -t /usr/local/bin \
        bitcoin-${BITCOIND_VERSION}/bin/bitcoin-cli \
        bitcoin-${BITCOIND_VERSION}/bin/bitcoind; \
    install -v -m 0750 -o bitcoind -g bitcoind -d /etc/bitcoind /run/bitcoind; \
    apt-get autoremove --purge; apt-get clean; \
    rm -rf /usr/src/* /var/lib/apt/lists/* /var/cache/apt/* /tmp/*

USER bitcoind:bitcoind
WORKDIR /var/lib/bitcoind
COPY bitcoin.conf /etc/bitcoind

EXPOSE 8332 8333 18332 18333

CMD ["/usr/local/bin/bitcoind", "-printtoconsole", \
                                "-pid=/run/bitcoind/bitcoind.pid", \
                                "-conf=/etc/bitcoind/bitcoin.conf", \
                                "-datadir=/var/lib/bitcoind" ]