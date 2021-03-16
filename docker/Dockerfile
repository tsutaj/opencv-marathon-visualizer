#Dockerfile
FROM ubuntu:16.04
ARG OPENCV_VERSION=3.4.13

RUN apt-get update && apt-get install -y --no-install-recommends \
    wget git cmake nano g++ libeigen3-dev libgtk-3-dev qt5-default freeglut3-dev libvtk6-qt-dev libtbb-dev\
    libjpeg-dev libjasper-dev libpng++-dev libtiff-dev libopenexr-dev libwebp-dev \
    libhdf5-dev libopenblas-dev liblapacke-dev \
    && rm -rf /var/lib/apt/lists/*

RUN wget https://github.com/opencv/opencv/archive/${OPENCV_VERSION}.tar.gz --no-check-certificate \
    && tar xfvz ${OPENCV_VERSION}.tar.gz
RUN cd opencv-${OPENCV_VERSION} && mkdir build && cd build \
    && pwd && cmake -D CMAKE_BUILD_TYPE=Release \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D WITH_TBB=ON .. \
    && make -j4 && make install
RUN echo /usr/local/lib > etc/ld.so.conf.d/opencv.conf && ldconfig -v
RUN opencv_version

