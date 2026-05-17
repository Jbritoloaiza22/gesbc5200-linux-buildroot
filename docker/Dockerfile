# Base Ubuntu
FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

# Dependencias para kernel/buildroot
RUN apt-get update && apt-get install -y \
    build-essential \
    git \
    wget \
    curl \
    perl \
    python3 \
    autoconf \
    automake \
    libtool \
    pkg-config \
    gawk \
    bison \
    flex \
    texinfo \
    tar \
    unzip \
    cpio \
    rsync \
    bc \
    kmod \
    file \
    vim \
    nano \
    libncurses5-dev \
    libncursesw5-dev \
    ccache \
    && rm -rf /var/lib/apt/lists/*

# Workspace
WORKDIR /workspace/project

# Toolchain Buildroot
ENV TOOLCHAIN_DIR=/opt/toolchains

# Cross compile
ENV ARCH=arm
ENV CROSS_COMPILE=arm-buildroot-linux-gnueabihf-
ENV SYSROOT=${TOOLCHAIN_DIR}/buildroot/sysroot

# PATH
ENV PATH=${TOOLCHAIN_DIR}/buildroot/bin:${PATH}

# Bash por defecto
CMD ["/bin/bash"]