FROM westonsteimel/alpine-glibc:edge

RUN apk upgrade && apk --no-cache add --virtual .build-dependencies \
    cmake \
    make \
    g++ \
    git \
    && apk --no-cache add \
    glew-dev \
    jpeg-dev \
    libpng-dev \
    libtheora-dev \
    mesa-gl \
    mesa-dri-intel \
    gtk+2.0-dev \
    gtkglext-dev \
    lua5.3-dev \
    lua-dev \
    ca-certificates \
    ttf-dejavu \
    && git clone --depth 1 --recurse-submodules https://github.com/CelestiaProject/celestia \
    && cd celestia \
	&& cmake . -DENABLE_GTK=ON -DENABLE_QT=OFF \
	&& make \
    && make install \
    && cd .. \
    && rm -rf celestia \
    && apk del .build-dependencies \
    && rm -rf /var/cache/*

ENTRYPOINT ["celestia-gtk"]
