FROM alpine:edge

RUN apk upgrade && apk --no-cache add \
	bind-tools \
    && addgroup bind-tools \
    && adduser -G bind-tools -s /bin/sh -D bind-tools

USER bind-tools

CMD ["/bin/sh"]
