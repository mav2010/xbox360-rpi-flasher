# xbox360-rpi-flasher
XBox 360 NAND reader/writer for Raspberry Pi 4

go to main.c and comment out depending on what you want to do

- read NAND: dumps the NAND 3 times, check afterwards with cksum that they are identical! If yes, the connection is stable enough to attempt a write.

- write NAND: writes to NAND from the provided file and dumps the NAND again. Compare input and dump file with cksum to confirm that they are identical. If yes, then your flash was successful. When flashing less than 16MB (the full 0x400 blocks), make sure to adjust the blocks variable in nand_to_file() accordingly. E.g. if you flash glitch.ecc, set the blocks to 0x050. Otherwise the dump will be too large and obviously the checksums will not match. This only affects the read procedure, for write the program automatically sets the right size depending on the file size.

Wiring Instructions for Pi 4, following the color coding from the Weekendmodder (https://weekendmodder.com/picoflasher):
Blue: GPIO23
Green: GPIO24
Black: MOSI (GPIO 10)
Orange: MISO (GPIO 9)
Red: SCLK (GPIO 11)
Brown: GPIO 26
Yellow: Ground
