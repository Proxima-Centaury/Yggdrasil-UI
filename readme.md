### UI Development Understanding
````markdown
### Tools you will need to achieve your UI overhauls

> Adobe Flash Professional CS4 up to CS6 ( I suggest you to use that last version "CS6" )
> A Flash decompiler ( You can pick JPEXs Free Flash Decompiler from github )
> An online tool or any other software to design your own UI components or edit existing ones ( In my case, I'm using Figma )

### Project understanding

Each interface ( such as : **loadwaitspinner.swf**, **startmenu.swf**, ... ) is built from an **.fla** file that contains various **Assets** and **Scripts**.
The language used to develop the interfaces is **ActionScript**. **ActionScript** has to 2 versions called respectively **ActionScript2** and **ActionScript3**.
I've heard that it is possible to make **ActionScript3** based interfaces, I tried it myself but it appears to me that it is not working on some interfaces.
For consistency and better code understanding, we'll keep using **ActionScript2** version.
When you open your first **.fla** file, using **Adobe Flash Professional CS4 or CS6** ( preferably ), it will prompt you a **Scene**.
**Scene** is the root element of an interface, it will hold your created **child components** ( see SCENE CONTAINER DETAILS SECTION for more informations ).

### Scene container details

For exemple, let's say we're working on **loadwaitspinner.swf**, which is the loader that appears in various places in Skyrim. First, I will create a file named **loadwaitspinner.fla**.
Once created, I will open it using **Adobe Flash Professional CS6**. It will prompt a window with a bunch of buttons and features with a blank **Scene** that takes most of the place.
Now let's say, I've designed my own spinner, I want to make sure it shows up in game. I will have to open my **project's library using CTRL+L** then drag and drop my design file in it.
Once done, my **spinner.png** ( let's pretend I named my spinner that way ) will appear in the library. Right click over it, go to properties and select **lossless PNG compression**.
Now that my **Asset** ( which is my **spinner.png** file ) is optimized for game integration, I will create a new **Layer** in my **Scene**.
Then select the **Layer**, then drag and drop the spinner in it.
Now the **Scene** has **child component**.

* This is just the basics, and this is enough to show your UIs in game, but you won't be able to interact with them until we get to **ActionScript** scripting.

### Debriefing

So, to sum up things, just remember the followings ( **concerns Skyrim, don't know about the other games** ) :
- Each **.swf** file is an in-game interface.
- Each **.swf** file is built from a **.fla** file using a **Flash** design tool such as **Adobe Flash Professional CS6**.
- Each **.swf** file contains various elements called : **Symbols/Shapes/Sprites, Movie Clips, Assets, Fonts, Videos, Layers, Animations/Transitions and Scripts**.
- Each **Script** in a **.swf** file is written using **ActionScript2** or **ActionScript3**.
- You cannot interact with UI components without adding **Scripts** to them.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

* Note : You'll find a precious tutorial on how to use **Adobe Flash Professional CS6** at the end of the file.
````
### ActionScript Understanding
````markdown
### Why do you need ActionScript to make things happen

**ActionScript** is a programming language based on **ECMAScript** ( similar to **JavaScript** if you're a fullstack or front web developer, this may ring a bell in your head ).
This language is used to bring UI elements ( built using tool's features or **.png**, **.bmp**, and similar files ) to life.
It allows you to manipulate your UI components and allow users to interact with your UI making it do magical things whenever a user presses a button or scrolls on a list.

### How to bind a script to a .png file

First of all, don't bind **Scripts** to **.png** files directly, that's not clean and not sure if would work as intended.
Most of the time, you'll turn your **.png Assets** to **Symbols/Shapes** and then to **Movie Clips**.
This way you make sure users will benefit from the animations resulting of their interactions with your UI components.
When you create a new UI component in Adobe Flash Professional CS6, you can bind an **ActionScript Class** to it through the component's properties context menu.

Example :
For example, if I want to create a **Press Start** interface in **startmenu.swf**, I would create a new **Movie Clip** named **Press Start**.
Then, I will create a **PressStart.as** file which is the extension for **ActionScript** files ( .as ), create a class named **PressStart** inside of it.
````
````javascript
// "extends Movie Clip" is a way to tell to our UI that this class is bound to a Movie Clip and therefore can access to MovieClip properties and functions.
class PressStart extends MovieClip {
    // Code goes here.
};
````
````markdown
Note that there are many other approaches, this is just an exemple, an other approach would be something like the following :
````
````javascript
// Let's pretend we've created a "StartMenu" MovieClip that holds multiple child components, such as "PressStart" and "MainMenu".
// You would create your "StartMenu" class, and then access your "PressStart" and "MainMenu" MovieClips directly from the parent ( which is StartMenu in this case ).
class StartMenu extends MovieClip {
    // First of all, we declare our child components like so.
    public var PressStartMovieClip: MovieClip;
    public var MainMenuMovieClip: MovieClip;
    // Then we can access them using "this.PressStartMovieClip" and "this.MainMenuMovieClip" without the quotes of course.
    // Note that the variables names were set through Adobe Flash Professional CS6's interface, in the component's properties section ( not the properties context menu ).
    // You can put any name you want, just make sure to do it through Adobe Flash Professional CS6 and use the same names in your code.
};
````
````markdown
### How to make sure the interface works

You can test your interfaces after **publishing** them, this will open a window with your interfaces running, you'll be able to interact with your interface with some limitations.
For exemple, game data will obviously not load in **Adobe Flash Professional CS6**, you'll be able to interact with your UIs with placeholder texts and variables.
When you've tested your UIs, and made sure there's no compiling errors, you can test them in-game to check if your texts and string variables are filled with game data or not.
It's all about => 1. Design / 2. Code / 3. Merge / 4. Test / 5. Run.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

* Note : That's all for the basics, you'll find another precious tutorial on **ActionScript** scripting and details about existing **Classes** and more at the end of the file.
````
### Project Dependencies & Explanations
````markdown
### Dependencies

First of all, I'm gonna let you know that Skyrim UI building requires some specific **Classes** provided by **Autodesk's Scaleform**.
You can find them by decompiling the vanilla UIs ( using **JPEXs Free Flash Decompiler** ) that can be extracted from the base game's **Interface.bas**.
But I'll provide reworked ( not so much ) versions of them in this repository, up to you.
BSA extractor can be found in nexus mods. You will also need to implement so specific **ActionScript Classes** that will be listed below.

### Dependencies list ( I renamed some of them, and renamed some of their properties and methods )

Autodesk's Scaleform :
- System.Capabilities
- GFX.Controls.Button
- GFX.Controls.ButtonBar
- GFX.Controls.ButtonGroup
- GFX.Controls.CoreList
- GFX.Controls.OptionStepper
- GFX.Controls.RadioButton
- GFX.Controls.ScrollBar
- GFX.Controls.ScrollIndicator
- GFX.Controls.ScrollingList
- GFX.Controls.Slider
- GFX.Controls.TextArea
- GFX.Controls.TextInput
- GFX.Core.UIComponent
- GFX.Data.DataProvider
- GFX.Events.EventDispatcher
- GFX.IO.GameDelegate
- GFX.Managers.FocusHandler
- GFX.Managers.InputDelegate
- GFX.UI.InputDetails
- GFX.UI.NavigationCode
- GFX.Utils.Constraints
- GFX.Utils.Locale

ActionScript : ( With some scaleform integrations )
- Mouse
- Selection
- Stage

Bethesda Classes :
- Shared.BSScrollingList <NOTE I will probably change this **Class** approach or merge it with other scrolling list **Classes**>
- Shared.ButtonChange
- Shared.ButtonTextArtHolder
- Shared.CenteredList
- Shared.CenteredScrollingList
- Shared.GlobalFunction
- Shared.ListFilterer
- Shared.PlatformChange
- Shared.VerticalCenteredList <NOTE I will probably merge this **Class** with **CenteredList** and **CenteredScrollingList** at some point>

My Classes :
- Utilities.Animation ( Optional )
- Utilities.Extension ( Optional )

### Project dependency tree

Bethesda has its own project structure, you can find the dependency tree of the vanilla game by visiting SkyUI Team's GitHub repositories.
Here, I'll provide a different approach ( but still not so different than the vanilla tree ), just it made more sense to me in the way I'm about to present it to you.

Root :
|   > **GFX.Core.UIComponent** that will extend **MovieClip**
|   |   > **Utilities.Animation**, **Animation** will be accessed through instance in **UIComponent**
|   |   > **GFX.IO.GameDelegate**, **GameDelegate** will be accessed through instance in **UIComponent**
|   |   > **GFX.Managers.FocusHandler**, **FocusHandler** will be accessed through instance in **UIComponent**
|   |   > **GFX.Managers.InputDelegate** that will extend **GFX.Events.EventDispatcher**, **InputDelegate** will be accessed through instance in **UIComponent**
|   |   > Your custom **Classes** that will extend **GFX.Core.UIComponent** instead of **MovieClip**
|

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

* Note : You'll find other **.md** files in this repository that will provide more explanations for each class and how to implement or re-use exisintg methods and properties.
````