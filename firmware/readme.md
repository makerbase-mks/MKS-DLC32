## List of upload Firmware
There are several compiled firmwares that can be downloaded here:  
[For Laser, normal machine](https://github.com/makerbase-mks/MKS-DLC32/tree/main/firmware/Laser/Normal)  
[For Laser, CoreXY machine](https://github.com/makerbase-mks/MKS-DLC32/tree/main/firmware/Laser/CoreXY)  
[For CNC, normal machine](https://github.com/makerbase-mks/MKS-DLC32/tree/main/firmware/CNC/Normal)(For beta)  
[For CNC, CoreXY machine](https://github.com/makerbase-mks/MKS-DLC32/tree/main/firmware/CNC/CoreXY)(For beta)  
The firmware of MKS DLC32 has been burned with laser normal machine before leaving the factory. 

## Method of upload Firmware

1. On Windows PC, download the "Flash Download Tools" from https://www.espressif.com/en/support/download/other-tools 
2. Open the "Flash Download Tools", choose "Developer Mode"->ESP32 DowloadTool, and it will open the main menu.
3. Config the Flash Download Tools  
3.1 Choose the firmware(binary file listed above) and fill the address to be 0  
3.2 Config the  spiFlash  
SPI speed: 40MHz  
SPI MODE: DOUT  
Flash Size: 32Mbit  
3.3 Connect MKS DLC32 to PC using the USB line. Choose the COM of the DLC32, if you can’t find the COM, please check if the CH340 driver has been installed on the PC.  
3.4 Choose the baudrate which can be over 115200(The greater the baud rate, the faster the transmission speed, but the greater the chance of transmission errors).  
3.5 Press START and it will start to upload, just wait it to be finished.

![微信图片_20210908150315](https://user-images.githubusercontent.com/12979070/132936561-fb650a06-0da6-4c36-9eb2-2d9574f100eb.png)








