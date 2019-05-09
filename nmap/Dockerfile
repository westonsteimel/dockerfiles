FROM alpine:edge

RUN apk upgrade && apk add --no-cache \
	nmap \
    nmap-scripts \
    && rm -rf /var/cache \
    && addgroup nmap \
	&& adduser -G nmap -s /bin/sh -D nmap

ENTRYPOINT ["nmap"]

