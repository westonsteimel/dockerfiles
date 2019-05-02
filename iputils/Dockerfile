FROM alpine:edge

RUN apk add --no-cache \
    iputils \
    ca-certificates \
    && rm -rf /var/cache \
    && addgroup iputils \
    && adduser -G iputils -s /bin/sh -D iputils

USER iputils
