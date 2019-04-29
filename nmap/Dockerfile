FROM alpine:edge

RUN apk upgrade && apk add --no-cache \
	nmap \
    nmap-scripts \
    && rm -rf /var/cache \
    && addgroup -g 1000 nmap \
	&& adduser -u 1000 -G nmap -s /bin/sh -D nmap

ENTRYPOINT ["nmap"]

