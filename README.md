# VNT firmware
Repository that unites micropython plus esp-idf and display driver to be able to compile firmware for device

## Building
Possible that you will need to get all git submodules when you checked out repo for the first time
```sh
git submodule update --init --recursive
```

### Build ESP32 build tools
```bash
vnt-esp-idf/install.sh && source vnt-esp-idf/export.sh 
```

### Build micropython tools for cross compilation
```bash
make -C vnt-micropython/mpy-cross
```

### Build MicroPython for the M5Stask Fire
```bash
cd vnt-micropython/ports/esp32
make submodules
make BOARD=M5STACK_FIRE USER_C_MODULES=../../../../vnt-ili9342c-mpy/src/micropython.cmake FROZEN_MANIFEST=../../../../../../vnt-ili9342c-mpy/manifest.py
```

## WSL low-speed hack
Mainly problem is described here: [WSL2 low exchange speed with mounted Windows folders](https://markentier.tech/posts/2020/10/faster-git-under-wsl2/#solution)

Solution (but it works not fully because inside cmake it is used full path to git executable):
```bash
source git-library.sh
```