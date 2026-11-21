# GopalPin
Documenting my finds about the Medion GoPal anti-theft system(with next to no experience regarding the languages). My Device is a medion P4440

20/11/26:
When looking at ST.exe(smartouch?) in Binary Ninja, the Strings `STMgr::SmartTouch::Call( IOCTL_HAL_READ_SECRET (%d)` and `STMgr::SmartTouch::Call( IOCTL_HAL_WRITE_SECRET (%d)` can be found. This command reads/writes normally hidden data. In this case it´s a section called "secret". This isn´t in Windows CE by default and was instead added by the people behind this PNA, which leads me to belive that this is where either the regular Passcode, the Superpin, or even BOTH are stored. They´re very likely to be encrypted, but still a major find. The mentioned ST.exe will be provided above, hopefully somebody can find out more about what it does and wether it can be used for reading the passcode.

21/11/26:
Just dumped as much of the windows CE image as possible, unfortunately the dlls didn´t want to export. The oem.res file has some more strings related to IOCTL and such. Another big discovery, changing HKLM/Drivers/Builtin/BusIoctl to another value seems to change the devices behavior. Changing it to 0 shows the password screen, albeit not working whatsoever. When the device is booted into the Pin mode, no other drives mount except the ROM. However, you can still add executables to the desktop and startup directories in the windows directory before rebooting into this state. The program which shows the pin windows is called "PinLock" (PL.exe)
