# Wireless Ferris Sweep

**TL;DR:** Repo for https://nickcoutsos.github.io/keymap-editor/

## Turning it on
To turn it on, switch the white switch on either side.

![power-switch](https://github.com/engelju/zmk-config-sweep/blob/main/pics/power-switch.png?raw=true)

## Resetting the halves

You can bridge the RST and GND pins on the nice!nano with tweezers or a wire — that simulates a reset press. Double-bridging (two quick taps) puts it into the UF2 bootloader, which is what you want for flashing.

![board](https://github.com/engelju/zmk-config-sweep/blob/main/pics/board.png?raw=true)

## Generating firmware with ZMK

See: https://zmk.dev/docs/user-setup?operating-system=mac

1. Install and Setup ZMK via `mise use uv@latest -g` and `uv tool install zmk`.
2. Setup the config repo via `zmk init`, mine was: https://github.com/engelju/zmk-config-sweep.
3. Add a keyboard: via `zmk keyboard add`, select **cradio** as your board/shield and **nice!nano v2** as your board.
4. Make an initial commit: `zmk cd && git add . && git commit -m "Initial commit" && git push`.
5. Every time you push a commit, GitHub Actions builds the firmware automatically. You download the resulting zip file from the Actions artifacts. It contains two .uf2 files: one for the left half, one for the right.

The repo will contain a config/ directory with your keymap (_cradio.keymap_ for the Sweep) and a build.yaml that defines which board/shield combos to build. 

You can either edit it with a text editor or connect the repo to https://nickcoutsos.github.io/keymap-editor.

## Flashing the firmware

1. Make sure the half is turned on.
2. Connect one half via USB.
3. Double-bridge RST+GND — the controller should mount as a USB drive (named something like NICENANO).
4. Drag and drop the correct .uf2 file (left or right) onto that drive. It'll unmount and reboot automatically.
5. Repeat for the other half.

# Battery Indicator

![battery](https://github.com/engelju/zmk-config-sweep/blob/main/pics/battery.png?raw=true)

# Links
- [Discord help thread with MechboardsUK](https://discord.com/channels/336826782772756481/1465751775196872705)
