FROM openjdk:17-jdk-alpine

ARG SBT_VERSION=1.5.5

RUN set -x \
    # install sbt
    && apk --update add --no-cache --virtual .build-deps curl \
    && SBT_VER=${SBT_VERSION} \
    # piccolo is dead https://github.com/sbt/sbt/issues/5860
    && SBT_URL="https://github.com/sbt/sbt/releases/download/v${SBT_VER}/sbt-${SBT_VER}.zip" \
    && apk add shadow bash openssh rsync git \
    && curl -Ls ${SBT_URL} > /tmp/sbt-${SBT_VER}.zip \
    && mkdir /opt/sbt \
    && unzip /tmp/sbt-${SBT_VER}.zip -d /opt/sbt \
    && sed -i -r 's#run \"\$\@\"#unset JAVA_TOOL_OPTIONS\nrun \"\$\@\"#g' /opt/sbt/sbt/bin/sbt \
    && apk del --purge .build-deps \
    && rm -rf /tmp/sbt-${SBT_VER}.tgz /var/cache/apk/* \
    # create workdir
    && mkdir /work

WORKDIR /work

ENV PATH="/opt/sbt/sbt/bin:$PATH" \
    JAVA_OPTS="-XX:+UseContainerSupport -Dfile.encoding=UTF-8" \
    SBT_OPTS="-Xmx2048M -Xss2M"
