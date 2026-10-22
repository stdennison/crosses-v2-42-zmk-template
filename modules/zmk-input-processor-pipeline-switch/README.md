# Vendored pipeline-switch module

The C sources, Kconfig, and CMakeLists.txt were already tracked in this
repository at `3001be0`. The upstream project is
https://github.com/Good-Great-Grand-Wonderful/zmk-input-processor-pipeline-switch.

The header filename now matches the sources' `zip_pipeline_switch.h` include.
Devicetree bindings have been added for the properties consumed by those
sources. Module metadata is at the standard `zephyr/module.yml` location.

Each entry in `build.yaml` passes the template root and this directory as
`ZMK_EXTRA_MODULES`. This module's own metadata registers its CMake, Kconfig,
and devicetree roots. There is no West project entry for this directory, so
West does not fetch a second copy.
