# Certora Rust Setup Action

Usage:

```yaml
name: Certora Rust Setup
on: [push, pull_request]
jobs:
  certora_rust_setup:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Rust
        uses: Certora/rust-setup-action@main
        with:
          version: "1.86.0" # Specify the Rust version you want to use
```
