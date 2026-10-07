ARG VARIANT="alpine3.23"
FROM mcr.microsoft.com/devcontainers/base:${VARIANT}

# Install shell script tools in the pre-built image so template users do not repeat this work.
RUN apk add --no-cache shellcheck shfmt
