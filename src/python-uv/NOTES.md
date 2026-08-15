This template uses a [pre-built image](https://containers.dev/implementors/reference/#prebuilding), so uv and the shared cache directory do not need to be installed every time a user creates the container.

* **Image**: `ghcr.io/chenxiex/devcontainer-templates/devcontainer-python-uv-<imageVariant>:latest`
* **Image source**: [`images/python-uv`](https://github.com/chenxiex/devcontainer-templates/tree/main/images/python-uv)

The generated `.devcontainer/Dockerfile` intentionally contains only the pre-built base image plus commented examples. Add project-specific `RUN`, `COPY`, or other Dockerfile instructions after `FROM` as usual.

## UV cache
This template mounts the named Docker volume `python-uv-cache` at `/cache`, allowing containers created from the template to share uv's cache without reading from or writing to the host's home directory. It also sets the default virtual environment location to `/cache/venv-for${localWorkspaceFolder}` to allow soft-link package installation. Check `devcontainer.json` for more details.

## Installing or updating Python utilities

This container installs all Python development utilities using [pipx](https://pipxproject.github.io/pipx/) to avoid impacting the global Python environment. You can use this same utility add additional utilities in an isolated environment. For example:

```bash
pipx install prospector
```

See the [pipx documentation](https://pipxproject.github.io/pipx/docs/) for additional information.
