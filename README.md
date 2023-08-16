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
Additionally, run the setup.sh file to donwload and extract the compiler

