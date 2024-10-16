This fix follows [themrrobert](https://github.com/themrrobert/neopets-flash-fix-windows-10)'s fix utilizing Waterfox Classic and Internet Explorer instead of Pale Moon.  

[![Flash Fix Video](https://github.com/SpudMonkey7k/neopets-flash-shockwave-3dvia-fix/blob/main/assets/flash-fix.mp4_20241015_205621.645.jpg)]([https://www.youtube.com/watch?v=ek1j272iAmc](https://cdn.discordapp.com/attachments/355950554301595649/1293042111968575499/flash-fix.mp4?ex=67107acf&is=670f294f&hm=cd660784fc589022312d40c59c5e163abd8b8352acc3f0516c5110ed71e2b6c7&))

### Tested on Windows 8.1 and 10; was unable to get Flash working on win11.
> This guide will use Waterfox Classic for Flash and IE for Shockwave and 3Dvia though will also include how to install flash for IE as well. 

**Make sure to uninstall any previous version of Flash or Shockwave currently installed on your mashine**
> you may need to run the uninstallers as admin.
1. [Flash Uninstaller](https://fpdownload.macromedia.com/get/flashplayer/current/support/uninstall_flash_player.exe)
2. [Shockwave Uninstaller](http://fpdownload.macromedia.com/get/shockwave/uninstall/win/sw_uninstaller.exe)


## Programs Needed Directions
1. Download and install  [IE Flash player](https://github.com/SpudMonkey7k/neopets-AIO-Fix/raw/main/Installers/flashplayer32_0r0_371_winax.exe), [Waterfox Flash](https://github.com/SpudMonkey7k/neopets-AIO-Fix/raw/main/Installers/flashplayer32_0r0_371_win.msi),  [Shockwave](https://github.com/SpudMonkey7k/neopets-AIO-Fix/raw/main/Installers/Shockwave_Installer_Full.msi), [3dvia](http://3dlifeplayer.dl.3dvia.com/player/install/installer.exe), [Waterfox Classic](https://github.com/WaterfoxCo/Waterfox-Classic/releases/download/2022.11-classic/WaterfoxClassic2022.11.exe), and [Fiddler Classic](https://www.telerik.com/download/fiddler) (No email confirmation to download, so you can use a fake one)
  > Note: If you get an error installing Flash saying something along the lines of Internet Explorer already having Flash built in, rerun the installer in Windows 7 compatibility mode and as Administrator. 
  > If it still gives the error, then download and install [this version of flash player](https://static.centbrowser.com/FlashPlayerStandalone/ppapi_32.0.0.363.exe).
2. With browser closed, add `ProtectedMode=0` to `mms.cfg` file then restart browser. 
> - C:\windows\SysWOW64\Macromed\Flash\mms.cfg for 64-bit system.
> - C:\windows\System32\Macromed\Flash\mms.cfg for 32-bit system.

### Fiddler
> Instructions by themrrobert.

**Installation Instructions:**

1. Find fiddler script folder (usually Documents\Fiddler2\Scripts) and save [CustomRules.js](https://github.com/themrrobert/neopets-flash-fix-windows-10/blob/main/fiddler/CustomRules.js) to that directory. Alternatively, you can copy/paste the file contents into Fiddler->Rules->Customize rules (erase everything in there first), and hit Ctrl+S to save. You should hear a slight ding.
2. In Fiddler go to Tools -> Options -> HTTPS.
> **Enable:**
> - Capture HTTPS CONNECTs
> - Decrypt HTTPS Traffic
> - Ignore Server Certificate Errors.
> 3. Click Actions->Export Root Certificate to Desktop (This is to make Waterfox Classic and Internet Explorer trust the localhost and not give you constant certificate errors)
> 4. Click Actions->Trust Root Certificate. This will make other browsers (like Chrome), and Windows apps such as Discord, also trust the proxy (Fiddler). *This isn't strictly necessary, but if it's not done, you won't be able to use Chrome/Discord/Etc while Fiddler is running and intercepting traffic.*
5. **Important:** Add exclusions to your proxy: In Fiddler, go to Tools->Options->Connections, and add the following into the "Bypass URLs that begin with..." field:
> <-loopback>;discord.com; discordapp.com; netflix.com; *.discord.com; *.discordapp.com; *.netflix.com; *.discordapp.net; discordapp.net; *.google.com; google.com; *.gmail.com; gmail.com; *.youtube.com; *.gstatic.com; *.cloudflare.com; *.googleapis.com; *.jquery.com; *.googlevideo.com; support.neopets.com
6. Download the [neopets folder in this project](https://download-directory.github.io/?url=https://github.com/themrrobert/neopets-flash-fix-windows-10/tree/main/neopets)
7. Find fiddler installation path (usually C:\Users\YOUR_USERNAME\AppData\Local\Programs\Fiddler or C:\Program Files\Fiddler), create a folder named "neopets" and extract the downloaded neopets.zip files into it. The extracted files should end up looking like C:\Users\YOUR_USERNAME\AppData\Local\Programs\Fiddler\neopets\games\...
8. Close Fiddler.
9. Start Fiddler whenever you want to play Neopets games :)

> **Notes:**  
> #5. You can remove this certificate later via Windows Certificate Manager (certmgr.msc->Trusted Root Certification Authorities->Certificates). The name of the certificate is DO_NOT_TRUST so that you're well aware it's a local certificate, and not from a trusted Certificate Authority (CA). It is safe to trust this certificate, BUT the implications are that you will not see any genuine certificate errors from websites, so you should keep Fiddler closed when you're not using it, and you should remove the certificate if you stop playing Neopets games.
>
> Fiddler seems to need "Capture Traffic" enabled in order to work consistently (feel free to experiment). This means it logs every packet that is proxied throuogh it. So while you can watch Youtube on Chrome while running Fiddler, you should clear out the history/restart Fiddler once in a while, otherwise it will start using up all your memory holding a copy of every video packet!

### Waterfox Classic
1. In Menu, click on `Options`.
2. Click on `Advanced`.
3. Click on `Certificates`.
4. Click on `View Certificates`.
5. Click `Import` and select the certificate created by Fiddler.
> Locate the exported certificate on your desktop. It is named "FiddlerRoot.cer"

**Waterfox Classic Plugins** 
1. In Menu, click on `Add-ons`.
2. Click on `Plugins`. 
> Should find `Shockwave Flash` listed (Flash Player). 

You are now ready to play Flash games on Waterfox Classic!
> Waterfox does not support Shockwave player or 3Dvia.

### Internet Explorer 
> Windows 8.1 and lower can skip to `Initial IE Setup` section. 

**Opening IE** (Windows 10 and up)
> Here's how to launch IE without it redirecting you to Edge.

1. At `C:\Program Files (x86)\Microsoft\Edge\Application\` there's a folder with a bunch of numbers, when you enter that folder there's another folder called `BHO`, rename it to `BHO.bak` and it will stop redirecting you. 
> Note that with every update to Edge you will have to repeat step 1.
2. On your desktop, create a `.vbs` file with the following code in it: 
```vbs
Set ie = CreateObject("InternetExplorer.Application")
ie.Navigate "about:blank"
ie.Visible = 1
```
3. Clicking on the created file will launch IE. 

**Initial IE Setup**
1. In the Menu, click on `Internet Options` and select `Content` tab. 
2. Click on `Certificates` and then Import the certificate created by Fiddler. 
> Locate the exported certificate on your desktop. It is named "FiddlerRoot.cer"
3. Click on `Security` tab. 
4. Uncheck `Enable Protected Mode`. 
> If `Enable Protected Mode` is missing, click on `Trusted Sites` and add neopets to the list like the image below then set security level to low.
> 
> ![IE Trusted settings](https://github.com/SpudMonkey7k/neopets-IE/blob/main/assets/trusted.png)
5. Close out of the `Internet Options` window. 
6. In the Menu, click on `Compatibility View Settings` and add `neopets.com`. 
7. Close out of the `Compatibility View Settings` window. 
8. head to https://neopets.com/vsilogin.phtml (old login page) to login. 
> Note that you will need to disable your 2fa to login via IE. 
9. Once logged in, head to https://neopets.com/games/classic.phtml to go to the game library. 
> Note that the pages of the website that use the new layout will not work properly, but any page that still uses the old layout will work.
> >  If IE freezes trying to load Neopets, please remove neopets from Compatibility Settings! 

**NeoPass**

IE does not natively work with neopass login! You will need to use the following workaround to login via NeoPass. 
If your default browser, like chrome:
1. Open developer console (ctrl + shift + i).
2. Write `document.cookie.split(';').find(c => c.includes('neologin')).trim()` in console, hit enter and you will see something like neologin=youruserxxxxx (don't show anyone this value!!!). 
3. Then in IE visit neopets.com
4. Open developer console (f12) and write `document.cookie = "yyy"` where yyy is what you got from chrome (neologin=youruserxxxxx). 
5. Then refresh and you should be logged in.

**Flash error**
![Flash error](https://github.com/SpudMonkey7k/neopets-IE/blob/main/assets/flash-error.png)

IE will initially hang loading the Flash games, simply wait a couple of seconds then click on the white square where the game should be. 
A message similar to the one above will popup. Simply clicking `Stop script` should start loading the game for you. 

> Make sure that Waterfox Classic and IE are certificated and that Fiddler is running when trying to play on Neopets.

