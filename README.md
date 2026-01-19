# QEMU Builds

[![QEMU Build and Release](https://github.com/marten-vm/qemu-builds/actions/workflows/release.yml/badge.svg)](https://github.com/marten-vm/qemu-builds/actions/workflows/release.yml)

Automated nightly builds of QEMU for **Windows (x86_64)** and **macOS (Intel & Apple Silicon)**, optimized for performance and minimal footprint.

This repository provides a CI/CD pipeline to build QEMU static binaries using MinGW64 (Windows) and Clang (macOS). These builds are intended to be used as a backend for Linux learning applications and other headless virtualization needs.

## Features

- **Platforms:** 
    - Windows x86_64 (MinGW64)
    - macOS x86_64 (Intel)
    - macOS aarch64 (Apple Silicon)
- **Optimization:** `-O2` (maximize performance)
- **Configuration:** Headless (No GTK, SDL, VNC, Spice)
- **Compact:** Includes only essential binaries and firmware.
- **Standalone:** Bundles necessary DLLs/Dylibs and firmware for immediate use.
- **Architecture Aware:**
    - Windows: Uses **WHPX** acceleration.
    - macOS: Uses **HVF** (Hypervisor.framework) acceleration.

## Build Details

- **Source:** Upstream [QEMU](https://gitlab.com/qemu-project/qemu) stable tags.
- **Compiler:** 
    - Windows: GCC (MinGW-w64)
    - macOS: Clang (Apple LLVM)
- **Accelerator:** 
    - Windows: WHPX
    - macOS: HVF

## Usage

Download the latest tarball from the [Releases](https://github.com/marten-vm/qemu-builds/releases) page. Ensure you have the [zstd](https://github.com/facebook/zstd) utility to decompress the archive if your toolchain doesn't support it natively.

```powershell
tar -I zstd -xf qemu-windows-x86_64-vX.Y.Z.tar.zst
```

## License

The CI/CD configuration in this repository is licensed under the [MIT License](LICENSE).
QEMU itself is licensed under GPLv2 and separate licenses for bundled firmware. See the `licenses` directory in the release archive for details.
