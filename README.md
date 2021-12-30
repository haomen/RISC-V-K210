# RISC-V-K210


### Linux

RISC-V linux image was built from busybox, following instructions from [vowstar/k210-linux-nommu](https://github.com/vowstar/k210-linux-nommu).

To transfer image onto K210 devboard.
```
sudo usermod -a -G uucp $(whoami)
sudo usermod -a -G dialout $(whoami)
sudo python3 -m pip install kflash
su $(whoami)

kflash -B dan -b 3000000 -p /dev/ttyUSB0 linux-image/loader.bin
python3 -m serial.tools.miniterm --raw --filter colorize /dev/ttyUSB0 115200
```