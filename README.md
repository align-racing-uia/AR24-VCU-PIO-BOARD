# AR24-VCU-PIO-BOARD
A Platform IO board package, for the AR24 VCU

W.I.P.

## How to use:
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

Can currently only upload using the STlink.