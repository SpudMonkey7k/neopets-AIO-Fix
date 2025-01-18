> A guide to handicapping your CPU to slow down games that run too fast on neopets.

## Windows 10/11 

- Open `This PC`
- Right click and select `Properties`
- Click on `Advanced System Options`/`Advanced System Settings` 
- Move to the `Advanced` tab 
- Click on `Environment Variables` 
- In the bottom window, select `NUMBERS_OF_PROCESSORS` and click `Edit` 
- In the `Variable Value` field, change the number of active cores to `1` 
  - *remember to return this number back to original number once done.*
- Click `OK` then `OK` then `APPLY` then `OK`

>[!NOTE]
>This can also be done through your bios/uefi, but if done wrong it could brick your computer.


## Mac OS

>[!NOTE]
>This requires Mac OS 14.5 or higher, unless you already have xcode developer tools installed.
>Different versions of xcode have the cpu tool in different places, so if this guide doesn't work for you, search through the xcode developer tools for the cpu preferences.

- Open the `App Store`
- Search for `xcode` and install
- Open `xcode`
- Open `developer tools`
- Click on `instruments` menu
- Select `instruments/preferences`
- Select `cpu`
- Edit your cpu settings and restart
  - *remember to return these settings to normal once done.*

>[!IMPORTANT]
>For older versions of xcode, you might be able to launch cpu settings by opening the xcode folder and going to `Developer/Extras/PreferencePanes/` folder and launching `processor.prefpane`

