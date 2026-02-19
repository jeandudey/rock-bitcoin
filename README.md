<!--
# SPDX-FileCopyrightText: 2026 Jean-Pierre De Jesus DIAZ <me@jeandudey.tech>
#
# SPDX-License-Identifier: MIT
-->

# Bitcoin rock

A distroless rock image for [Bitcoin Core](https://github.com/bitcoin/bitcoin).

## Usage

```bash
docker pull ghcr.io/jeandudey/bitcoin:30.2
docker run -it ghcr.io/jeandudey/bitcoin:30.2
```

The image expects the data directory to be at:

```
/var/lib/bitcoin
```

No configuration is provided other than passing `-datadir=/var/lib/bitcoin`.

The wallet has been also disabled.

## Size

The goal of this image is to reduce size and attack surface by having less
components in the final image, in comparison, the Docker image from
`docker.io/bitcoin/bitcoin:latest` is about 206 MB and this
image is around 44.7 MB.
