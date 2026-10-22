

# crosses-42-zmk-template

### Original reference diagram
![Keymap](keymap-drawer/crosses.svg)

The diagram above is the original template. See [the current controls](docs/controls.md)
for the maintenance layout, thumb positions, and scroll controls.

### Trackball scroll

Hold Function (layer 3, left thumb Space) to scroll with the **right** trackball.
Hold Numpad (layer 4, right thumb Escape) to scroll with the **left** trackball.
Both use reversed vertical scrolling and a `1/16` scaler. Media does not enable
scrolling and keeps its left/right clicks and Alt keys.

### Maintenance

From Base, press **36 + 38** (left Space + Delete) or **39 + 41** (right Enter +
Escape) within 50 ms, then hold the pair for 500 ms. Keep holding while pressing
a maintenance command; releasing either thumb exits. The mirrored maintenance
layer contains Bluetooth profiles, pairing clear, output selection, Studio
unlock, reset, and bootloader. Those commands are removed from Media.

### Build dependencies

Board support and the pipeline-switch module are vendored under `modules/`
and registered by `zephyr/module.yml` and `build.yaml`. West still fetches
ZMK and the other public modules listed in `config/west.yml`; this is not an
offline build.

Push to run **Build ZMK firmware** in GitHub Actions. Verify the left, right,
and settings-reset builds succeed. Flash the regular firmware artifacts to
their matching halves, then follow the [hardware checks](docs/controls.md#hardware-checks).
Sensitivity, direction, and combo timing still need to be checked on hardware.
