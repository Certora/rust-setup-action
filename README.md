# Certora Rust Setup Action

This GitHub Action sets up the Rust environment for Certora Prover.
In most cases this action is part of the [Certora Run Action](https://github.com/Certora/certora-run-action)
and should not be used directly.

Documentation:

- [Certora Prover Solana Documentation](https://docs.certora.com/en/latest/docs/solana/installation.html)
- [Cargo Certora SBF](https://github.com/Certora/cargo-certora-sbf)

## Usage

```yaml
name: Certora Rust Setup
on: [push, pull_request]
jobs:
  certora_rust_setup:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      # Set up Rust environment
      - name: Set up Rust
        uses: Certora/rust-setup-action@v1

      # Call certora-sbf or other cargo related commands
      - name: cargo certora-sbf --help

      # Submit verification jobs to Certora Prover
      # This step normally uses this actions to set up the Rust environment
      - name: Submit verification jobs to Certora Prover
          uses: Certora/certora-run-action@v1
          with:
          configurations: |-
              integrity.conf
              vault_consistency.conf
              no_dilution_processor.conf
              solvency_processor.conf
              fees.conf
              inflation.conf
          job-name: "Test Action"
          ecosystem: solana
          working-directory: programs/vault/src/certora/confs
          certora-key: ${{ secrets.CERTORAKEY }}
          env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

## Example Configurations

- [Vault Tutorial](https://github.com/Certora/certora-vault-tutorial)
- [Certora Run Action](https://github.com/Certora/certora-run-action)
