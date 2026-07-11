# SeaMless ZMK Config

SeaMless is a one-piece version of SeaGlass using a XIAO nRF52840 Plus.

This config follows the SeaGlass firmware setup for the PMW3610 trackball,
rotary encoders, mouse switches, RGB LED widget, battery history, charge
indicator, and ZMK Studio modules. The key matrix is changed to a
7-pin charlieplex scan with a dedicated interrupt pin.

## Build

Use GitHub Actions or build locally with the ZMK workflow:

```sh
west build -s zmk/app -b seeeduino_xiao_ble -- -DSHIELD="SeaMless rgbled_adapter" -DZMK_CONFIG="$PWD/config"
```
