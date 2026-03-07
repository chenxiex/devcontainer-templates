This template references an image that was [pre-built](https://containers.dev/implementors/reference/#prebuilding) to automatically include needed devcontainer.json metadata.

* **Image**: mcr.microsoft.com/devcontainers/python ([source](https://github.com/devcontainers/images/tree/main/src/python))
* **Applies devcontainer.json contents from image**: Yes ([source](https://github.com/devcontainers/images/blob/main/src/python/.devcontainer/devcontainer.json))

## UV cache
This template mount `~/.cache` into the container so uv cache can be shared among host and containers. It also set the default venv location to `~/.cache/venv-for${localWorkspaceFolder}` to allow soft link package installation. Checkout `devcontainer.json` for more details.

## Installing or updating Python utilities

This container installs all Python development utilities using [pipx](https://pipxproject.github.io/pipx/) to avoid impacting the global Python environment. You can use this same utility add additional utilities in an isolated environment. For example:

```bash
pipx install prospector
```

See the [pipx documentation](https://pipxproject.github.io/pipx/docs/) for additional information.
