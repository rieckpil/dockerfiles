FROM ubuntu:16.04

LABEL maintainer = "mail@philipriecks.de"

RUN apt-get update && \
    apt-get install -y \
    python2.7 \
    openjdk-8-jdk \
    ant \
    git \
    cmake \
    wget unzip \
    gcc g++ &&\
    apt-get clean && \
    rm -rf /var/lib/apt/lists/

ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64/
RUN export JAVA_HOME

ENV OPEN_CV_VERSION 3.4.2

RUN wget https://github.com/opencv/opencv/archive/${OPEN_CV_VERSION}.zip && \
    unzip ${OPEN_CV_VERSION}.zip && \
    rm ${OPEN_CV_VERSION}.zip

RUN cd opencv-${OPEN_CV_VERSION} && \
    mkdir build && cd build && \
    cmake -D BUILD_SHARED_LIBS=off .. && \
    make -j8

ENV OPEN_CV_LIB /opencv-${OPEN_CV_VERSION}/build/lib
RUN export OPEN_CV_LIB 