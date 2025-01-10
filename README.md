This fix follows [themrrobert](https://github.com/themrrobert/neopets-flash-fix-windows-10)'s fix utilizing Safari instead of Pale Moon.  

### Tested on Windows 10
> 3Dvia does not seem to be compatible with Safari. Although Safari detected the plugin, it was never able to load the games.

**Make sure to uninstall any previous version of Flash or Shockwave currently installed on your mashine**
> you may need to run the uninstallers as admin.
1. [Flash Uninstaller](https://fpdownload.macromedia.com/get/flashplayer/current/support/uninstall_flash_player.exe)
2. [Shockwave Uninstaller](http://fpdownload.macromedia.com/get/shockwave/uninstall/win/sw_uninstaller.exe)

## Directions
1. Download and install  [Flash player](https://github.com/SpudMonkey7k/neopets-safari/raw/refs/heads/main/installers/install_flash_player.exe),  [Shockwave](https://github.com/SpudMonkey7k/neopets-safari/raw/refs/heads/main/installers/Shockwave_11_Installer_Full.msi), and [Fiddler Classic](https://www.telerik.com/download/fiddler) (No email confirmation to download, so you can use a fake one)

### Fiddler
> Instructions by themrrobert.

**Installation Instructions:**

1. Find fiddler script folder (usually Documents\Fiddler2\Scripts) and save [CustomRules.js](https://github.com/themrrobert/neopets-flash-fix-windows-10/blob/main/fiddler/CustomRules.js) to that directory. Alternatively, you can copy/paste the file contents into Fiddler->Rules->Customize rules (erase everything in there first), and hit Ctrl+S to save. You should hear a slight ding.
2. In Fiddler go to Tools -> Options -> HTTPS.
> **Enable:**
> - Capture HTTPS CONNECTs
> - Decrypt HTTPS Traffic
> - Ignore Server Certificate Errors.
> 3. Click Actions->Export Root Certificate to Desktop (This is to make Internet Explorer trust the localhost and not give you constant certificate errors)
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

### Safari 

1. Download and install [Safari for Windows](https://download.cnet.com/download/apple-safari/3000-2356_4-10697481.html). 
2. In Safari, click on the `Cog` and select `Show Menu Bar`. 
3. Click on `Help` in the Menu Bar then click on `Installed Plug-ins`.
> It should open a page showing that Flash and Shockwave are installed.
4. head to https://neopets.com/vsilogin.phtml (old login page) to login. 
> Note that you will need to disable your 2fa to login via Safari. 
9. Once logged in, head to https://neopets.com/games/classic.phtml to go to the game library. 
> Note that the pages of the website that use the new layout will not work properly, but any page that still uses the old layout will work.

**NeoPass**

> [!NOTE]
> **Since the new login page doesn't load right with Safari, IDK if using this workaround to login via NeoPass will work.**

In your default browser, *like chrome*:
1. Browse to neopets.
2. Open developer console (ctrl + shift + i).
3. Write `document.cookie.split(';').find(c => c.includes('neologin')).trim()` in console, hit enter and you will see something like neologin=youruserxxxxx (don't show anyone this value!!!). 
4. Then in Safari visit neopets.com
5. Open developer console (ctrl + alt + c) and write `document.cookie = "yyy"` where yyy is what you got from chrome (neologin=youruserxxxxx). 
6. Then refresh and you should be logged in.
> [!IMPORTANT]
> In Safari, you will need to open Preferences (ctrl + ,), go to the `Advanced` tab, and check `Show Develop menu in menu bar` to be able to open developer console.
