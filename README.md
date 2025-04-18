# Codex CLI Nix Flake

A Nix flake for building and running the OpenAI Codex CLI tool - a terminal-based coding assistant.

## Description

This flake packages the OpenAI Codex CLI tool for use with Nix. It provides a convenient way to install and run the Codex CLI in a reproducible environment.

## Usage

### Direct Installation

```bash
nix profile install github:castrozan/codex-flake
```

### Development Shell

To enter a development shell with Codex CLI available:

```bash
nix develop github:castrozan/codex-flake
```

### As a Flake Input

Add `codex-flake` to your flake inputs and reference its package in your outputs:

```nix
{
  inputs = {
    nixpkgs.url = "github:NixOS/nixpkgs/nixos-unstable";
    flake-utils.url = "github:numtide/flake-utils";
    codex-flake = {
      url = "github:castrozan/codex-flake";
      inputs.flake-utils.follows = "flake-utils";
    };
  };
}
```

For NixOS system configurations, you can add `codex` to `environment.systemPackages`. For example, in a separate `configuration.nix`:

```nix
{ pkgs, inputs, ... }:
{
  environment.systemPackages = [
    inputs.codex-flake.packages.${pkgs.system}.default
  ];
}
```
## License

The build scripts in this repository are dual-licensed under the terms of the MIT license and the Apache License (Version 2.0).

See [LICENSE-MIT](LICENSE-MIT) and [LICENSE-APACHE](LICENSE-APACHE) for details.

The OpenAI Codex CLI tool itself is licensed under the Apache License 2.0.

## Contribution

Made with ❤️ by [castrozan](https://github.com/castrozan)

## Disclaimer

This is an unofficial Nix packaging of the OpenAI Codex CLI tool. It is not affiliated with or endorsed by OpenAI.
