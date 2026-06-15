[update-readmes]   Mode: rewrite — migrating to template structure...
# incus-windows

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/incus-windows)

<!-- AI:start:what-it-does -->
_Description pending._
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
_Architecture documentation pending._
<!-- AI:end:architecture -->

## Install

<!-- Add installation instructions here. This section is yours — the AI will not modify it. -->

```bash
git clone https://github.com/Interested-Deving-1896/incus-windows.git
cd incus-windows
```

## Usage


The common workflow is to run the `build.sh` script with the Windows
version you want to have an VM image for. If you'd like to use a
custom ISO or , read below.

Note that, unless the user changed the unattended install configuration,
all systems have an administrator-level account named `admin` with
password `changeme`.

```
# Build a disk image (disk.qcow2) and metadata archive (incus.tar.xz)
# in ./output/win2022/
sh incus-windows/build.sh 2022

# Import into incus using helper script
sh incus-windows/tools/import.sh ./output/win2022/

# Create and launch the virtual machine
incus init win2022 w22 -c security.secureboot=false
incus config device add w22 iso-agent disk source=agent:config
incus start w22
incus init win2008 w2k8 -c security.secureboot=false -c security.csm=true
incus config device add w2k8 iso-agent disk source=agent:config
incus start w2k8

# Optionally, create a profile for easier launches
incus profile create winvm
incus profile device add winvm iso-agent disk source=agent:config
incus launch win2022 w22 -p default -p winvm
```

## Configuration

<!-- Document configuration options here. This section is yours — the AI will not modify it. -->

## CI

<!-- AI:start:ci -->
_CI documentation pending._
<!-- AI:end:ci -->

## Mirror chain

<!-- AI:start:mirror-chain -->
This repo is maintained in [`Interested-Deving-1896/incus-windows`](https://github.com/Interested-Deving-1896/incus-windows) and mirrored through:

```
Interested-Deving-1896/incus-windows  ──►  OpenOS-Project-OSP/incus-windows  ──►  OpenOS-Project-Ecosystem-OOC/incus-windows
```

Changes flow downstream automatically via the hourly mirror chain in
[`fork-sync-all`](https://github.com/Interested-Deving-1896/fork-sync-all).
Direct commits to OSP or OOC are detected and opened as PRs back to `Interested-Deving-1896`.
<!-- AI:end:mirror-chain -->

## Contributors

<!-- AI:start:contributors -->
_Contributors pending._
<!-- AI:end:contributors -->

## Origins

<!-- AI:start:origins -->
_Original project — no upstream fork._
<!-- AI:end:origins -->

## Resources

<!-- AI:start:resources -->
_No additional resource files found._
<!-- AI:end:resources -->

## License

<!-- AI:start:license -->
<!-- License not detected — add a LICENSE file to this repo. -->
<!-- AI:end:license -->
