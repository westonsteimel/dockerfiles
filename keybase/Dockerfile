FROM golang:1.12-alpine AS builder

ENV KEYBASE_VERSION=v3.0.0

RUN apk upgrade && apk --no-cache add --virtual .build-dependencies \
    git \
    build-base \
    && mkdir -p "${GOPATH}/src/github.com/keybase" \
    && cd "${GOPATH}/src/github.com/keybase" \
    && git clone --branch "${KEYBASE_VERSION}" --depth 1 https://github.com/keybase/client \
    && cd client/go/keybase \
    && go get ./... \
    && go build -v -a -tags production -o "/usr/local/bin/keybase" \
    && cd / \
    && rm -rf ${GOPATH}/client \
    && apk del .build-dependencies \
    && rm -rf /var/cache/*

FROM alpine:edge

COPY --from=builder /usr/local/bin/keybase /usr/local/bin/keybase

RUN apk upgrade && apk --no-cache add \
    ca-certificates \
    && addgroup -g 1000 keybase \
    && adduser -u 1000 -G keybase -s /bin/sh -D keybase
    
USER keybase

ENTRYPOINT ["keybase"]
