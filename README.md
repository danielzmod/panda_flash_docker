# panda_flash_docker
Memory notes and modified dockerfile to get grey panda flashed.
Performed from Ubuntu 22.04.

# Prerequsites
 - Install docker
 - modify dockerfile in panda directory, adding usbutil (for lsusb) and a few other rows to build panda. 
 - build dockerfile
 - run the docker image in an interactive shell with full access to usb devices. 
   this command worked for me.
   ```sudo docker run -it --privileged -v /dev/bus/usb:/dev/bus/usb docker-image-name /bin/bash```

# Steps
 - Build usb cable that can short VBus to shield. 
 - Short usb shield before plugging in cable to computer. Then plug in to computer and release short after a few seconds. 
 - Now the panda should be in dfu mode. (lsusb should show something like 0483:df11 STMicroelectronics STM32  BOOTLOADER appearing as something like this)
 - modify constants.py, BASEDIR needs to be changed to ```BASEDIR = os.path.abspath("/tmp/panda")``` inside of panda library. Otherwise the file to flash won't be      found.
 - cd into the folder board inside panda repository 
 - Run ```./recover.py```
 - Run ```./flash.py```

Hopefully should be flashed now.
