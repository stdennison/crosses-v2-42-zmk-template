# Vendored Crosses v2 board support

Board sources and LICENSE copied from the adjacent local checkout of
https://github.com/Good-Great-Grand-Wonderful/crosses-v2-zmk-firmware at
`a4279793633de831c849e065663d01c05f1c89cd`. Trailing whitespace has been removed.

The template's `zephyr/module.yml` registers this directory as its board root.
This directory contains board support, not ZMK itself. ZMK and the other
public dependencies are listed explicitly in `config/west.yml` at the template
root. The settings-reset shield comes from ZMK; no local placeholder is needed.
