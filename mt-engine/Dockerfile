FROM ubuntu:16.04
MAINTAINER Ulrich Germann <ugermann@inf.ed.ac.uk>
# This is a docker containing the infrastructure required for building
# or repackaging the components necessary to run the MT service.


# Intel MKL is so expensive to install that we install it as on one of the first
# Docker layers

COPY GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB .
# from: https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB

RUN apt-get update \
    && apt-get install -y apt-transport-https \
    && apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB \
    && echo deb https://apt.repos.intel.com/mkl all main >/etc/apt/sources.list.d/intel-mkl.list \
    && apt-get update && apt-get install -y  intel-mkl-64bit-2018.2-046

RUN apt-get install -y \
    autoconf \
    automake \
    cmake \
    g++ \
    git \
    libssl-dev \
    libtool \
    libboost-all-dev \
    libgoogle-perftools-dev \
    libpcre3-dev \
    python3-pip \
    unzip \
    wget 

ADD . .
RUN rm -rf /var/lib/apt/lists/*
