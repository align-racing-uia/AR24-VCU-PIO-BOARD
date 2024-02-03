# AR24-VCU-PIO-BOARD
A Platform IO board package, for the AR24 VCU

W.I.P.

## How to install:
1. Put the `ar24vcu.json` in your `.platformio/platforms/ststm32/boards/` folder.
2. Generate a project in Platform IO using the AR24 VCU board.
3. Copy the variants folder, and put into the platformio project base folder.
4. Add the following code to the platformio.ini file:
```
[env:ar24vcu]
platform = ststm32
board = ar24vcu
framework = arduino
board_build.variants_dir = variants
board_build.variant = AR24VCU
```
5. Try to build, and enjoy!

## Caveats, tips and tricks
A big caveat of the current hardware, is the lack of serial pins. The only pins currently broken out, is SWDIO/SWCLK, so a J-LINK, Black Magic Probe, or a STLINK is needed to program the chip.
As the current AR24 VCU dosent come with a USB port (or any form of serial pins whatsoever), we need some other way to be able to debug the program. One good way is to use a Arduino Library called `RTT Stream`. To read the output of this library, you will also need a program to view an RTT stream through a debugger. Some alternatives are:
1. A project named `probe-rs` that is able to upload and connect to a RTT stream.
2. A project named `strtt` which can be found here on github.


To use `probe-rs` the following tutorial tells you how to install it:
https://probe.rs/docs/getting-started/installation/

After this, you can put the following lines at the bottom of your `platformio.ini` file, to get logging straight into the console using `RTT Stream`.
```
upload_protocol = custom
upload_command = probe-rs run --chip STM32G473CETx $BUILD_DIR/${PROGNAME}.elf
lib_deps = koendv/RTT Stream@^1.4.1
```
