# syntax=docker/dockerfile:1
FROM golang:1.24-bookworm

ARG NODE_MAJOR=22
ARG CLAUDE_CODE_VERSION=2.1.310
ARG USERNAME=nightrun
ARG USER_UID=1000
ARG USER_GID=1000

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    git \
    gnupg \
    jq \
    procps \
    python3 \
    python3-pip \
    python3-venv \
    build-essential \
    && mkdir -p /etc/apt/keyrings \
    && curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg \
    && echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_${NODE_MAJOR}.x nodistro main" > /etc/apt/sources.list.d/nodesource.list \
    && apt-get update && apt-get install -y --no-install-recommends nodejs \
    && npm install -g "@anthropic-ai/claude-code@${CLAUDE_CODE_VERSION}" \
    && npm cache clean --force \
    && rm -rf /var/lib/apt/lists/*

# Create non-root user with fixed UID/GID matching host/WSL user.
RUN groupadd --gid "${USER_GID}" "${USERNAME}" \
    && useradd --uid "${USER_UID}" --gid "${USER_GID}" --create-home --shell /bin/bash "${USERNAME}" \
    && mkdir -p \
        "/home/${USERNAME}/.claude" \
        "/home/${USERNAME}/.gemini" \
        "/home/${USERNAME}/.local/bin" \
        "/home/${USERNAME}/.local/share/claude" \
        "/home/${USERNAME}/.cache/nightrun" \
        /go \
        /workspace \
    && chown -R "${USER_UID}:${USER_GID}" "/home/${USERNAME}" /go /workspace \
    && git config --system --add safe.directory '*'

ENV HOME="/home/${USERNAME}"
ENV GOCACHE="/home/${USERNAME}/.cache/go-build"
ENV GOMODCACHE="/home/${USERNAME}/.cache/go-mod"
ENV PATH="/home/${USERNAME}/.local/bin:/usr/local/go/bin:/go/bin:${PATH}"
ENV NIGHTRUN_IN_CONTAINER=1

USER ${USERNAME}
WORKDIR /workspace
