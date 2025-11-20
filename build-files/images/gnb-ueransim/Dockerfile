# syntax=docker/dockerfile:1

# global build-time arguments for FROM statements
ARG UERANSIM_VERSION="v3.2.7"
ARG UBUNTU_VERSION="jammy"

FROM fgftk/base-ueransim:${UERANSIM_VERSION} AS builder

FROM ubuntu:${UBUNTU_VERSION}

LABEL organization="FgfTk@fb2.fra-uas.de"

# build-time arguments
ARG DEBIAN_FRONTEND="noninteractive"

# install dependencies
RUN apt-get update && apt-get install libsctp-dev lksctp-tools \
    iproute2 iputils-ping net-tools ethtool procps grep -y

# change working directory
WORKDIR /UERANSIM

# copy executable and default config
COPY --from=builder /UERANSIM/build/nr-gnb /UERANSIM/nr-gnb
COPY --from=builder /UERANSIM/build/nr-cli /UERANSIM/nr-cli
COPY --from=builder /UERANSIM/config/open5gs-gnb.yaml /UERANSIM/config/open5gs-gnb.yaml

ENTRYPOINT [ "/UERANSIM/nr-gnb" ]

# use CMD to provide arguments to ENTRYPOINT (can be overridden by user)
CMD [ "-c", "/UERANSIM/config/open5gs-gnb.yaml" ]