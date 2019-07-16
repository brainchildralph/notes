
ADB 
=======

### udev rules
/etc/udev/rules.d/51-android.rules: 
```
SUBSYSTEM=="usb", ATTR{idVendor}=="04e8", MODE="0666", GROUP="plugdev", SYMLINK+="android%n"
```
|Vendor|ID|
|:----:|:-----:|
| Acer | 0502 |
| ASUS | 0b05 |
| Dell | 413c |
| Foxconn | 0489 |
| Fujitsu | 04c5 |
| Fujitsu Toshiba | 04c5 |
| Garmin-Asus | 091e |
| Google | 18d1 |
| Haier | 201E |
| Hisense | 109b |
| HP | 03f0 |
| HTC | 0bb4 |
| Intel | 8087 |
| K-Touch | 24e3 |
| KT Tech | 2116 |
| Kyocera | 0482 |
| Lenovo | 17ef |
| LG | 1004 |
| Motorola | 22b8 |
| MTK | 0e8d |
| NEC | 0409 |

### Connect deivice by TCP/IP
```
adb connect ${IP}:${Port}
```



