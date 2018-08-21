FROM raspbian/jessie
LABEL maintainer="tyler@tbowdev.com"

RUN apt-get update -y && \
    apt-get install -y curl gcc g++ git libncurses5-dev libpcap-dev make && \
    apt-get clean all

# build latest cmake
ARG cmake_sources="https://cmake.org/files/v3.6/cmake-3.6.0.tar.gz"
LABEL cmake-version=3.6.0

RUN cd /opt \
 && mkdir src \
 && curl -s $cmake_sources | tar -xz --strip-components=1 -C src \
 && cd src \
 && ./bootstrap \
 && make -j8 \
 && make install \
 && cd .. \
 && rm -rf src

RUN alias ll='ls -lh'
