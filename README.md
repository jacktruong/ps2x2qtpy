# ps2x2qtpy
Converts a USB signal from a PiKVM to a multiport PS/2 KVM using an [Adafruit QT Py RP2040](https://learn.adafruit.com/adafruit-qt-py-2040). Modified from [No0ne/ps2x2pico](https://github.com/No0ne/ps2x2pico).

|![image1](https://raw.githubusercontent.com/jacktruong/ps2x2qtpy/main/image1.jpg) |![image2](https://raw.githubusercontent.com/jacktruong/ps2x2qtpy/main/image2.jpg) |
|-|-|


# Usage
* Copy `ps2x2pico.uf2` to your Qt PY by pressing BOOTSEL before pluggging in.
* 3.3V/5V conversion is done using a bi-directional level shifter: https://www.amazon.ca/dp/B07DS4C5GK
* Connect the USB C port from the Qt PY to the PiKVM "data" out.
* The USB wires connect via the diagram below to the level shifter. The USB-A end connects to a PS/2 adapter.

```
                  _________________
                 |                 |
QtPY GPIO5 ______| LV1         HV1 |______ USB D+ (green) mouse**
QtPY GPIO6 ______| LV2         HV2 |______ USB D- (white) mouse**
QtPY GPIO4 ______| LV3         HV3 |______ USB D+ (green) keyboard
QtPY GPIO3 ______| LV4         HV4 |______ USB D- (white) keyboard
QtPY  3.3V ______| LV          HV  |______ USB VBUS (red) + QtPY 5V
QtPY   GND ______| GND         GND |______ USB GND (black)
           ______| LV5         HV5 |______ NC
           ______| LV6         HV6 |______ NC
           ______| LV7         HV7 |______ NC
           ______| LV8         HV8 |______ NC
                 |_________________|

**Have not successfully tested with a PS/2 mouse, YMMV.
```

# Build
make sure Pico SDK is on `develop` branch
```
export PICO_SDK_PATH=/path/to/pico-sdk
mkdir build
cd build
cmake ..
make
```

# Resources
* https://github.com/No0ne/ps2pico
* https://github.com/No0ne/ps2x2pico
* https://wiki.osdev.org/PS/2_Keyboard
* https://wiki.osdev.org/PS/2_Mouse
* https://wiki.osdev.org/Mouse_Input
* https://wiki.osdev.org/%228042%22_PS/2_Controller
* https://isdaman.com/alsos/hardware/mouse/ps2interface.htm