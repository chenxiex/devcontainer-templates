FROM mcr.microsoft.com/devcontainers/python:2-${templateOption:imageVariant}

# Install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

# Keep the named cache volume writable when Dev Containers remaps the user's UID.
RUN mkdir -p /cache && chmod 0777 /cache

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>
