# Terrain agent

Release artifacts for the Terrain Labs robot agent.

This repository hosts the compiled binaries that robots install via the
Terrain Labs install script. It exists so that headless robots can
download the agent without needing any GitHub credentials.

## Install

On any Linux amd64 or arm64 host (Jetson, Raspberry Pi 4/5, Intel NUC,
generic server):

```bash
curl -fsSL https://api.terrainlabs.io/install.sh | sudo bash -s -- --token <claim-code>
```

Get a claim code from your robot detail page in Terrain Studio.

## Release shape

Each release tag (e.g. `agent-v0.1.0`) contains three assets:

| File | Purpose |
|---|---|
| `terrain-linux-amd64` | Static binary for x86_64 Linux, stripped, CGO_ENABLED=0 |
| `terrain-linux-arm64` | Static binary for aarch64 Linux, stripped, CGO_ENABLED=0 |
| `checksums.txt` | SHA256 checksums for the binaries |

Both binaries are statically linked — no runtime dependencies on the host.

## Verifying a download by hand

```bash
curl -fsSL -O https://github.com/terrainlabs/terrain-agent/releases/download/agent-v0.1.0/terrain-linux-arm64
curl -fsSL -O https://github.com/terrainlabs/terrain-agent/releases/download/agent-v0.1.0/checksums.txt
sha256sum --ignore-missing -c checksums.txt
```

## More

Platform and dashboard: https://terrainlabs.io
