
# C++ extra (cpp-extra)

Develop C++ applications on Linux. Includes Debian C++ build tools and the clice language server.

## Options

| Options Id | Description | Type | Default Value |
|-----|-----|-----|-----|
| imageVariant | Published Debian / Ubuntu image variant: | string | debian13 |
| reinstallCmakeVersionFromSource | Install CMake version different from what base image has already installed. | string | none |

This template uses a [pre-built image](https://containers.dev/implementors/reference/#prebuilding), so the C++ tools and clice do not need to be installed every time a user creates the container.

* **Image**: `ghcr.io/chenxiex/devcontainer-templates/devcontainer-cpp-extra-<imageVariant>:latest`
* **Image source**: [`images/cpp-extra`](https://github.com/chenxiex/devcontainer-templates/tree/main/images/cpp-extra)

The generated `.devcontainer/Dockerfile` uses the pre-built base image, optionally reinstalls the selected CMake version, and retains commented examples. Add project-specific `RUN`, `COPY`, or other Dockerfile instructions as usual.

### Using clice

The image installs [clice 1.0.0](https://github.com/clice-io/clice/releases/tag/v1.0.0) from its official Linux release package for x64 or ARM64. Image maintainers can select another release with the `CLICE_VERSION` build argument in `images/cpp-extra/Dockerfile`.

The template installs the official `clice-io.clice` VS Code extension and sets `clice.executable` to `/usr/local/bin/clice`. It disables clangd and C/C++ IntelliSense to avoid duplicate language services; the C/C++ extension remains available for debugging. The image also retains `clang-format`, `clang-tidy`, and `clang-tools` as standalone tools.

For CMake projects, generate a compilation database with a Makefile or Ninja generator:

```sh
cmake -S . -B build -DCMAKE_EXPORT_COMPILE_COMMANDS=ON
```

clice discovers `compile_commands.json` in the project root and its immediate subdirectories, including `build/`. See the [clice project setup guide](https://docs.clice.io/clice/guide/quick-start) for other build systems.

When migrating an existing container, apply these extension and settings changes to its `.devcontainer/devcontainer.json`, then rebuild the container after the updated pre-built image has been published. If the clangd extension is already installed, the `clangd.enable` setting disables its language service.

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
