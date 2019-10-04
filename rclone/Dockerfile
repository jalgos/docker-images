FROM alpine

ARG RCLONE_VERSION="1.48.0"

ENV RCLONE_TYPE="amd64"
ENV BUILD_DEPS \
    wget \
    linux-headers \
    unzip \
    fuse
RUN set -x \
    && apk update \
    && apk add --no-cache --virtual .persistent-deps \
    bash \
    curl \
    monit \
    ca-certificates \
    && apk add --no-cache --virtual .build-deps \
    $BUILD_DEPS \
    && mkdir -p /tmp \
    && cd /tmp  \
    && wget -q http://downloads.rclone.org/v${RCLONE_VERSION}/rclone-v${RCLONE_VERSION}-linux-${RCLONE_TYPE}.zip\
    && unzip /tmp/rclone-v${RCLONE_VERSION}-linux-${RCLONE_TYPE}.zip \
    && mv /tmp/rclone-v${RCLONE_VERSION}-linux-${RCLONE_TYPE}/rclone /usr/bin \
    && mkdir -p /config /defaults /data \
    && rm -Rf /tmp/* \
    && rm -rf /var/cache/apk/* \
    && apk del .build-deps

CMD ["rclone"]
