# htop in a container
#
# docker run --rm -it \
# 	--pid host \
# 	westonsteimel/htop
#
FROM alpine:edge

RUN apk upgrade && apk --no-cache add \
	htop \
    && rm -rf /var/cache \
    && addgroup htop \
    && adduser -G htop -s /bin/sh -D htop

USER htop

CMD [ "htop" ]
