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
1. A project named `strtt` whcih can be found here on github.
2. A project named `probe-rs` that is also able to connect to a RTT stream.

## TODO:
Add either STRTT or probe-rs debugging as a default command when clicking `Upload and monitor`