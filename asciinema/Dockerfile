FROM python:3-alpine

ENV ASCIINEMA_VERSION 2.0.2

RUN apk update && apk add --no-cache \
    ca-certificates \
    ncurses \
    && addgroup -g 1000 asciinema \
    && adduser -u 1000 -G asciinema -s /bin/sh -D asciinema

USER asciinema
ENV PATH "/home/asciinema/.local/bin:$PATH"
RUN pip install --user --no-cache-dir asciinema==${ASCIINEMA_VERSION}

ENTRYPOINT ["asciinema"]
