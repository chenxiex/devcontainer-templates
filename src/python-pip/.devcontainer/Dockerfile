FROM mcr.microsoft.com/devcontainers/python:2-${templateOption:imageVariant}

# Install pip packages if requirements.txt is present
COPY requirements.txt noop.txt /tmp/pip-tmp/
RUN if [ -f "/tmp/pip-tmp/requirements.txt" ]; then pip install -r /tmp/pip-tmp/requirements.txt; fi \
    && rm -rf /tmp/pip-tmp

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>