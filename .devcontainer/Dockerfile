ARG LINUX_DIST=ubuntu
ARG LINUX_DIST_VERSION=24.04
ARG DEBIAN_DISTRIBUTION=noble
ARG USERID=1000
ARG GID=1000
ARG BUILDARCH=aarch64

FROM ${LINUX_DIST}:${LINUX_DIST_VERSION}

ARG LINUX_DIST
ARG LINUX_DIST_VERSION
ARG DEBIAN_DISTRIBUTION
ARG USERID    
ARG GID
ARG BUILDARCH

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    apt-transport-https \
    ca-certificates \
    sudo make cmake lldb liblldb-dev clang libclang-dev libssl-dev git \
    wget curl gnupg lsb-release protobuf-compiler iptables

RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
ENV PATH="/root/.cargo/bin:${PATH}"

WORKDIR /workspaces/tcpproxy
ENTRYPOINT ["bash"]