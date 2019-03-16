FROM alpine:edge

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
    eigen-dev \
    qt5-qtbase-dev \
    qt5-qttools-dev \
    qt5-qtlocation \
    lua5.3-dev \
    lua-dev \
    ca-certificates \
    ttf-dejavu \
    && git clone --branch fix-qt-errors --depth 1 --recurse-submodules https://github.com/westonsteimel/celestia \
    && cd celestia \
	&& cmake . -DENABLE_GTK=OFF -DENABLE_QT=ON \
	&& make \
    && make install \
    && cd .. \
    && rm -rf celestia \
    && apk del .build-dependencies \
    && rm -rf /var/cache/*

ENTRYPOINT ["celestia-qt"]
