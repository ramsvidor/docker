# credits to hseeberger/sbt-scala
FROM ramsvidor/graalvm

ARG SCALA_VERSION="2.13.3"
ARG SBT_VERSION="1.3.13"
ARG APPUSER="marvin"
ARG VCS_REF
ARG VCS_URL
ARG BUILD_DATE

LABEL maintainer="Ramses Vidor <ramsvidor@gmail.com>" \
      org.label-schema.schema-version="1.0" \
      org.label-schema.vcs-ref="${VCS_REF}" \
      org.label-schema.vcs-url="${VCS_URL}" \
      org.label-schema.build-date="${BUILD_DATE}" \
      com.ramsesvidor.license="Apache-2.0"

ENV INSTALL_DIR="/usr/lib/scala"
ENV SCALA_HOME="${INSTALL_DIR}/scala-${SCALA_VERSION}"
ENV PATH="${SCALA_HOME}/bin:${PATH}"

RUN apt-get update -qq; \
    apt-get autoremove -qq --purge; \
    apt-get install -qq --no-install-recommends fakeroot; \
    mkdir -m 755 -p "${INSTALL_DIR}"; \
    wget -qO- "https://downloads.typesafe.com/scala/${SCALA_VERSION}/scala-${SCALA_VERSION}.tgz" \
             | tar xfz - -C "${INSTALL_DIR}" && \
             rm -f "${SCALA_HOME}/bin/*.bat"; \
    wget -q "https://dl.bintray.com/sbt/debian/sbt-${SBT_VERSION}.deb" && \
             dpkg -i "sbt-${SBT_VERSION}.deb" && \
             rm -f "sbt-${SBT_VERSION}.deb"; \
    adduser --quiet --system --group --home "/var/lib/${APPUSER}" --shell /bin/bash "${APPUSER}" && \
             install -d -m 0755 -o "${APPUSER}" -g "${APPUSER}" "/var/log/${APPUSER}"; \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/*

USER "${APPUSER}"
WORKDIR "/var/lib/${APPUSER}"

RUN sbt sbtVersion; \
    mkdir project; \
    echo "scalaVersion := \"${SCALA_VERSION}\"" | tee build.sbt; \
    echo "sbt.version=${SBT_VERSION}" | tee project/build.properties; \
    echo "case object Temp" | tee Temp.scala; \
    sbt compile; \
    rm -rf *
