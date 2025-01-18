# UI Development Requirements

## Required tools

The tools required for UI development in Skyrim are as follows :

- `Adobe Flash Professional CS4/CS6`.
    - `Adobe Flash Professional CS6` is the recommended one and the one this guide is written for.

- `Unreal Development Kit 2015`.
    - It contains the necessary `GFX Extensions`, `CLIK` files and everything else needed to test your UIs using `Adobe Flash Professional CS6`.

- `JPEXS Free Flash Decompiler`.
    - Used for decompiling the vanilla `.swf` files ( *more on those later* ).

- A tool of your choice to design UI elements, some `FREE` examples below :
    - `FREE` [Figma](https://www.figma.com)
    - `FREE` [Gimp](https://www.gimp.org/downloads)
    - `FREE` [Paint.NET](https://www.getpaint.net)

- `BSA Archive Extractor`.
    - Used to extract vanilla game's UI components, you can do it for existing UI mods as well if you're allowed to do so.

Download links can be found [here](#download-links).

## Setting up the enviroment

1. Install `Adobe Flash Professional CS6`.
	- You will find a crack inside of the archive as well with an `Instructions.txt` file.
	- Download links for the tools can be found at the end of this documentation.

2. Install `Unreal Development Kit 2015`.
	- There's no setup file here, content provided already unpacked, as-is, just extract the content in the location of your choice.
	- For example `C:/Tools/Unreal Development Kit 2015`.

3. Configure `Adobe Flash Professional CS6`.
	- Run `Adobe Flash Professional CS6`.
	- In `Adobe Flash Professional CS6`, go to the following path : `Help > Manage Extensions` ( screen of the popup window below ).

		![Extension Menu](/docs/resources/media/extension_menu.png)

	- Click `Install`, then browse to your `Unreal Development Kit 2015` install location.
		- If you have been following this tutorial, that would be : `C:/Tools/Unreal Development Kit 2015`.
  	- Find `Scaleform Extensions.mxp` located in `UDK 2015-01/Binaries/GFx/CLIK Tools`.
  	- Click on the file to install `Scaleform Extensions`.
		- `Adobe Flash Professional CS6` will inform you that it needs to restart for changes to apply, do that.
	- In `Adobe Flash Professional CS6` go to the following settings : `Edit > Preferences > ActionScript` and click on `ActionScript 2.0 Parameters` button here :

   		![Actionscript Settings](/docs/resources/media/actionscript_settings.png)
   
	- A new window should open, you'd want to input the paths for the UDK Flash files for `ActionScript 2.0` by hitting the `+` sign like so :

		![Actionscript Classes](/docs/resources/media/actionscript_classes.png)

   		1. Click the `+` sign to add a new source folder.
		2. Browse the following path, assuming you have followed the tutorial : `C:/Tools/Unreal Development Kit 2015/UDK 2015-01/Development/Flash/AS2/CLIK`.
			- Depending on how you extracted the file, the `UDK 2015-01` folder might be inside another folder, adjust accordingly.
    	1. Move the location you just added to the top ( before the project's root folder which is marked with a single dot ) to match the following order :
          	1. `C:/Tools/Unreal Development Kit 2015/UDK 2015-01/Development/Flash/AS2/CLIK`
          	2. `.`
          	3. `${LocalData}/Classes`
		2. Press `Ok`, the window should automatically close.
	- Go to the following path : `Window > Other Panels` and click on `Scaleform Launcher`.
		- A new window should open, which you can then drag into `Adobe Flash Professional CS6`'s right panel for easier access, like so :

		https://github.com/MissCorruption/Yggdrasil-UI/assets/125442561/c396ec2f-7627-4c05-8905-1a9db71147fe

  	- In `Scaleform Launcher` section on the right panel, click on the `+` sign, it will open a small window with `3 Fields`.
  	- In the first field, click on the `+` sign and go to your `Unreal Development Kit 2015` installation, then go to the following path : `UDK 2015-01/Binaries/GFx`.
		- Select `GFxMediaPlayerD3d9.exe`, it will ask you to choose a name for the player, I suggest typing `GFxMediaPlayer`.
  	- In the second field, enter a profile name for your player profile, you can type whatever you want.
	- Leave the third field untouched.
	- It should look something like this :

		![Scaleform Launcher profile](/docs/resources/media/scaleform_launcher_profile.png)

   	- If everything is as it should, click `Ok`.
	- You can now test your UI behaviors by starting the `Scaleform Launcher` from the right panel and select `Test with : GFxMediaPlayer` :
 
 		![Scaleform Launcher Test](/docs/resources/media/scaleform_launcher_test.png)
   
	- This may have some limitations, you'll have to test around yourself until I can provide more information.

## Download Links

<u>Libraries & Tools :</u>

- [Adobe Flash Professional CS6](https://www.mediafire.com/file/fiylko26035lrxb/Adobe_Flash_Professional_CS6_%2528_Version_12.0.0.481_%2529.rar/file) <s>( Have a look at my [Yggdrasil UI](https://www.nexusmods.com/skyrimspecialedition/mods/108880?tab=files) mod page for the tool )</s>
- [BSA Archive Extractor](https://www.nexusmods.com/skyrimspecialedition/mods/974?tab=files&file_id=5396)
- [Figma ( Windows )](https://www.figma.com/download/desktop/win) ( You can stick to the online tool though, not forced to download the app )
- [Figma ( MacOS )](https://www.figma.com/download/desktop/mac) ( You can stick to the online tool though, not forced to download the app )
- [Gimp](https://www.gimp.org/downloads)
- [Green Sock](https://github.com/greensock/GreenSock-AS2) ( `ActionScript 2 Library` for `Animations` and other filters )
- [JPEXS Free Flash Decompiler ( Windows )](https://github.com/jindrapetrik/jpexs-decompiler/releases/download/version20.1.0/ffdec_20.1.0_setup.exe)
- [JPEXS Free Flash Decompiler ( Linux )](https://github.com/jindrapetrik/jpexs-decompiler/releases/download/version20.1.0/ffdec_20.1.0.deb)
- [JPEXS Free Flash Decompiler ( MacOS )](https://github.com/jindrapetrik/jpexs-decompiler/releases/download/version20.1.0/ffdec_20.1.0.pkg)
- [JSON](https://github.com/camboris/json-as2/blob/master/JSON.as) ( `ActionScript 2 Library` for `JSON` parsing and stringifying )
- [Paint.NET](https://www.getpaint.net)
- [Unreal Development Kit 2015](https://www.mediafire.com/file/2j7gvobo8sxnlg1/Unreal_Development_Kit_2015.rar/file) ( `GFx Player` and `GFx Classes` )

<u>Sources :</u>

- [ActionScript 2.0 Documentation](https://open-flash.github.io/mirrors/as2-language-reference/index.html)
- [ActionScript 3.0 Documentation](https://airsdk.dev/reference/actionscript/3.0)
- [Green Sock Documentation](https://www.tud.ttu.ee/im/Jaak.Henno/FlashDevelop/greensock-as3/greensock-as3/docs/com/greensock/)
- [Unofficial Skyrim UI SDK](https://github.com/Mardoxx/skyrimui) ( By SkyUI team )

## Credits

- [CommonLibSSE-NG Team](https://github.com/CharmedBaryon/CommonLibSSE-NG) for their great work on their SKSE replacer
- [Eugene](https://www.patreon.com/c/EdgeUI/posts) for his great Edge UI mod that made me want to create my own mod as well
- [Mrowrpurr](https://www.youtube.com/c/skyrimscripting) for C++ scripting tutorials
- [SKSE Team](https://github.com/ianpatt/skse64) for their great script extender
- [SkyUI Team](https://github.com/Mardoxx/skyrimui) for their great work on UI modding

Thanks to them, I'm now able to re-do every single UI component existing in game from the GROUND and creating new custom UI components as well ( for the SKSE part, ActionScript wasn't that complicated to understand me being a web developer ).
