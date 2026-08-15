ARG VARIANT="debian13"
FROM mcr.microsoft.com/devcontainers/cpp:${VARIANT}

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends clangd clang-tidy clang-format clang-tools \
    && rm -rf /var/lib/apt/lists/*
