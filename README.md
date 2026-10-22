

# crosses-42-zmk-template

### Default Firmware Keymap
![Keymap](keymap-drawer/crosses.svg)

### Trackball scroll

Hold Function (layer 3, left thumb Space) to scroll with the left trackball.
Vertical scrolling is reversed relative to commit `11915311`, and the `1/16`
scroll scaler produces half that commit's scroll output. Horizontal scroll
direction and ordinary cursor movement retain their previous configuration.

### Build dependencies

Board support and the pipeline-switch module are vendored under `modules/`
and registered by `zephyr/module.yml` and `build.yaml`. West still fetches
ZMK and the other
public modules listed in `config/west.yml`; this is not an offline build.

Push to run **Build ZMK firmware** in GitHub Actions. Verify the left, right,
and settings-reset builds succeed. Flash the regular firmware artifacts to
their matching halves, then check normal cursor movement and Function-layer
scrolling. Sensitivity and direction still need to be checked on hardware.
