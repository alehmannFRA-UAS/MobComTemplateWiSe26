# syntax=docker/dockerfile:1

# global build-time arguments for FROM statements
# (https://docs.docker.com/engine/reference/builder/#understand-how-arg-and-from-interact)

ARG UBUNTU_VERSION="jammy"

FROM ubuntu:${UBUNTU_VERSION} AS builder

LABEL organization="FgfTk@fb2.fra-uas.de"

# build-time arguments for builder
ARG UERANSIM_VERSION="v3.2.7"
ARG DEBIAN_FRONTEND="noninteractive"

# install dependencies
RUN apt-get update && apt-get install make gcc g++ libsctp-dev lksctp-tools iproute2 cmake git -y

# clone the specific UERANSIM version and install it
RUN if [ "$UERANSIM_VERSION" = "latest" ]; then \
        git clone https://github.com/aligungr/UERANSIM.git; \
    else \
        git clone --depth 1 --branch=${UERANSIM_VERSION} https://github.com/aligungr/UERANSIM.git; \
    fi    
RUN cd UERANSIM && make -j `nproc`