FROM ubuntu:latest
MAINTAINER Will Price <will.price94+dev@gmail.com>


ARG OPENCV_VERSION="3.1.0"

# Docker file deps
RUN apt-get update && \
    apt-get install -y wget sudo unzip

# OpenCV dependencies
RUN apt-get update && \
    apt-get install -y libopencv-dev \
                       build-essential \
                       checkinstall \
                       cmake \
                       pkg-config \
                       yasm \
                       libjpeg-dev \
                       libjasper-dev \
                       libavcodec-dev \
                       libavformat-dev \
                       libswscale-dev \
                       libdc1394-22-dev \
                       libxine2-dev \
                       libgstreamer0.10-dev \
                       libgstreamer-plugins-base0.10-dev \
                       libv4l-dev \
                       python-dev \
                       python-numpy \
                       libtbb-dev \
                       libqt4-dev \
                       libgtk2.0-dev \
                       libmp3lame-dev \
                       libopencore-amrnb-dev \
                       libopencore-amrwb-dev \
                       libtheora-dev \
                       libvorbis-dev \
                       libxvidcore-dev \
                       x264 \
                       v4l-utils \
                       ffmpeg \
                       cmake \
                       qt5-default \
                       checkinstall

# Download OpenCV
WORKDIR "/tmp"
RUN wget -O OpenCV-$OPENCV_VERSION.zip \
         "http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/$OPENCV_VERSION/opencv-$OPENCV_VERSION.zip/download"
RUN unzip OpenCV-$OPENCV_VERSION.zip && \
    mv opencv-$OPENCV_VERSION opencv

# Build OpenCV
WORKDIR "/tmp/opencv"
RUN mkdir build && \
    cd build && \
    cmake -D CMAKE_BUILD_TYPE=RELEASE \
          -D CMAKE_INSTALL_PREFIX=/usr/local \
          -D WITH_TBB=ON \
          -D BUILD_NEW_PYTHON_SUPPORT=ON \
          -D WITH_V4L=ON \
          -D INSTALL_C_EXAMPLES=ON \
          -D INSTALL_PYTHON_EXAMPLES=ON \
          -D BUILD_EXAMPLES=ON -D WITH_QT=ON -D WITH_OPENGL=ON \
          .. && \
    make -j5 && \
    checkinstall

# Dev tools
RUN apt-get update && \
    apt-get install -y vim-gtk3 && \
    rm -rf /var/cache/apt

RUN mkdir /src
WORKDIR /src
VOLUME /src
CMD ["bash"]

