
# C++ extra (cpp-extra)

Develop C++ applications on Linux. Includes Debian C++ build tools and dev tools such as clangd.

## Options

| Options Id | Description | Type | Default Value |
|-----|-----|-----|-----|
| imageVariant | Published Debian / Ubuntu image variant: | string | debian13 |
| reinstallCmakeVersionFromSource | Install CMake version different from what base image has already installed. | string | none |

This template uses a [pre-built image](https://containers.dev/implementors/reference/#prebuilding), so the C++ and LLVM tools do not need to be installed every time a user creates the container.

* **Image**: `ghcr.io/chenxiex/devcontainer-templates/devcontainer-cpp-extra-<imageVariant>:latest`
* **Image source**: [`images/cpp-extra`](https://github.com/chenxiex/devcontainer-templates/tree/main/images/cpp-extra)

The generated `.devcontainer/Dockerfile` uses the pre-built base image, optionally reinstalls the selected CMake version, and retains commented examples. Add project-specific `RUN`, `COPY`, or other Dockerfile instructions as usual.

### Using Vcpkg

This dev container and its associated image includes a clone of the [`Vcpkg`](https://github.com/microsoft/vcpkg) repo for library packages, and a bootstrapped instance of the [Vcpkg-tool](https://github.com/microsoft/vcpkg-tool) itself.

The minimum version of `cmake` required to install packages can be higher than the version available in a distribution's package repository. `Vcpkg` can download a compatible version for its own use, or you can install a global CMake version through the template's `reinstallCmakeVersionFromSource` option. This optional installation remains in the generated Dockerfile and is not included in the pre-built image.

Most additional library packages installed using Vcpkg will be downloaded from their [official distribution locations](https://github.com/microsoft/vcpkg#security). To configure Vcpkg in this container to access an alternate registry, more information can be found here: [Registries: Bring your own libraries to vcpkg](https://devblogs.microsoft.com/cppblog/registries-bring-your-own-libraries-to-vcpkg/).

To update the available library packages, pull the latest from the git repository using the following command in the terminal:

```sh
cd "${VCPKG_ROOT}"
git pull --ff-only
```

> Note: Please review the [Vcpkg license details](https://github.com/microsoft/vcpkg#license) to better understand its own license and additional license information pertaining to library packages and supported ports.


---

_Note: This file was auto-generated from the [devcontainer-template.json](https://github.com/chenxiex/devcontainer-templates/blob/main/src/cpp-extra/devcontainer-template.json).  Add additional notes to a `NOTES.md`._
