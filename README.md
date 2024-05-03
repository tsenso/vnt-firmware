# vnt-firmware
Repository that unites micropython plus esp-idf and display driver to be able to compile firmware for device


```sh
git submodule update --init --recursive
```

```bash
vnt-esp-idf/install.sh && source vnt-esp-idf/export.sh 
```

```bash
make -C vnt-micropython/mpy-cross
```

Then to build MicroPython for the ESP32 run:

```bash
cd vnt-micropython/ports/esp32
make submodules
make BOARD=M5STACK_FIRE USER_C_MODULES=../../../../vnt-ili9342c-mpy/src/micropython.cmake FROZEN_MANIFEST=../../../../../../vnt-ili9342c-mpy/manifest.py
```