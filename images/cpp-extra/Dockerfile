ARG VARIANT="debian13"
FROM mcr.microsoft.com/devcontainers/cpp:${VARIANT}

ARG CLICE_VERSION="1.0.0"

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends ca-certificates curl clang-tidy clang-format clang-tools \
    && rm -rf /var/lib/apt/lists/*

# Keep the bundled Clang resource headers beside the clice executable.
RUN set -eux; \
    case "$(dpkg --print-architecture)" in \
        amd64) clice_arch="x86_64" ;; \
        arm64) clice_arch="aarch64" ;; \
        *) echo "Unsupported clice architecture: $(dpkg --print-architecture)" >&2; exit 1 ;; \
    esac; \
    curl --fail --location --retry 3 \
        "https://github.com/clice-io/clice/releases/download/v${CLICE_VERSION}/clice-${CLICE_VERSION}.${clice_arch}-unknown-linux-gnu.tar.gz" \
        --output /tmp/clice.tar.gz; \
    mkdir -p /opt/clice; \
    tar -xzf /tmp/clice.tar.gz -C /opt/clice --strip-components=1; \
    ln -s /opt/clice/bin/clice /usr/local/bin/clice; \
    rm /tmp/clice.tar.gz; \
    clice --version
