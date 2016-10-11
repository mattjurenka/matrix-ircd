# Matrix IRCd

[![Build Status](https://travis-ci.org/matrix-org/matrix-ircd.svg?branch=master)](https://travis-ci.org/matrix-org/matrix-ircd)

An IRCd implementation backed by Matrix. Inspired by [PTO](https://github.com/tdfischer/pto)!

Join the discussion on the Matrix channel: [#matrix-ircd:matrix.org](https://matrix.to/#/#matrix-ircd:matrix.org)

## Status

**This is a work in progress.** Matrix IRCd should be stable enough to hack on
and test, but has not been tested in production or for any length of time.

See the GitHub issues page for a more detailed breakdown of what is left to do.


## Building

Matrix IRCd currently requires using a nightly compiler of rust<sup>1</sup>.
Building and installing uses the standard `cargo` commands.

To run a plain debug version:

```
cargo run -- --url "https://matrix.org"
```

To build with trace logging:

```
cargo build --features trace_logging
```


<sup>1</sup> It is recommended to use a tool such as [rustup](rustup.rs) to
manage the rust compiler toolchains.


## Usage

```
IRC Matrix Daemon 0.1.0

USAGE:
    matrix-ircd [OPTIONS] --url <MATRIX_HS>

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
    -b, --bind <BIND>        Sets the address to bind to. Defaults to 127.0.0.1:5999
        --cert <CERT>        Sets the PEM file to read TLS cert from
        --url <MATRIX_HS>    The base url of the Matrix HS
        --pkey <PKEY>        Sets the PEM file to read TLS pkey from
```

The `MATRIX_HS` URL should be of the form: `https://matrix.org`. Plain HTTP is
also supported but should *only* be used for testing and development.

Supplying both `pkey` and `cert` arguments will cause Matrix IRCd to listen
on TLS, otherwise it will use plain TCP.


## Development

Matrix IRCd aims to build with zero standard warning and no clippy warnings.

To run clippy use (after install clippy):

```
cargo clippy --features clippy
```

The feature flag disables certain spurious warnings related to third party
crates.
