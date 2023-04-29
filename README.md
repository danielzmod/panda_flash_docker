# panda_flash_docker
Memory notes and modified dockerfile to get grey panda flashed

Prerequsites
 - Install docker
 - modify dockerfile in panda directory, adding usbutil (for lsusb) and a few other rows to build panda. 
 - build dockerfile
 - run the docker image in an interactive shell with full access to usb devices. 
   this command worked for me.
   sudo docker run -it --privileged -v /dev/bus/usb:/dev/bus/usb docker-image-name /bin/bash

1. Build usb cable that can short VBus to shield. 
2. Short usb shield before plugging in cable to computer. Then plug in to computer and release short after a few seconds. 
3. Now the panda should be in dfu mode. (lsusb should show something like 0483:df11 STMicroelectronics STM32  BOOTLOADER appearing as something like this)
4. modify constants.py, BASEDIR need to changed to BASEDIR = os.path.abspath("/tmp/panda") inside of panda library. Otherwise the file to flash won't be found.
5. cd into the folder board inside panda repository 
6. Run recover.py
7. Run ./flash.py

Hopefully should be flashed now.
