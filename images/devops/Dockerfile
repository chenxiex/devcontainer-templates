ARG VARIANT="trixie"
FROM mcr.microsoft.com/devcontainers/base:${VARIANT}

# Install shell script tools in the pre-built image so template users do not repeat this work.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends shellcheck shfmt \
    && rm -rf /var/lib/apt/lists/*
