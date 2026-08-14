
# Python with uv (python-uv)

Develop Python 3 applications with uv

## Options

| Options Id | Description | Type | Default Value |
|-----|-----|-----|-----|
| imageVariant | Python version (use -bookworm, or -bullseye variants on local arm64/Apple Silicon): | string | 3.14-trixie |

This template references an image that was [pre-built](https://containers.dev/implementors/reference/#prebuilding) to automatically include needed devcontainer.json metadata.

* **Image**: mcr.microsoft.com/devcontainers/python ([source](https://github.com/devcontainers/images/tree/main/src/python))
* **Applies devcontainer.json contents from image**: Yes ([source](https://github.com/devcontainers/images/blob/main/src/python/.devcontainer/devcontainer.json))

## UV cache
This template mounts the named Docker volume `python-uv-cache` at `/cache`, allowing containers created from the template to share uv's cache without reading from or writing to the host's home directory. It also sets the default virtual environment location to `/cache/venv-for${localWorkspaceFolder}` to allow soft-link package installation. Check `devcontainer.json` for more details.

## Installing or updating Python utilities

This container installs all Python development utilities using [pipx](https://pipxproject.github.io/pipx/) to avoid impacting the global Python environment. You can use this same utility add additional utilities in an isolated environment. For example:

```bash
pipx install prospector
```

See the [pipx documentation](https://pipxproject.github.io/pipx/docs/) for additional information.


---

_Note: This file was auto-generated from the [devcontainer-template.json](https://github.com/chenxiex/devcontainer-templates/blob/main/src/python-uv/devcontainer-template.json).  Add additional notes to a `NOTES.md`._
