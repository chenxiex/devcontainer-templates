ARG VARIANT="3-trixie"
FROM mcr.microsoft.com/devcontainers/python:2-${VARIANT}

# Install uv in the pre-built image so template users do not repeat this work.
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

# Keep the named cache volume writable when Dev Containers remaps the user's UID.
RUN mkdir -p /cache && chmod 0777 /cache
