<!--
# SPDX-FileCopyrightText: 2026 Jean-Pierre De Jesus DIAZ <me@jeandudey.tech>
#
# SPDX-License-Identifier: MIT
-->

# Bitcoin rock

A distroless rock image for [Bitcoin Core](https://github.com/bitcoin/bitcoin).

## Usage

```bash
docker pull ghcr.io/jeandudey/bitcoin:30.2-1
docker run -it ghcr.io/jeandudey/bitcoin:30.2-1
```

The image expects the data directory to be at:

```
/var/lib/bitcoin
```

No configuration is provided other than passing `-datadir=/var/lib/bitcoin`.

The wallet has been also disabled.

## Utilities

This images provides these two binaries which can be used to check the status
of the node:

- `/usr/bin/bitcoind-is-alive`: Check that the daemon is alive.
- `/usr/bin/bitcoind-is-synchronized`: Check that the daemon has finished synchronization.

Both expect an address parameter (for example: `127.0.0.1:8332`) to be passed, it uses
the `bitcoin-cli` utility and reads the cookie file from the data directory, it also
requires the node to provide the RPC API (with `rest=1`).

These are not provided by default in the Pebble layer as these checks depend on the
configuration of the node.

Also these use `-rpcwait` so it is important to place a timeout on these commands.

## Size

The goal of this image is to reduce size and attack surface by having less
components in the final image, in comparison, the Docker image from
`docker.io/bitcoin/bitcoin:latest` is about 206 MB and this
image is around 45 MB.
