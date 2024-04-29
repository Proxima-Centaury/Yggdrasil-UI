# UI Development Understanding
---

## Required tools:

The tools required for UI development in Skyrim are as follows:

- Adobe Flash Professional CS4/CS6 
	- Cs6 is the recommended one and the one this guide is written for
- Unreal Development Kt 2015.
	- It contains the necessary GFX extensions, CLIK files etc.
- A Flash decompiler, such as [JPEXs Free Flash Decompiler](https://github.com/jindrapetrik/jpexs-decompiler/)
	- Used for decompiling the vanilla SWF files (more on those later)
- A tool of your choice to design UI elements.
	- A free online one is [Figma](https://www.figma.com/) but anything will work.
- Downloads to all of them can be found [here](#download-links).

## Setting up the enviroment

#### Installing and configuring the required tools

1. Install **Adobe Flash Professional CS6**.
	- You will find a crack inside of the archive as well with an **Instructions.txt**.
	- Download links for the tools can be found at the end of this documentation.
2. Install **Unreal Development Kit 2015**.
	- There's no setup file here, content provided already unpacked, as-is, just extract the content in the location of your choice.
	- For example `C:/Tools/Unreal Development Kit 2015/`

3. Configure **Adobe Flash Professional CS6**.
	- Run **Adobe Flash Professional CS6**.
	- In **Adobe Flash Professional CS6**, go to the following path: **Help > Manage extensions**. 
		- Should prompt you a window like this one:
		![Extension Menu](/docs/resources/media/extension_menu.png)

	- Click **Install**, then browse to your **Unreal Development Kit 2015** install location.
		- If you have been following this tutorial, that would be:
		 `C:/Tools/Unreal Development Kit 2015`
  	- Find **Scaleform Extensions.mxp** located in **UDK 2015-01/Binaries/GFx/CLIK Tools**.
  	- Click on the file to install **Scaleform Extensions**.
		- Cs6 will inform you that it needs to restart for changes to apply, do that.

	- In **Adobe Flash Professional CS6** go to the following settings -> **Edit > Preferences > ActionScript** and click on **ActionScript 2.0 parameters** button here:
	![Actionscript Settings](/docs/resources/media/actionscript_settings.png)
	- A new window should open, you'd want to input the paths for the UDK Flash files for Action Script 2 by hitting the plus sign like so:
	![Actionscript Classes](/docs/resources/media/actionscript_classes.png)
		1. Click the plus sign to add a new class
		2. Browse the following path, assuming you have followed the tutorial:
		`C:/Tools\Unreal Development Kit 2015/UDK 2015-01/Development/Flash/AS2/CLIK`
			- Depending on how you extracted the file, the `UDK 2015-01` folder might be inside another folder, adjust accordingly.
		3. Press `Ok`, the window should automatically close.
	- Go to the following path **Window > Other Panels** and click on **Scaleform Launcher**
		- A new window should open, which you can then drag into Adobe CS6's right panel for easier access, like so:
		
			![Scaleform Launcher Right Panel](/docs/resources/media/Scaleform-Launcher.mov)
	
  	- In **Scaleform Launcher** section on the right panel, click on the **+** sign, it will open a small window with **3 inputs**.
  	- In the first input, click on the **+** sign and go to your **Unreal Development Kit 2015** installation, then go to the following path :
    - **UDK 2015-01/Binaries/GFx** and select **GFxMediaPlayerD3d9.exe**, it will ask you to choose a name for the player, I suggest typing **GFxMediaPlayer**.
  	- In the second input, enter a profile name for your player profile, you can type whatever you want.
	- Leave the third input untouched.
	- It should look something like this:
	![Scaleform Launcher profile](/docs/resources/media/scaleform-launcher-profile.png)
  	- If everything is as it should, click `Ok`.
	- You can now test your UI behaviors by starting the Scaleform Launcher from the right panel and select `Test with: GFxMediaPlayer`:
	![Scaleform Launcher Test](/docs/resources/media/scaleform_launcher_test.png)
		- This may have some limitations, you'll have to test around yourself until I can provide more information.

## Understanding interfaces and SWFs

> ---
> Each interface ( such as : **loadwaitspinner.swf**, **startmenu.swf**, ... ) is built from an **.fla** file that contains various **Assets** and **Scripts**.
>
> The language used to develop the interfaces is **ActionScript**. **ActionScript** has to 2 versions called respectively **ActionScript 2.0** and **ActionScript 3.0**.
>
> I've heard that it is possible to make **ActionScript 3.0** based interfaces, I tried it myself but it appears to me that it is not working on some interfaces.
>
> For consistency and better code understanding, we'll keep using **ActionScript 2.0** version.
>
> When you open your first **.fla** file, using **Adobe Flash Professional CS4 or CS6** ( preferably ), it will prompt you a **Scene**.
>
> The **Scene** element is the root of an interface, it will hold your created **child components** ( see **[scene container details](#scene-container-details-) section** for more informations ).
>
> ---

#### Scene container details

> ---
> For example, let's say we're working on **loadwaitspinner.swf**, which is the loader that appears in various places in Skyrim. First, I will create a file named **loadwaitspinner.fla**.
>
> Once created, I will open it using **Adobe Flash Professional CS6**. It will prompt a window with a bunch of buttons and features with a blank **Scene**.
>
> Now let's say, I've designed my own spinner, I want to make sure it shows up in game. I will have to open my **project's library using CTRL+L** then drag and drop my design file in it.
>
> My **spinner.png** ( let's pretend I named my spinner that way ) will appear in the library. Right click over it, go to properties and select **lossless PNG compression**.
>
> Now that my **Asset** ( which is my **spinner.png** file ) is optimized for game integration, I will create a new **Layer** in my **Scene**.
>
> Then select the **Layer**, and drag and drop the spinner in it. Now the **Scene** has a **child component**.
>
> ---

#### Project building :

> ---
> To be able to see your UIs in game, you will need to convert your **.fla** files to **.swf** files. To do so, go to **File > Publishing parameters** and make sure the **target** is set to **Flash Player 11.2** and the **script** to **ActionScript 2.0**. Once you made sure the parameters were set properly, you can choose the **.swf file output location**, and then you can press **Ok**.
>
> If **YOU ARE NOT USING GFX PLAYER**, do the following :
> After setting the parameters as mentioned above, you can press **CTRL+Enter** to compile your projects to **.swf**.
>
> If **YOU ARE USING GFX PLAYER** :
> Your projects will be converted to **.swf** automatically when you test your UIs through the player on **Adobe Flash Professional CS6**'s right panel.
>
> This will create a **.swf** file ( By the way, don't change the base game's **.swf** file names, this could brake your UIs in game, note that it's not the case for custom created UIs, you'll be able to name them as you wish since they're built from the ground ).
>
> Now that you have your **.swf** file, you can put it in the base game **/Interface** folder, or create a mod of it and install it through a mod manager using the same game folder path.
>
> ---

````markdown
* 1 : This is just the basics, and this is enough to show your UIs in game.
* 2 : Note that you won't be able to interact with them until we get to **ActionScript** scripting.
````

#### Debriefing :

So, to sum up things, just remember the followings :

- Each **.swf** file is an in-game interface.
- Each **.swf** file is built from a **.fla** file, using a **Flash** design tool such as **Adobe Flash Professional CS6**.
- Each **.swf** file contains various elements called :
  - **Scenes**
  - **Symbols, Shapes or Sprites**
  - **Movie Clips**
  - **Assets**
  - **Fonts**
  - **Videos**
  - **Layers**
  - **Animations or Transitions**
  - **Scripts**.
- Each **Script** in a **.swf** file is written using **ActionScript 2.0** or **ActionScript 3.0**.
- You cannot interact with UI components without adding **Scripts** to them.

````markdown
* 3 : You'll find a precious tutorial on how to use **Adobe Flash Professional CS6** [here](/docs/resources/Scripting%20examples.md) **NOT FINISHED YET**
````


````

#### How to make sure the interface works :

> ---
> You can test your interfaces after **publishing** with **CTRL+Enter** if **YOU ARE NOT USING GFX PLAYER**, this will open a window with your interfaces running, you'll be able to interact with your interface with some limitations.
>
> For example, game data will obviously not load in **Adobe Flash Professional CS6**, you'll be able to interact with your UIs with placeholder texts and variables.
>
> When you've tested your UIs, and made sure there's no compiling errors, you can test them in-game to check if your texts and string variables are filled with game data or not.
>
> You can also test your interfaces with **GFX Player** that provides **more features and controller support** than built-in **Adobe Flash Professional CS6**'s player.
>
> It's all about :
> 1. Designing UI components and moving them to your **.fla** file.
> 2. Coding the logic behind the interaction with your UI components to bring them to life.
> 3. Merging your UI components and your **scripts** through **Adobe Flash Professional CS6**.
> 4. Testing your UIs in **Adobe Flash Professional CS6** first, checking the interactions, the animations.
> 5. Running your UIs in game to see if your interface components receive game data or not.
>
> ---

````markdown
* 4 : You'll find another precious tutorial on **ActionScript** scripting at the end. #NOT_AVAILABLE_YET
````

### Project Dependencies & Explanations
---

#### Dependencies :

> ---
> First of all, I'm gonna let you know that Skyrim UI building requires some specific **Classes** provided by **Autodesk's Scaleform**.
>
> You can find them by decompiling the vanilla UIs ( using **JPEXs Free Flash Decompiler** ) that can be extracted from the base game's **Interface.bsa**.
>
> But I'll provide reworked ( not so much ) versions of them in this repository, up to you.
>
> BSA extractor can be found in nexus mods. You will also need to implement some specific **ActionScript Classes**, everything needed will be listed below.
>
> ---

#### Dependencies list : SKIP THIS SECTION AS IT IS RELATED TO MY CUSTOM APPROACH ( which is not available yet )

> ---
> Note : *I renamed some of them, and renamed some of their properties and methods as well*.
>
> Autodesk's Scaleform :
> - **System.Capabilities**
> - **GFX.Controls.Button**
> - **GFX.Controls.ButtonBar**
> - **GFX.Controls.ButtonGroup**
> - **GFX.Controls.CoreList**
> - **GFX.Controls.OptionStepper**
> - **GFX.Controls.RadioButton**
> - **GFX.Controls.ScrollBar**
> - **GFX.Controls.ScrollIndicator**
> - **GFX.Controls.ScrollingList**
> - **GFX.Controls.Slider**
> - **GFX.Controls.TextArea**
> - **GFX.Controls.TextInput**
> - **GFX.Core.UIComponent**
> - **GFX.Data.DataProvider**
> - **GFX.Events.EventDispatcher**
> - **GFX.IO.GameDelegate**
> - **GFX.Managers.FocusHandler**
> - **GFX.Managers.InputDelegate**
> - **GFX.UI.InputDetails**
> - **GFX.UI.NavigationCode**
> - **GFX.Utils.Constraints**
> - **GFX.Utils.Locale**
>
> ActionScript : ( With some scaleform integrations )
> - **Mouse**
> - **Selection**
> - **Stage**
>
> Bethesda Classes :
> - **Shared.BSScrollingList** ( I will probably change this **Class** approach or merge it with other scrolling list **Classes** )
> - **Shared.ButtonChange**
> - **Shared.ButtonTextArtHolder**
> - **Shared.CenteredList**
> - **Shared.CenteredScrollingList**
> - **Shared.GlobalFunction**
> - **Shared.ListFilterer**
> - **Shared.PlatformChange**
> - **Shared.VerticalCenteredList** ( I will probably merge this **Class** with **CenteredList** and **CenteredScrollingList** at some point )
>
> My Classes :
> - **Utilities.Animation** ( Optional )
> - **Utilities.Extension** ( Optional )
>
> ---

#### Project dependency tree :

> ---
> Bethesda has its own project structure, you can find the dependency tree of the vanilla game by visiting SkyUI Team's GitHub repositories.
>
> Here, I'll provide a different approach ( but still not so different than the vanilla tree ), just that it made more sense to me in the way I'm about to present it to you.
>
> You'll find out more by checking this repository's files, everything will be explained ( as much as I can explain it of course ).
>
> ---

````markdown
* 5 : You'll find other **.md** files in this repository, providing more explanations for each class. #NOT_AVAILABLE_YET
* 6 : That's all for the introduction, see below for some download links.
````

### Download Links
---

Tools:
- [Adobe Flash Professional CS6](https://www.mediafire.com/file/fiylko26035lrxb/Adobe_Flash_Professional_CS6_%2528_Version_12.0.0.481_%2529.rar/file) <s>( Have a look at my [Yggdrasil UI](https://www.nexusmods.com/skyrimspecialedition/mods/108880?tab=files) mod page for the tool )</s>
- [Unreal Development Kit 2015](https://www.mediafire.com/file/2j7gvobo8sxnlg1/Unreal_Development_Kit_2015.rar/file)
- [JPEXs Free Flash Decompiler ( Windows )](https://github.com/jindrapetrik/jpexs-decompiler/releases/download/version20.1.0/ffdec_20.1.0_setup.exe)
- [JPEXs Free Flash Decompiler ( Linux )](https://github.com/jindrapetrik/jpexs-decompiler/releases/download/version20.1.0/ffdec_20.1.0.deb)
- [JPEXs Free Flash Decompiler ( MacOS )](https://github.com/jindrapetrik/jpexs-decompiler/releases/download/version20.1.0/ffdec_20.1.0.pkg)
- [Figma ( Windows )](https://www.figma.com/download/desktop/win) ( You can stick to the online tool though, not forced to download the app )
- [Figma ( MacOS )](https://www.figma.com/download/desktop/mac) ( You can stick to the online tool though, not forced to download the app )
- [BSA Archive Extractor](https://www.nexusmods.com/skyrimspecialedition/mods/974?tab=files&file_id=5396)

Sources :
- [ActionScript 2.0 Documentation](https://open-flash.github.io/mirrors/as2-language-reference/index.html)
- [Unofficial Skyrim UI SDK](https://github.com/Mardoxx/skyrimui) ( By SkyUI team )