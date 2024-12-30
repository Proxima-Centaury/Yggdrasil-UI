# UI Development Understanding

## Quick introduction about the files

The files used to create UI components :

- Each interface ( such as : `loadwaitspinner.swf`, `startmenu.swf`, ... ) is built from an `.fla` file which is a flash based project.

- The language used to develop the UI is `ActionScript` and is contained in `.as` files.
    - `ActionScript` has to 2 versions called respectively `ActionScript 2.0` and `ActionScript 3.0`.

## Quick introduction about UI content

The various components used to create UIs :

- For example, let's say we want to create a new main menu built from scratch ( *from the ground* ).
    - First of all, you will need to create a new flash project, and name your `.fla` file according to Skyrim's file name for the same UI component.
    - In Skyrim, the main menu is called `startmenu.swf`, so you will need to name your `.fla` file `startmenu.fla`.
 
- Now that your flash project is created, you can open it using `Adobe Flash Professional CS6`.
    - When you open your project, `Adobe Flash Professional CS6` opens with a default view called `Scene`.
    - The `Scene` serves as a root container for your UI components, the `Scene` is the parent component of your UI.

- Besides the `Scene`, your flash-based UI project will be made using at least `5 elements` specific to game UI creation / modding.
    - The `Layer` that will show-up in the `timeline` section of each of your UI components.
    - The `MovieClip` element serving as a `script-bound component` ( *not necessarily, but most-likely* ) containing multiple `Layers` for `animating` and `scripting`.
    - The `Graphic` element serving as an asset usually holding `bitmaps`, `shapes` and `texts`.
    - The `Asset` element that is simply each visual resource imported as a `.jpg` or `.png` for example.

- To add a `MovieClip` or whatever to your `Scene` or a `MovieClip` as a nested component or asset, you just have to drag and drop it in the view while having a `Layer` selected.

## Summary

So, to sum up things, just remember the followings :

- Each `.swf` file is an in-game interface.
- Each `.swf` file is built from a `.fla` file, using a flash design tool such as `Adobe Flash Professional CS6`.
- Each `.swf` file contains various elements called :
    - `Scene`
    - `Layer`
    - `Movie Clip`
    - `Graphic`
    - `Asset`
    - But also :
        - `Animation`
        - `Font`
        - `Script`
        - `Video`
- The `Layers` elements can contain `Animation transitions`, `ActionScript scripts`, `MovieClips`, `Graphics`, `Assets` or `Videos`.
- To add a component or an asset in your `Scene` or a `MovieClip`, just drag and drop your component or asset while having a `Layer` selected in the view.
- Each `Script` in a `.swf` file is written using `ActionScript 2.0` or `ActionScript 3.0`.
- You cannot interact with UI components without adding `Scripts` to them to handle `Events` such as user keyboard, mouse or controller inputs.
- You'll find a quick tutorial about `ActionScript 2.0` [here](../actionscript/README.md).
  
## Bonus ( additional explanation )

- As a **BONUS**, if you want a 100% percent customized UI mod, you can also create an `SKSE Plugin` using `C++` or create a `Papyrus Script` ( `.psc` to `.pex` files ).
    - Creating an `SKSE Plugin` or a `Papyrus Script` will allow you to trigger `Events` or `Actions` in the game `Engine` such as closing the game, opening another menu and so on.
    - It also allows you to fetch player data to display on your `.swf` UIs directly in your components.
    - As you may have understood, an `SKSE Plugin` or a `Papyrus Script` is like a bridge that joins your `.swf` UIs with the game `Engine`.

If you decide to skip the creation of an `SKSE Plugin` or a `Papyrus Script`, you will have to stick to vanilla `GameDelegate callbacks`.<br/>
That means that you won't be able to create additional custom callbacks.<br/>
You will need to use the already existing `Papyrus callbacks` from the base game to handle your UI actions.

## The flow works like this

