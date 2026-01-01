# Building The Code

## Supported Platforms

See [supported platforms](README.md#Supported-Platforms).

## Prerequisites

- CMake 4.2.1 or higher
- Visual Studio 2026

## Configuring CMake

The following variables must be configured.

- `CMAKE_INSTALL_PREFIX`: The install directory. Must be set to the mod directory in Steam directory. e.g.

  ```text
  C:\Program Files (x86)\steamapps\common\Half-Life\<MyMod>
  ```

- `CPACK_PACKAGE_NAME`: Prefix to prepend to the name of the mod package.

## First Time Build

Build the `INSTALL` project. This will build `hl_cdll` and `hldll` projects and will copy all mod files to the mod directory (Install directory) and run the setup script automatically.

## Launching From Visual Studio

1. Ensure Steam is running.
2. Right click on either `hl_cdll` or `hldll` and select Debug -> Start New Instance

## Projects

- `hl_cdll`: Game client project
- `hldll`: Game server project
- `INSTALL`: Builds hl_cdll and hldll projects, copies all mod files to the mod directory.
- `PACKAGE`: Builds everything and creates the mod package.
