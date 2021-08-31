# Readme

## 下载文件列表

- boot_app0.bin
- bootloader_dout_80m.bin
- firmware.bin
- partitions.bin
- spiffs.bin

## 下载方法

使用flashload 3.8.5，选择以上的文件，通过串口进行刷写，每个文件有对应的下载地址配置：

| 文件                    | 地址     |
| ----------------------- | -------- |
| boot_app0.bin           | 0xe000   |
| bootloader_dout_80m.bin | 0x1000   |
| firmware.bin            | 0x10000  |
| partitions.bin          | 0x8000   |
| spiffs.bin              | 0x310000 |

也可以查看dowmload address.txt这个文件，里面也有下载地址的记录。

## 配置文件

dlc_cfg.txt是DLC32的配置文件，讲它放在SD卡的根目录下，重启DLC32，即可更新配置，更新配置后重启生效。

