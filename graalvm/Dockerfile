ARG DEBIAN_IMAGE_VERSION="stretch-slim"
FROM debian:${DEBIAN_IMAGE_VERSION}

ARG JDK_VERSION="11"
ARG GRAALVM_VERSION="20.1.0"
ARG VCS_REF
ARG VCS_URL
ARG BUILD_DATE

LABEL maintainer="Ramses Vidor <ramsvidor@gmail.com>" \
      org.label-schema.schema-version="1.0" \
      org.label-schema.vcs-ref="${VCS_REF}" \
      org.label-schema.vcs-url="${VCS_URL}" \
      org.label-schema.build-date="${BUILD_DATE}"

ENV LANG="C.UTF-8" \
    INSTALL_DIR="/usr/lib/java" \
    DOWNLOAD_URL="https://github.com/graalvm/graalvm-ce-builds/releases/download"
ENV JAVA_HOME="${INSTALL_DIR}/graalvm-ce-java${JDK_VERSION}-${GRAALVM_VERSION}"
ENV PATH="${JAVA_HOME}/bin:${PATH}"

RUN apt-get update -qq; \
    apt-get autoremove -qq --purge; \
    apt-get install -qq --no-install-recommends wget ca-certificates p11-kit; \
    mkdir -m 755 -p "${INSTALL_DIR}"; \
    wget -qO- "${DOWNLOAD_URL}/vm-${GRAALVM_VERSION}/graalvm-ce-java${JDK_VERSION}-linux-amd64-${GRAALVM_VERSION}.tar.gz" \
            | tar xfz - -C "${INSTALL_DIR}"; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/*

CMD "/bin/bash"
