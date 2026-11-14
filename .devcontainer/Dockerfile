FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

ARG GO_VERSION=1.25.0
ARG PYTHON_VERSION=3.12

ENV DEBIAN_FRONTEND=noninteractive

# System dependencies
RUN apt-get update && apt-get install -y \
    curl \
    wget \
    git \
    unzip \
    make \
    jq \
    build-essential \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Go
RUN curl -fsSL \
    https://go.dev/dl/go${GO_VERSION}.linux-amd64.tar.gz \
    -o /tmp/go.tar.gz \
    && tar -C /usr/local -xzf /tmp/go.tar.gz \
    && rm /tmp/go.tar.gz

ENV PATH="/usr/local/go/bin:${PATH}"

# Python is installed through the base image's
# Ubuntu package repositories for this initial setup.
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    python3-venv \
    && rm -rf /var/lib/apt/lists/*

# uv
RUN curl -LsSf https://astral.sh/uv/install.sh \
    | sh

ENV PATH="/root/.local/bin:${PATH}"

USER vscode

ENV PATH="/home/vscode/.local/bin:${PATH}"

WORKDIR /workspace/helix