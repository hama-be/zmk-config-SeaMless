# SeaMless ZMK Config

SeaMless is a one-piece version of SeaGlass using a XIAO nRF52840 Plus.

This config follows the SeaGlass firmware setup for the PMW3610 trackball,
rotary encoders, mouse switches, RGB LED widget, battery history, charge
indicator, and ZMK Studio modules. The key matrix is changed to a
7-pin charlieplex scan with a dedicated interrupt pin.

## Build

Use the standalone Docker builder to build all entries in `build.yaml`:

```sh
/Users/hamasaki/Documents/work/zmk-docker-builder/build.sh .
```

The UF2 files are written to `firmware/`:

- `firmware/SeaMless.uf2`: normal firmware
- `firmware/settings-reset.uf2`: settings reset firmware

The first build downloads the container image and ZMK dependencies. Later builds
reuse a Docker volume for the ZMK checkout and compiler output, so they are much
faster. The host only receives the final files in `firmware/`.

To build one entry or list the available artifact names:

```sh
/Users/hamasaki/Documents/work/zmk-docker-builder/build.sh . SeaMless
/Users/hamasaki/Documents/work/zmk-docker-builder/build.sh . --list
```

### Build another ZMK config

Pass any ZMK config repository containing `build.yaml` and `config/west.yml` to
the same builder. Nothing needs to be copied into the firmware repository:

```sh
/Users/hamasaki/Documents/work/zmk-docker-builder/build.sh /path/to/zmk-config
```

GitHub Actions continues to use the same `build.yaml`, so local and CI artifact
names stay aligned.
