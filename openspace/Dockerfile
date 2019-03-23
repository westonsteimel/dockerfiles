# docker run \
#    --rm \
#    -v /etc/localtime:/etc/localtime:ro \
#    -v /etc/machine-id:/etc/machine-id:ro \
#    -v /tmp/.X11-unix:/tmp/.X11-unix \
#    -v ${HOME}/.stellarium:/home/stellarium/.stellarium \
#    -e "DISPLAY=unix${DISPLAY}" \
#    -e GDK_SCALE \
#    -e GDK_DPI_SCALE \
#    -v /dev/shm:/dev/shm \
#    --device /dev/snd \
#    --device /dev/dri \
#    --device /dev/video0 \
#    --group-add audio \
#    --group-add video \
#    --name stellarium \
#    "${DOCKER_REPO_PREFIX}/stellarium" "$@"

FROM alpine:edge AS builder

ENV MESA_GL_VERSION_OVERRIDE=4.5

RUN apk upgrade && apk --no-cache add --virtual .build-dependencies \
    cmake \
    make \
    g++ \
    git 

RUN apk --no-cache add \
    glew-dev \
    jpeg-dev \
    libpng-dev \
    libxrandr-dev \
    libxinerama-dev \
    libxcursor-dev \
    boost-dev \
    mesa-gl \
    mesa-dri-intel \
    ca-certificates \
    ttf-dejavu \
    qt5-qtbase-dev \
    qt5-qttools-dev \
    qt5-qtlocation-dev \
    qt5-qtserialport-dev \
    qt5-qtscript-dev \
    && apk --no-cache add --repository http://dl-cdn.alpinelinux.org/alpine/edge/testing/ \
    gdal-dev \
    freeimage-dev

RUN git clone --depth 1 --recurse-submodules https://github.com/OpenSpace/OpenSpace \
    && cd OpenSpace \
    && mkdir build \
    && cd build \
    && cmake .. -DCMAKE_BUILD_MODE=Release \
    && make -j2 \
    && make install \
    && cd .. \
    && rm -rf OpenSpace \
    && apk del .build-dependencies \
    && rm -rf /var/cache/*

#FROM alpine:edge

#COPY --from=builder /usr/local/share/stellarium /usr/local/share/stellarium
#COPY --from=builder /usr/local/bin/stellarium /usr/local/bin/stellarium

#RUN apk upgrade && apk --no-cache add \
#    mesa-gl \
#    mesa-dri-intel \
#    lua5.3 \
#    lua \
#    ca-certificates \
#    ttf-dejavu \
#    qt5-qtbase \
#    qt5-qttools \
#    qt5-qtlocation \
#    qt5-qtserialport \
#    qt5-qtscript

#RUN addgroup -g 1000 stellarium \
#    && adduser -u 1000 -G stellarium -s /bin/sh -D stellarium

#USER stellarium

#ENTRYPOINT ["stellarium"]
