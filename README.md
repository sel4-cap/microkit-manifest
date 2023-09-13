# sel4cp-manifest

This repo contains the seL4 microkit with Capgemini-provided support for USB 3.0 (xHCI)

Specifically, we have provided support for these USB devices:
* Keyboard
* Optical Mouse
* Resistive Touch Screen (Capacitative untested but believed to also be supported)
* USB Hub

In future we intend to support the following devices:
* Mass Storage Flash Drives

## Quickstart
To quickly get up and running with the xhci-stub-maax example for the
maaxboard, collect the files with

```
mkdir mk-manifest
cd mk-manifest
repo init -u git@github.com:sel4-cap/microkit-manifest.git
repo sync
```

To download and extract the compiler, run
```
curl --output compiler.xz https://armkeil.blob.core.windows.net/developer/Files/downloads/gnu-a/10.2-2020.11/binrel/gcc-arm-10.2-2020.11-x86_64-aarch64-none-elf.tar.xz
tar -xvf compiler.xz
rm -r compiler.xz
```

This will extract the compiler which will need to be added to your path
```
export PATH=<path-to-mk-manifest>/gcc-arm-10.2-2020.11-x86_64-aarch64-none-elf/bin:$PATH
```

Next, build the SDK by runnim 
```
python build_sdk.py --sel4 <PATH-TO-mk-MANIFEST>/seL4
```

Once this is built, the xHCI driver can be built using the following command:
```
python dev_build.py --board=maaxboard --example=xhci_stub
```

This will create an image in `tmp_build/loader.img` that can be run.
