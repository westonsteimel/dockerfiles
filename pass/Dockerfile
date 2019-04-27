FROM alpine:edge as builder

ENV PASS_VERSION 1.7.3

RUN apk update && apk add --no-cache \
	git \
    bash \
    make \
    tree \
    gnupg \
    pwgen \
    ca-certificates \
	&& cd /tmp \
	&& git clone --depth=1 --branch "${PASS_VERSION}" https://github.com/zx2c4/password-store.git \
	&& cd password-store \
	&& PREFIX=/usr/local make install \
	&& apk del curl make git \
	&& rm /var/cache/apk/* 

FROM alpine:edge

COPY --from=builder /usr/local/bin/pass /usr/local/bin/pass
COPY --from=builder /usr/local/share /usr/local/share
COPY --from=builder /usr/local/lib /usr/local/lib

RUN apk update && apk add --no-cache \
    bash \
    tree \
    gnupg \
    pwgen \
    ca-certificates \
    && rm /var/cache/apk/* \
    && addgroup -g 1000 pass \
    && adduser -u 1000 -G pass -s /bin/sh -D pass

USER pass
WORKDIR /home/pass
ENV GPG_TTY /dev/console

ENTRYPOINT ["/usr/local/bin/pass"]
