# mininal-wasm-clang 

[![Build and Release minimal-wasm-clang](https://github.com/NekoImageLand/mininal-wasm-clang/actions/workflows/build.yml/badge.svg)](https://github.com/NekoImageLand/mininal-wasm-clang/actions/workflows/build.yml)

> **Proudly built on Firefly DataCenter**

## What does this component do?

A minimal LLVM build tailored for use in the Cloudflare Worker Builder, currently providing only the WebAssembly target.

As you may know, when building Rust crates that include C/C++ code we typically rely on clang—but the Cloudflare Worker Builder [does not ship clang for us](https://developers.cloudflare.com/workers/ci-cd/builds/build-image/), which makes integrating a Rust-based Worker into Cloudflare 's CI/CD pipeline extremely difficult.

Since Cloudflare Worker [won’t let you install clang via apt](https://community.cloudflare.com/t/installing-ubuntu-packages-in-pages-builder/720127) and provides very little disk space (unpacking the \~1 GB official LLVM release runs out of space), I’ve crafted a minimal LLVM package specifically for my needs.

## What can this component do?

This minimized LLVM package contains only the WebAssembly target, built with `-C opt-level=z` (MinSizeRel), shared libraries enabled, and full LTO.