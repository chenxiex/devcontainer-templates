FROM mcr.microsoft.com/devcontainers/cpp:1-${templateOption:imageVariant}

ARG REINSTALL_CMAKE_VERSION_FROM_SOURCE="${templateOption:reinstallCmakeVersionFromSource}"

# Optionally install the cmake for vcpkg
COPY ./reinstall-cmake.sh /tmp/

RUN if [ "${REINSTALL_CMAKE_VERSION_FROM_SOURCE}" != "none" ]; then \
        chmod +x /tmp/reinstall-cmake.sh && /tmp/reinstall-cmake.sh ${REINSTALL_CMAKE_VERSION_FROM_SOURCE}; \
    fi \
    && rm -f /tmp/reinstall-cmake.sh

ARG SWITCHMIRROR="${templateOption:switchMirror}"

RUN if [ "${SWITCHMIRROR}" != "none" ]; then \
        curl -sSL https://linuxmirrors.cn/main.sh | bash -s -- \
        --source ${SWITCHMIRROR} \
        --protocol https \
        --use-intranet-source false\
        --backup true \
        --upgrade-software false \
        --clean-cache true \
        --ignore-backup-tips; \
    fi

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends clangd

# [Optional] Uncomment this section to install additional vcpkg ports.
# RUN su vscode -c "${VCPKG_ROOT}/vcpkg install <your-port-name-here>"

# [Optional] Uncomment this section to install additional packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>
