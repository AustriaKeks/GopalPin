# GopalPin
Documenting my finds about the Medion GoPal anti-theft system(with next to no experience regarding the languages). My Device is a medion P4440

20/11/26:
When looking at ST.exe(smartouch?) in Binary Ninja, the Strings **STMgr::SmartTouch::Call( IOCTL_HAL_READ_SECRET (%d)** and **STMgr::SmartTouch::Call( IOCTL_HAL_WRITE_SECRET (%d)** can be found. This command reads/writes normally hidden data. In this case it´s a section called "secret". This isn´t in Windows CE by default and was instead added by the people behind this PNA, which leads me to belive that this is where either the regular Passcode, the Superpin, or even BOTH are stored. They´re very likely to be encrypted, but still a major find. The mentioned ST.exe will be provided above, hopefully somebody can find out more about what it does and wether it can be used for reading the passcode.
