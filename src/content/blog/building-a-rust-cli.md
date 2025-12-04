---
title: 'Building a CLI Tool in Rust'
description: 'A step-by-step guide to creating fast command-line applications with Rust and clap'
pubDate: 2024-11-28
tags: ['rust', 'cli']
---

Rust is an excellent choice for CLI tools. Here's how to get started.

## Setting up the project

First, create a new Rust project with Cargo:

```bash
cargo new my-cli
cd my-cli
```

## Adding clap for argument parsing

Add clap to your `Cargo.toml`:

```toml
[dependencies]
clap = { version = "4.0", features = ["derive"] }
```

## Conclusion

Rust makes building CLI tools fast and reliable.
