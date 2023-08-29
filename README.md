# sel4cp-manifest

This repo contains sel4cp (seL4 Core Platform) with Capgemini-provided support for xHCI USB (USB 3.0)

Specifically, we have provided support for these USB devices:
* Keyboard
* Optical Mouse
* Resistive Touch Screen (Capacitative untested but believed to also be supported)

In future we intend to support the following devices:
* USB Hub
* Mass Storage Flash Drives

## Quickstart
To quickly get up and running with the xhci-stub-maax example for the
maaxboard, collect the files with

```
mkdir cp-manifest
cd cp-manifest
repo init -u git@github.com:sel4-cap/sel4cp-manifest.git
repo sync
```

To download and extract the compiler, run
```
curl -O compiler.xz
https://armkeil.blob.core.windows.net/developer/Files/downloads/gnu-a/10.2-2020.11/binrel/gcc-arm-10.2-2020.11-x86_64-aarch64-none-elf.tar.xz
tar -xvf compiler.xz
rm -r compiler.xz
```

This will extract the compiler which will need to be added to path
```
export PATH=<path-to-cp-manifest>/gcc-arm-10.2-2020.11-x86_64-aarch64-none-elf/bin:$PATH
```

Next, build the SDK by running `python build_sdk.py --sel4
<PATH-TO-CP-MANIFEST>/seL4`
