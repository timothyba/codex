FROM ubuntu:22.04

# Set non-interactive mode for apt
ARG DEBIAN_FRONTEND=noninteractive

# Install dependencies and clean up in a single RUN command
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    software-properties-common \
    build-essential \
    curl \
    git \
    ca-certificates \
    pkg-config \
    clang \
    musl-tools \
    libssl-dev && \
    add-apt-repository --yes universe && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Non-root dev user
ARG USER=dev
ARG UID=1000
RUN useradd -m -u $UID $USER

USER $USER

# Install Rust + musl target as dev user
RUN curl -sSf https://sh.rustup.rs | sh -s -- -y --profile minimal && \
    ~/.cargo/bin/rustup target add aarch64-unknown-linux-musl

ENV PATH="/home/${USER}/.cargo/bin:${PATH}"

WORKDIR /workspace