<u>Step 1 :</u>
- Your `.swf` file is loaded ( I'm talking about vanilla UIs here such as `startmenu.swf`, `loadwaitspinner.swf`, `statsmenu.swf`, `map.swf`, and so on, **not custom ones** ).

<u>Step 2 :</u>
- If some components in your `.swf` file require in-game data :
    - Your `.swf` file, upon loading or after a specific action, will trigger `ActionScript` functions that will ask an `SKSE Plugin` or a `Papyrus Script` for the data.
    - The `SKSE Plugin` or the `Papyrus Script` will execute a bunch of actions.
    - Then you will receive the data through `class properties` or `function parameters` ( also called `arguments` or `args` ) passed to an `ActionScript function` invoked by your external scripts or vanilla scripts to manipulate to your liking ( *example below* ).

**/!\\** CODE EXAMPLES WILL BE ADDED WHEN I MADE SURE EVERYTHING WORKS AS INTENDED **/!\\**

## UI configuration file

**/!\\** THIS FILE ( `configuration.json` ) SHOULD BY PLACED IN `/Interface/Yggdrasil UI` **/!\\**

It serves as a UI customization preference, allowing to change text colors, content positioning, content visibility, icon swaps, and more to fit your tastes.

### Section `GENERAL` :

```markdown
[Key](SetUIAlignment) :
> Defines the alignment of UI components, as well as their contents and texts
> Value <Center> will align the content in the middle
> Value <Left> will align the content in the left side
> Value <Right> will align the content in the right side
## Note :
If a UI has one or multiple states where it shows 2 or more containers, like startmenu.swf for example where you the have <MainMenu> and ( in some cases ) when selecting a character's save in <CharacterSelection> for example, also shows you another container, then the other container will be placed at the opposite if you chose <Left> or <Right> as value. If you select <Center> the other containers will be placed in the <Left> side first then in the <Right> side if you face cases where you have 3 containers displayed at once.
```

### Section `STARTMENU` :

```markdown
[Key](EnableCustomBackground) :
> Defines whether your custom background should be displayed in startmenu or not
> Value <true> will enable your custom background
> Value <false> will disable your custom background
```

```markdown
[Key](EnableCustomBackgroundRandomizer) :
> Defines whether startmenu background should be randomized or not
> Value <true> will enable custom background randomization
> Value <false> will disable custom background randomization
## Note :
Note that the randomizer will require you to have more than 1 background in the backgrounds folder. Custom backgrounds should be placed in : Interface/Yggdrasil UI/Backgrounds.
```

```markdown
[Key](EnableCustomBackgroundVignette) :
> Defines whether a vignette should be displayed or not
> Value <true> will enable vignette above your custom background
> Value <false> will disable vignette above your custom background
```

### Section `PRESSSTART` :

```markdown
[Key](SetButtonColor) :
> Defines the color of the "Press any button" text
> Value any <HEXCOLOR> without # ( ex : "FFFFFF" )
```

```markdown
[Key](SetCursorLeft) :
> Defines the icon of the cursor next to "Press any button" text
> Value any <ICON> existing in <SetCursorLibrary>
## Note :
The icon you choose here will be searched in the library you decided to use in SetCursorLibrary key, so double check you set the correct Icon IDs here.
```

```markdown
[Key](SetCursorRight) :
> Defines the icon of the cursor next to "Press any button" text
> Value any <ICON> existing in <SetCursorLibrary>
## Note :
The icon you choose here will be searched in the library you decided to use in SetCursorLibrary key, so double check you set the correct Icon IDs here.
```

```markdown
[Key](SetCursorLibrary) :
> Defines from which library the icons should be displayed
> Value any <LIBRARY>
## Note :
Note that the libraries are located in : Interface/Yggdrasil UI/Icons.
```

```markdown
[Key](SetLogo) :
> Defines the main icon that appears during the "Press any button" state
> Value any <ICON> existing in <SetLogoLibrary>
## Note :
The icon you choose here will be searched in the library you decided to use in SetLogoLibrary key, so double check you set the correct Icon IDs here.
```

```markdown
[Key](SetLogoLibrary) :
> Defines from which library the icons should be displayed
> Value any <LIBRARY>
## Note :
Note that the libraries are located in : Interface/Yggdrasil UI/Icons.
```

```markdown
[Key](SetSequelColor) :
> Defines the color of the "V" text
> Value any <HEXCOLOR> without # ( ex : "FFFFFF" )
## Note :
You can change the text in the translation files located in : Interace/Yggdrasil UI/Translations.
```

```markdown
[Key](SetTitleColor) :
> Defines the color of the "The Elder Scrolls" text
> Value any <HEXCOLOR> without # ( ex : "FFFFFF" )
## Note :
You can change the text in the translation files located in : Interace/Yggdrasil UI/Translations.
```

### Section `MAINMENU` :

**/!\\** SECTION UNDER DEVELOPMENT **/!\\**