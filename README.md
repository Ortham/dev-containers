# Readme

This repository contains files needed to build a few container images that are useful as dev containers.

## rust-windows-gnu

This image is based on `mcr.microsoft.com/devcontainers/rust` and adds:

- the `x86_64-pc-windows-gnu` Rust target
- the latest Wine stable release (11.0 at time of writing)
- cargo-vet
- cargo-llvm-cov and the llvm-tools-preview Rustup component that it needs

It also sets the cargo runner for `x86_64-pc-windows-gnu` to be `wine`.

Build it using:

```
podman build -t ghcr.io/ortham/dev-rust-windows-gnu:latest rust-windows-gnu
```

## rust-mingw-gcc

This image is based on `ghcr.io/ortham/dev-rust-windows-gnu:latest` (i.e. the `rust-windows-gnu` image) and adds:

- cbindgen
- cmake
- g++-mingw-w64-x86-64
- A CMake toolchain file that uses x86_64-w64-mingw32-* and `wine` at `/opt/cmake/toolchains/x86_64-mingw-w64.cmake`

It also sets the `WINEPATH` environment variable to `/usr/lib/gcc/x86_64-w64-mingw32/14-win32`.

Build it using:

```
podman build -t ghcr.io/ortham/dev-rust-mingw-gcc:latest rust-mingw-gcc
```
