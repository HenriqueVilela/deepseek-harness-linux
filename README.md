# DeepSeek Harness

English | [中文](README.zh.md)

DeepSeek Harness (`dsh`) is an open-source agent harness developed by [DeepSeek AI](https://deepseek.com).

It is built on an **everything-is-a-plugin** architecture and powered by [Cordis](https://github.com/cordiverse/cordis), whose design is described in [_A Programming Paradigm for Spatiotemporal Composability_](https://arxiv.org/abs/2608.25512).

Documentation: [https://deepseek-harness.github.io/deepseek-harness/](https://deepseek-harness.github.io/deepseek-harness/)

## Developer preview

DeepSeek Harness is in _developer preview_ and iterating rapidly. **THERE WILL BE COMPATIBILITY-BREAKING CHANGES.**

Review the [safety notice](SAFETY.md) before running the project.

## Run

### Run from `npm`

Install `Node.js`, then run:

```sh
npx @deepseek-ai/dsh web
```

The command starts the Web UI at `http://127.0.0.1:3080` by default and opens it in the default browser for a local launch. An SSH launch only prints the host URL because the SSH client or editor owns the local forwarded address. Pass `--no-open` to run the server without opening a browser. See [Web UI guide](docs/user/guide/index.md).

### Run from source

To run from a repository checkout:

```sh
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
pnpm install
pnpm run build
pnpm dsh web
```

`pnpm run build` prepares the repository artifacts. `pnpm dsh web` uses those built artifacts without rebuilding.

### Linux (Ubuntu / Debian)

#### Desktop App (.AppImage & .deb)

DeepSeek Harness Desktop is available on Linux for both `x64` and `arm64` architectures.

##### Running the AppImage

```sh
# Make the AppImage executable and launch
chmod +x deepseek-harness-*-linux-x64.AppImage
./deepseek-harness-*-linux-x64.AppImage
```

> [!TIP]
> On Ubuntu 24.04 and newer, install `libfuse2t64` if your system does not yet have FUSE 2 installed:
> ```sh
> sudo apt update && sudo apt install -y libfuse2t64
> ```

##### Installing the Debian Package (.deb)

```sh
sudo apt update
sudo apt install -y ./deepseek-harness-*-linux-amd64.deb

# Launch from your application launcher or terminal
deepseek-harness
```

#### Build and run Desktop from source on Linux

1. **Install system prerequisites:**
   - Linux (Ubuntu 22.04+ or Debian 12+ recommended)
   - Node.js >= 24.9.0 and pnpm >= 11
   - Build essentials and Python 3:
     ```sh
     sudo apt update && sudo apt install -y curl git python3 build-essential
     ```

2. **Clone and install dependencies:**
   ```sh
   git clone https://github.com/deepseek-ai/deepseek-harness.git
   cd deepseek-harness
   pnpm install
   ```

3. **Start Desktop in development mode:**
   ```sh
   pnpm run dev:desktop
   ```

4. **Package native Linux installers (.AppImage and .deb):**
   ```sh
   # Package for x64
   pnpm run package:desktop:linux:x64

   # Package for ARM64
   pnpm run package:desktop:linux:arm64
   ```
   Built artifacts are output to `apps/desktop/.desktop-build/targets/linux-x64/artifacts/`.

## Community and support

- Submit feedback or bug reports through [GitHub Discussions](https://github.com/deepseek-ai/deepseek-harness/discussions).
- Add the [`dsh-plugin`](https://github.com/topics/dsh-plugin) topic to your plugin repository for discoverability.
- Join <a href="https://discord.gg/4MrtZUhpxg">DeepSeek Harness Discord community</a>.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Development

Start with the [development guide](docs/development.md) and [architecture documentation](docs/architecture.md).

`pnpm run dev:web` builds, serves, and rebuilds client bundles on source edits in one terminal, and `make help` lists the matching Make targets for Web and Desktop; the guide's application commands section owns the full table.

For agents, follow [AGENTS.md](AGENTS.md).

## Citation

```bibtex
@misc{deepseek-harness2026,
  title={DeepSeek Harness: Everything is a Plugin},
  author={DeepSeek-AI},
  year={2026},
  publisher={GitHub},
  howpublished={\url{https://github.com/deepseek-ai/deepseek-harness}},
}
```

## License

[MIT](LICENSE)

Third-party dependencies and their licenses are disclosed in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
