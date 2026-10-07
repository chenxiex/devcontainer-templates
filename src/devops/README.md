
# DevOps (devops)

Dev environment on Alpine Linux for Dockerfiles, CI workflows and helper scripts. Includes shellcheck and shfmt.

## Options

| Options Id | Description | Type | Default Value |
|-----|-----|-----|-----|
| imageVariant | Published Alpine image variant: | string | alpine3.23 |

This template uses a [pre-built image](https://containers.dev/implementors/reference/#prebuilding), so the tools below do not need to be installed every time a user creates the container.

* **Image**: `ghcr.io/chenxiex/devcontainer-templates/devcontainer-devops-<imageVariant>:latest`
* **Image source**: [`images/devops`](https://github.com/chenxiex/devcontainer-templates/tree/main/images/devops)

The generated `.devcontainer/Dockerfile` intentionally contains only the pre-built base image plus commented examples. Add project-specific `RUN`, `COPY`, or other Dockerfile instructions after `FROM` as usual.

## Included tools

* [ShellCheck](https://www.shellcheck.net/) for linting, picked up automatically by Bash IDE
* [shfmt](https://github.com/mvdan/sh) for formatting, picked up automatically by Bash IDE
* [Bash IDE](https://github.com/bash-lsp/bash-language-server) language server support
* VS Code extensions for GitHub Actions workflows, Docker Compose and Dockerfiles


---

_Note: This file was auto-generated from the [devcontainer-template.json](https://github.com/chenxiex/devcontainer-templates/blob/main/src/devops/devcontainer-template.json).  Add additional notes to a `NOTES.md`._
