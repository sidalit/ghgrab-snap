<div align="center">

# ghgrab

**Browse and download files from GitHub, GitLab and other forges.**

[![ghgrab](https://snapcraft.io/ghgrab/badge.svg)](https://snapcraft.io/ghgrab)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64, arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [ghgrab](https://github.com/abhixdd/ghgrab), a terminal tool that browses repositories and downloads files, folders and release assets without cloning.

</div>

---

## Getting Started

<a href="https://snapcraft.io/ghgrab"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install ghgrab
ghgrab config set path "$HOME/Downloads"
ghgrab https://github.com/rust-lang/rust
```

Select files with `Space` and download them with `d`. Use `ghgrab rel owner/repo --extract` for release assets, and `ghgrab agent tree <url>` for JSON output.

## Configure

There are no `snap set` options. ghgrab stores its settings in `~/snap/ghgrab/current/.config`:

| Setting | Accepted values | Default |
| --- | --- | --- |
| `ghgrab config set path <dir>` | An absolute folder path | `~/snap/ghgrab/current/Downloads` |
| `ghgrab config set token <token>` | A GitHub personal access token | Not set |

ghgrab also reads `GHGRAB_GITHUB_TOKEN` or `GITHUB_TOKEN` from the environment. Use `--cwd` to download into the current folder for one run.

For downloads to removable storage:

```bash
sudo snap connect ghgrab:removable-media
```

## Limitations

- `--token auto` and `--token gh` cannot run the host's `gh` command. Pass a token or set `GITHUB_TOKEN` instead.
- `ghgrab mcp --install` cannot edit host assistant configurations in hidden folders. Add `/snap/bin/ghgrab mcp` to your assistant's MCP configuration manually.
- Downloads must go to a normal folder under your home directory or to connected removable storage. Hidden folders directly under your home directory are not accessible.
- The short `ghg` command is not included; create one with `sudo snap alias ghgrab ghg`.

## Build

```bash
git clone https://github.com/sidalit/ghgrab-snap.git
cd ghgrab-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/ghgrab-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/abhixdd/ghgrab/issues).

## License

Snap packaging: [MIT](LICENSE).
