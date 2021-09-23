# MKS-DLC32
MKS DLC32 motherboard kit, which is an offline engraving master control kit developed for desktop engraving machines. The hardware is equipped with a 32-bit high-speed ESP32 module, integrated WIFI function, and directly drives a 3.5-inch touch color screen; it can realize fast engraving and WEB web pages. Control, mobile phone APP control and other functions.  
The mounting holes and board size of MKS DLC32 are compatible with MKS DLC, and the it can also be used with the [LaserGRBL](https://lasergrbl.com) and [LightBurn](https://lightburnsoftware.com) PC software.  
![main](https://user-images.githubusercontent.com/12979070/131437599-2b7aae8f-1569-4e38-b713-bb6b87596be5.png)   
## Related tutorials and Notice
Product introduce video: https://www.youtube.com/watch?v=U_OzlMxwms8&t=6s  
Basic usage for laser engraving machine: https://www.youtube.com/watch?v=MKRBYVbxJmw&t=139s  

# Purchase link
Aliexpress: https://www.aliexpress.com/item/1005003183498253.html?spm=a2g0o.store_pc_home.productList_8356958.pic_0

# HARDWARE
![interface](https://user-images.githubusercontent.com/12979070/131437579-cddae779-2c0f-478e-899e-be1a01e1c4c5.png)
# Compare between MKS DLC and MKS DLC32
| ITEMS      |  MKS DLC  | MKS DLC32 |
|------------|--------------------|--------------------|
| MCU        | ATMEGA328P ( 8bits) | ESP32-WROOM-32U（ 32bits） |
| MCU Freq.	| 20MHz	| 240MHz |
| FLASH	| 32KBytes	| 8192KBytes |
| RAM	| 32KBytes	| 520KBytes |
| Power Input | DC 12v/24v |	 DC12v/24v  |
| Laser Speed	 | <=3000mm/min	| <=8000mm/min |
| PC engraving | Support |	Support |
| Offline Mode |	Not Support |	Support |
| LCD	 | Not Support |	Support，3.5 inch Touch TFT |
| WiFi On Board	| Not Support	| Support |
| Web Control	| Not Support	| Support |
| Mobile APP Control	| Not Support	| Support |
| LaserGRBL	| Support |	Support |
| LightBurn	| Support |	Support |

# FIRMWARE
There are several compiled firmwares that can be downloaded here:  
[For Laser, normal machine](https://github.com/makerbase-mks/MKS-DLC32/tree/main/firmware/Laser/Normal)  
[For Laser, CoreXY machine](https://github.com/makerbase-mks/MKS-DLC32/tree/main/firmware/Laser/CoreXY)  
[For CNC, normal machine](https://github.com/makerbase-mks/MKS-DLC32/tree/main/firmware/CNC/Normal)(For beta)  
[For CNC, CoreXY machine](https://github.com/makerbase-mks/MKS-DLC32/tree/main/firmware/CNC/CoreXY)(For beta)  
The firmware of MKS DLC32 has been burned with laser normal machine before leaving the factory. If you need to update the firmware, you can follow the update instructions [here](https://github.com/makerbase-mks/MKS-DLC32/tree/main/firmware#method-of-upload-firmware).

# Mobile App
We have developed MKSLaser, the App for mobile phone, which can connect to MKS DLC32, control movement, edit image, upload files and so on. Now the Android verison has been uploaded to [Google Play](https://play.google.com/store/apps/details?id=makerbase.com.mkslaser). And the one for IOS is still under development.
![H20730396e9f9417b8b05651f1d692a73x](https://user-images.githubusercontent.com/12979070/134457521-72c39e06-5292-453d-881e-71d8285324ee.jpg)


# CONFIGRATION 
When you want to use MKS DLC32 to install to a new machine, you generally need to configure parameters to fit your engraving machine. There are two ways to configure parameters, one is to configure through the configration file, and the other is to configure through the PC software.

## Configure through configuration files
1. Download the configuration file "dlc_cfg.txt" from MKS GITHUB: https://github.com/makerbase-mks/MKS-DLC32/tree/main/firmware
2. Modify the corresponding configuration items according to your engraving machine needs. For specific parameters configrations you can refer to [Parameters configuration](https://github.com/makerbase-mks/MKS-DLC32/blob/main/README.md#parameters-configuration)
3. Save "dlc_cfg.txt" and copy to TF card.
4. Insert the TF card to DLC32 motherboard, restart it, and it will be automatically configured.

## Configure through PC software
1. Use a USB cable to connect the DLC32 to the PC
2. Open the LaserGRBL software or LightBurn or other serial tools on the PC (the default baud rate is 115200)
3. Modify the configuration items. For specific configuration commands, please refer to [Parameters configuration](https://github.com/makerbase-mks/MKS-DLC32/blob/main/README.md#parameters-configuration)


## Parameters configuration 
You can use PC software such as GRBLaser to config the parameters by sending commands, here is the list:

| COMMANDS      |  PARAMETERS  | DESCRIPTION |
|------------|--------------------|--------------------|
| $0 | 	10	 | Sets time length per step. Minimum 3usec. |
| $1 | 	5 | 	Sets a short hold delay when stopping to let dynamics settle before disabling steppers. Value 255 keeps motors enabled with no delay. |
| $2	 | 0	 | Inverts the step signal. Set axis bit to invert (00000ZYX). The details can refer to [XYZ-TABLE](https://github.com/makerbase-mks/MKS-DLC32#xyz-table)|
| $3 | 	1	 | Inverts the direction signal. Set axis bit to invert (00000ZYX). The details can refer to [XYZ-TABLE](https://github.com/makerbase-mks/MKS-DLC32#xyz-table)|
| $4 | 	0	 | Inverts the stepper driver enable pin signal. |
| $5 | 	1	 | Inverts the all of the limit input pins. |
| $6 | 	0	 | Inverts the probe input pin signal. |
| $10	 | 1 | 	Alters data included in status reports. |
| $11	 | 0.01 | 	Sets how fast Grbl travels through consecutive motions. Lower value slows it down. |
| $12 | 	0.002	 | Sets the G2 and G3 arc tracing accuracy based on radial error. Beware: A very small value may effect performance. |
| $13	 | 0	 | Enables inch units when returning any position and rate value that is not a settings value. |
| $20	 | 0 | 	Enables soft limits checks within machine travel and sets alarm when exceeded. Requires homing. |
| $21 | 	0 | 	Enables hard limits. Immediately halts motion and throws an alarm when switch is triggered. |
| $22 | 0	 | Enables homing cycle. Requires limit switches on all axes. |
| $23	 | 0	 | Homing searches for a switch in the positive direction. Set axis bit (00000ZYX) to search in negative direction. The details can refer to [XYZ-TABLE](https://github.com/makerbase-mks/MKS-DLC32#xyz-table)|
| $24	 | 300	 | Feed rate to slowly engage limit switch to determine its location accurately. |
| $25	 | 1000	 | Seek rate to quickly find the limit switch before the slower locating phase. |
| $26	 | 250 | 	Sets a short delay between phases of homing cycle to let a switch debounce. |
| $27 | 	1	 | Retract distance after triggering switch to disengage it. Homing will fail if switch isn't cleared. |
| $30	 | 1000	 | Maximum spindle speed. Sets PWM to 100% duty cycle. |
| $31	 | 0	 | Minimum spindle speed. Sets PWM to 0.4% or lowest duty cycle. |
| $32	 | 1	 | Enables laser mode. Consecutive G1/2/3 commands will not halt when spindle speed is changed. |
| $100	 | 80	 | X-axis travel resolution in steps per millimeter. |
| $101	 | 80	 | Y-axis travel resolution in steps per millimeter. |
| $102	 | 80	 | Z-axis travel resolution in steps per millimeter. |
| $110	 | 6000 | 	X-axis maximum rate. Used as G0 rapid rate. |
| $111	 | 6000	 | Y-axis maximum rate. Used as G0 rapid rate. |
| $112	 | 6000	 | Z-axis maximum rate. Used as G0 rapid rate. |
| $120	 | 500	 | X-axis acceleration. Used for motion planning to not exceed motor torque and lose steps. |
| $121 | 	500	 | Y-axis acceleration. Used for motion planning to not exceed motor torque and lose steps. |
| $122	 | 500	 | Z-axis acceleration. Used for motion planning to not exceed motor torque and lose steps. |
| $130	 | 285	 | Maximum X-axis travel distance from homing switch. Determines valid machine space for soft-limits and homing search distances. |
| $131	 | 272 | 	Maximum Y-axis travel distance from homing switch. Determines valid machine space for soft-limits and homing search distances. |
| $132	 | 80	 | Maximum Z-axis travel distance from homing switch. Determines valid machine space for soft-limits and homing search distances. |

### XYZ TABLE
For the commands of $2/$3/$23, the detailed parameters can be refer to:
| Directions | Parameters |
|----------|--------------|
| X+  Y+  Z+ |	0 |
| X-  Y+  Z+ |	1 |
| X+  Y-  Z+ |	2 |
| X-  Y-  Z+ |	3 |
| X+  Y+  Z- |	4 |
| X-  Y+  Z- |	5 |
| X+  Y-  Z- |	6 |
| X-  Y-  Z- |	7 |

## Note
- Thank you for using MKS products. If you have any questions during use, please contact us in time and we will work with you to solve it.
- For more product dynamic information and tutorial materials, you can always follow MKS's Facebook and GitHub and YouTube. Thank you!
![](https://github.com/makerbase-mks/MKS-Robin-Nano/blob/master/hardware/Image/MKS_FGA.png)
