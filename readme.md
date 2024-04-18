### UI Development Understanding
---

#### Tools you will need to achieve your UI overhauls :

> ---
> 1. **Adobe Flash Professional CS4 up to CS6**. ( I suggest you to use that last version **CS6** )
> 2. **Unreal Development Kit 2015**. ( Contains GFX Extensions, CLIK files / GFX Player )
> 3. **A Flash decompiler**. ( You can pick **JPEXs Free Flash Decompiler** from GitHub )
> 4. **An online tool or any other software to design your own UI components or edit existing ones**. ( In my case, I'm using **Figma** )
> 
> ---

````markdown
* 0 : You'll find download links and resources at the end of this file.
````

#### Adobe Flash CS6 + GFX setup :

- Install **Adobe Flash Professional CS6**.
  - You will find a crack inside of the archive as well with an **Instructions.txt**.
  - Download links for the tools can be found at the end of this documentation.
- Install **Unreal Development Kit 2015**.
  - There's no setup file here, content provided already unpacked, as-is, just extract the content in the location of your choice.
- Run **Adobe Flash Professional CS6**.
- In **Adobe Flash Professional CS6**, go to the following path :
  - **Help > Manage extensions**. Should prompt you a window like this one :
  ![Screenshot of Flash CS6 Pro extension manager.](/documentation/screenshots/extension_manager.jpg)
- Click **Install**, then browse to your **Unreal Development Kit 2015** install location.
  - Find **Scaleform Extensions.mxp** located in **UDK 2015-01/Binaries/GFx/CLIK Tools**.
  - Click on the file to install **Scaleform Extensions**.
  - Restart **Adobe Flash Professional CS6**.
- In **Adobe Flash Professional CS6**, go to the following path :
  - **Edit > Preferences > ActionScript** and click on **ActionScript 2.0 parameters** button here :
  ![Screenshot of Flash CS6 Pro ActionScript settings.](/documentation/screenshots/actionscript_settings.jpg)
  - A window like this one should open :
  ![Screenshot of Flash CS6 Pro ActionScript settings.](/documentation/screenshots/actionscript_classes.jpg)
  - Click the **+** sign and add the following path :
    - **{REPLACE THIS WITH YOUR DRIVE AND PARENT FOLDERS EVENTUALLY}/UDK 2015-01/Development/Flash/AS2/CLIK**.
    - **/!\\** Replace the the text inside the braces with your **Unreal Development Kit 2015** drive location, **C:/** or whatever.
    - **/!\\** And eventually add parent folders IF **UDK 2015-01** folder is **INSIDE ANOTHER FOLDER**, then remove the braces as well.
  - When done, click **OK**, the window will close.
- Have a look at the right panel in **Adobe Flash Professional CS6**.
  - If you can't find a section called **Scaleform Launcher**, you will need to go to the following path :
  - **Window > Other Panels** and click on **Scaleform Launcher**, now it should appear on **Adobe Flash Professional CS6** right panel.
- Now you should be able to bind GFX Player to **Adobe Flash Professional CS6**.
  - In **Scaleform Launcher** section on the right panel, click on the **+** sign, it will open a small window with **3 inputs**.
  - In the first input, click on the **+** sign and go to your **Unreal Development Kit 2015** installation, then go to the following path :
    - **UDK 2015-01/Binaries/GFx** and select **GFxMediaPlayerD3d9.exe**, it will ask you to choose a name for the player, I suggest typing **GFxMediaPlayer**.
  - In the second input, enter a profile name for your player profile, you can type whatever you want.
  - Leave the third input as it is, then click **OK**, you should be able to simulate in-game behaviors now by clicking on **Test with : GFxMediaPlayer** after selecting your profile in the dropdown below ( may have some limitations though, not sure, you'll have to test it by yourself until I provide more informations about that ).

#### Project understanding :

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
> The **Scene** element is the root of an interface, it will hold your created **child components**. ( see **[scene container details](#scene-container-details) section** for more informations )
>
> ---

#### Scene container details :

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
> To be able to see your UIs in game, you will need to convert your **.fla** files to **.swf** files. To do so, go to **File > Publishing parameters** and make sure the **target** is set to **Flash Player 11.2** and the **script** to **ActionScript 2.0**.
>
> Once you made sure the parameters were set properly, you can choose the **.swf file output location**, and then you can press **Ok** or **Publish**, note that once this step is done, you'll be able to publish and test your UIs by using **CTRL+Enter** shortcut.
>
> This will create a **.swf** file. ( By the way, don't change the base game's **.swf** file names, this could brake your UIs in game, note that it's not the case for custom created UIs, you'll be able to name them as you wish since they're built from the ground )
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
* 3 : You'll find a precious tutorial on how to use **Adobe Flash Professional CS6** at the end.
````

### ActionScript Understanding
---

#### Why do you need ActionScript to make things happen :

> ---
> **ActionScript** is a programming language based on **ECMAScript**. ( similar to **JavaScript** if you're a fullstack or front web developer, this may ring a bell in your head )
>
> This language is used to bring UI elements ( built using tool's features or **.png**, **.bmp**, and similar files ) to life.
>
> It allows you to manipulate your UI components and allow users to interact with your UI making it do magical things whenever a user presses a button or scrolls on a list.
>
> Without any script, your UIs will work somehow, by that I mean that your transitions and animations will work, but they'll loop for ever or remain static without having the possibility to manipulate the transitions or animations according to user inputs.
>
> ---

#### How to bind a script to a .png file :

> ---
> First of all, don't bind **Scripts** to **.png** files directly, that's not clean and not sure if would work as intended.
>
> Most of the time, you'll turn your **.png Assets** to **Symbols/Shapes** ( I would recommend turning all of your assets to **Shapes**, I faced some issues myself trying to leave everything to **.png** only ) and then to **Movie Clips** ( if they're animated ).
>
> That way you make sure users will benefit from the animations resulting of their interactions with your UI components.
>
> When you create a new UI component in **Adobe Flash Professional CS6**, you can bind an **ActionScript Class** to it through the component's properties context menu.
>
> Example :
>
> For example, if I want to create a **Press Start** interface in **startmenu.swf**, I would create a new **Movie Clip** named **Press Start**.
>
> Then, I will create a **PressStart.as** file which is the extension for **ActionScript** files ( **.as** ), create a class named **PressStart** inside of it.
>
> ---

````javascript
// "extends Movie Clip" is a way to tell to our UI that this class is bound to a Movie Clip.
// That way you'll be able to access MovieClip's built-in properties and functions.
class PressStart extends MovieClip {

    // Code goes here.

};
````

> ---
> Note that there are many other approaches, this is just an example, an other approach would be something like the following. ( **see below** )
>
> ---

````javascript
// Let's pretend we've created a "StartMenu" MovieClip that holds multiple child components,
// such as "PressStart" and "MainMenu".

// You would create your "StartMenu" class,
// and then access your "PressStart" and "MainMenu" MovieClips directly from the parent.
// ( which is StartMenu in this case )

class StartMenu extends MovieClip {
    
    // First of all, we declare our child components like so.
    public var PressStartMovieClip: MovieClip;
    public var MainMenuMovieClip: MovieClip;
    
    // Then we can access them using "this.PressStartMovieClip" and "this.MainMenuMovieClip"
    // without the quotes of course.
    
    // Note that the variables names were set through Adobe Flash Professional CS6's interface,
    // in the component's properties section. ( Not the properties context menu )
    
    // You can put any name you want, just make sure to do it through Adobe Flash Professional CS6
    // and use the same names in your code.

};
````

#### How to make sure the interface works :

> ---
> You can test your interfaces after **publishing** them, this will open a window with your interfaces running, you'll be able to interact with your interface with some limitations.
>
> For example, game data will obviously not load in **Adobe Flash Professional CS6**, you'll be able to interact with your UIs with placeholder texts and variables.
>
> When you've tested your UIs, and made sure there's no compiling errors, you can test them in-game to check if your texts and string variables are filled with game data or not.
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
* 4 : You'll find another precious tutorial on **ActionScript** scripting at the end.
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
> You'll find out more by checking this repository's files, everything will be explained. ( as much as I can explain it of course )
>
> ---

````markdown
* 5 : You'll find other **.md** files in this repository, providing more explanations for each class.
* 6 : That's all for the introduction, see below for some download links.
````

### Download Links
---

Tools :
- [Adobe Flash Professional CS6](https://www.mediafire.com/file/fiylko26035lrxb/Adobe_Flash_Professional_CS6_%2528_Version_12.0.0.481_%2529.rar/file) <s>( Have a look at my [Yggdrasil UI](https://www.nexusmods.com/skyrimspecialedition/mods/108880?tab=files) mod page for the tool )</s>
- [Unreal Development Kit 2015](https://www.mediafire.com/file/2j7gvobo8sxnlg1/Unreal_Development_Kit_2015.rar/file)
- [JPEXs Free Flash Decompiler ( Windows )](https://github.com/jindrapetrik/jpexs-decompiler/releases/download/version20.1.0/ffdec_20.1.0_setup.exe)
- [JPEXs Free Flash Decompiler ( Linux )](https://github.com/jindrapetrik/jpexs-decompiler/releases/download/version20.1.0/ffdec_20.1.0.deb)
- [JPEXs Free Flash Decompiler ( MacOS )](https://github.com/jindrapetrik/jpexs-decompiler/releases/download/version20.1.0/ffdec_20.1.0.pkg)
- [Figma ( Windows )](https://www.figma.com/download/desktop/win) ( You can stick to the online tool though, not forced to download the app )
- [Figma ( MacOS )](https://www.figma.com/download/desktop/mac) ( You can stick to the online tool though, not forced to download the app )
- [BSA Archive Extractor](https://www.nexusmods.com/skyrimspecialedition/mods/974?tab=files&file_id=5396)
