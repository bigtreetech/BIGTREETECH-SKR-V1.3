# BIGTREETECH-SKR-V1.3
32bit board with LPC1768, support marlin2.0 and smoothieware, support lcd2004/12864, On-board TMC2130 SPI interface and TMC2208 UART interface no additional wiring is 

BIGTREETECH SKR V1.3 YouTube Video：[here](https://www.youtube.com/watch?v=oaXfXkPYHpw&t=8s)
 
# BIGTREETECH-SKR-V1.4
This [article](https://3dwork.io/en/complete-guide-skr-v1-4-and-tmc2209) explains how to configure all different TMC2209 dirvers from different procuders in SKR V1.4 & V1.4 Turbo

# Uploading firmware via SD card
The easiest way to upload firmware, is to put it at the top of the SD card named `firmware.bin`, insert it into the SKR board (not the TFT), and reset the board.

# Uploading firmware via USB
The installed [bootloader][bootloader] supports going into DFU mode by holding down the rotary dial on the LCD (connected via EXP1 pin [0.28](https://github.com/ardiehl/BTT_SKR_13_14_14T_SD-DFU-Bootloader/blob/3a1a2dfe5443b04ac4e2d5657fc145c9b48d662f/config.h#L55)) while the board is booting up. Then you can run `dfu-util -D <firmware.bin>` on the computer attached via USB.

# Changing the [bootloader][bootloader] (flashing via UART)
If you have a USB UART available (3.3V) you can hold the [ISP_BOOT pin][1.4SCH] low while booting (connected to [R28](https://github.com/bigtreetech/BIGTREETECH-SKR-V1.3/blob/master/BTT%20SKR%20V1.4/Hardware/BTT%20SKR%20V1.4-SCH.pdf), hold the P2.10 side down not the side connected to 3.3V). Then you can flash via UART, see [here](https://os.mbed.com/users/chris/notebook/prototype-to-hardware/) or [here](https://github.com/bigtreetech/BIGTREETECH-SKR-V1.3/issues/346#issuecomment-754120640).

# Changing the [bootloader][bootloader] (flashing via SWD)
You can attach any SWD capable debugger (such as an ST-Link) to the SWD pins (see [pinout top left][1.4PIN]). To use, I have had success with OpenOCD via `openocd -c "telnet_port 4444" -f interface/stlink.cfg -f board/mcb1700.cfg` (if you are not using an ST-link then you want to change the `-f interface/...` bit), and in another terminal window `telnet localhost 4444` to get the OpenOCD console, and in that OpenOCD console run `program build/DFU-Bootloader.bin exit`.

[bootloader]: https://github.com/ardiehl/BTT_SKR_13_14_14T_SD-DFU-Bootloader
[1.4SCH]: https://github.com/bigtreetech/BIGTREETECH-SKR-V1.3/blob/master/BTT%20SKR%20V1.4/Hardware/BTT%20SKR%20V1.4-SCH.pdf
[1.4PIN]: https://github.com/bigtreetech/BIGTREETECH-SKR-V1.3/blob/master/BTT%20SKR%20V1.4/Hardware/BTT%20SKR%20V1.4PIN.pdf
