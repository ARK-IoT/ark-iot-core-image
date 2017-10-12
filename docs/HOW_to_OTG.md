# Pi Zero OTG Setup   

Quick guide to setting up headless/OTG-mode Pi access via SSH. 

-----

### Items Needed
- Raspberry Pi
- micro-USB cable
- microSD-card
- Host Computer
  - Windows (with [Bonjour](https://support.apple.com/kb/DL999), iTunes or Quicktime installed) . 
  - Mac OS or Linux (with Avahi Daemon installed, for example Ubuntu has it built in).

-----

### Steps 
  
**1.** Flash Raspbian (full or Lite) [onto the SD card](https://www.raspberrypi.org/documentation/installation/installing-images/README.md).   
  - [**Etcher.io**](https://etcher.io) recommended.  

#

**2.** Once flashed, open up the 'boot' partition of the microSD-card, 
 -  Add the following to the bottom of the ```config.txt```:  
    ```dtoverlay=dwc2```     
 
#

**3.** Open up the file named ```cmdline.txt```.  
  - Directly after the word  ```rootwait```, add the following line:  
     ```modules-load=dwc2,g_ether```  

  - It should look something like this:  
    ```rootwait modules-load=dwc2,g_ether quiet splash``` 

  - At the time of this writing, an example can be found [pastebin.com/cmdline.txt](https://pastebin.com/WygSaptQ).

**4.** Create a new file called ```ssh``` 
  - You can create this using an empty .txt file, just make sure to remove the ```.txt``` part.    

#

**5.** Almost done!
  - Eject the SD card from your computer,  
      put it in your Raspberry Pi Zero,  
      then connect it via USB to your computer.  
  - It will take up to 90s to boot up (shorter on subsequent boots).  
  - It should then appear as a USB Ethernet device. 
  - You can typically SSH into it using--for instance--```raspberrypi.local``` as the address.  

-----

  adapted from: [**HowToOTGFast.md**](https://gist.github.com/gbaman/975e2db164b3ca2b51ae11e45e8fd40a#file-howtootgfast-md) | more: [**Programming Over USB!**](http://blog.gbaman.info/?p=791)    
