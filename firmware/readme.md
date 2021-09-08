
## Method of upload Firmware

1. On Windows PC, download the "Flash Download Tools" from https://www.espressif.com/en/support/download/other-tools 
2. Open the "Flash Download Tools", choose "Developer Mode"->ESP32 DowloadTool, and it will open the main menu.
3. Config the Flash Download Tools
   3.1 Choose the files listed above and fill the correct address

| File                    | Address     |
| ----------------------- | -------- |
| boot_app0.bin           | 0xe000   |
| bootloader_dout_80m.bin | 0x1000   |
| firmware.bin            | 0x10000  |
| partitions.bin          | 0x8000   |
| spiffs.bin              | 0x310000 |

3.2 Config the  spiFlash  
SPI speed: 40MHz  
SPI MODE: DOUT  
Flash Size: 32Mbit  

3.3 Connect MKS DLC32 to PC using the USB line. Choose the COM of the DLC32, if you can’t find the COM, please check if the CH340 driver has been installed on the PC.

3.4 Choose the baudrate which can be over 115200(The greater the baud rate, the faster the transmission speed, but the greater the chance of transmission errors).



3.5 Press START and it will start to upload, just wait it to be finished.

![微信图片_20210908150315](https://user-images.githubusercontent.com/12979070/132467459-1a5ec6e0-db1d-4bc1-9dd9-b70929ad2f48.png)







