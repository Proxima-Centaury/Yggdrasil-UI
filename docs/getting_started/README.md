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

**/!\\** THIS FILE ( `configuration.json` ) SHOULD BE PLACED IN `/Interface/Yggdrasil UI` **/!\\**

It serves as a UI customization preference, allowing to change text colors, content positioning, content visibility, icon swaps, and more to fit your tastes.

---

> ### Key `Adjustment` :
> 
> #### Description :
> ```json
> // Allows you to tweak [ x, y ] axis positioning for supported UI elements.
> // Mostly for containers, menus, titles and icons.
> ```
> 
> #### Value :
> ```markdown
> > Accepts object only.
> <x> can be any positive or negative value.
> <y> can be any positive or negative value.
> ```
> 
> #### Usage :
> ```json
> // Following ex decreases UI element's y position by 20 pixels
> "Adjustment": { "x": 0, "y": -20 }
> // Following ex increases UI element's y position by 80.5 pixels
> "Adjustment": { "x": 0, "y": 80.5 }
> // Basically : Current UI element's y position plus or minus y "Adjustment" value
> ```

---

> ### Key `Align` :
> 
> #### Description :
> ```markdown
> > Allows you to tweak [ x ] axis positioning for supported UI elements.
> > Mostly for texts.
> ```
> 
> #### Value :
> ```markdown
> > Accepts string only.
> Can be <center>, <left> or <right>.
> ```
> 
> #### Usage :
> ```json
> // Following ex sets UI element's position to center
> "Align": "center"
> // Following ex sets UI element's position to right
> "Align": "right"
> // May not align text in some cases ( when 2 texts are aligned for example )
> // It's generally because it can be aligned using the container instead
> ```

---

> ### Key `Alpha` :
> 
> #### Description :
> ```markdown
> > Allows you to tweak transparency for supported UI elements.
> > Mostly for backgrounds and menu items.
> ```
> 
> #### Value :
> ```markdown
> > Accepts number only.
> Can be any <positive> value between 0 and 100 included.
> ```
> 
> #### Usage :
> ```json
> // Following ex sets UI element's alpha to 17.5%
> "Alpha": 17.5
> // Following ex sets UI element's alpha to 50%
> "Alpha": 50
> ```

---

> ### Key `Backgrounds` :
> 
> #### Description :
> ```markdown
> > Allows you to define which backgrounds should be displayed.
> > Concerns the Background Randomizer feature only.
> ```
> 
> #### Value :
> ```markdown
> > Accepts array only.
> Can be of any <size>, add as much backgrounds as you want.
> ```
> 
> #### Usage :
> ```json
> // Following ex sets UI element's alpha to 17.5%
> "Backgrounds": [ "0001.dds", "test.dds", "sky.dds", "skyrim_scenery.dds" ]
> // Make sure to add the extension to file name or it won't work
> // Also, it's case-sensitive, so make sure to write each file name correctly
> ```

---

> ### Key `Color` :
> 
> #### Description :
> ```markdown
> > Allows you to tweak color for supported UI elements.
> > Mostly for backgrounds and texts.
> ```
> 
> #### Value :
> ```markdown
> > Accepts string only.
> Can be any <hexadecimal> code.
> ```
> 
> #### Usage :
> ```json
> // Following ex sets UI element's color to a shade of black
> "Color": "262626"
> // Following ex sets UI element's color to red
> "Color": "FF0000"
> // Following ex sets UI element's color to white
> "Color": "FFFFFF"
> ```

---

> ### Key `Colors` :
> 
> #### Description :
> ```markdown
> > Allows you to tweak colors for supported UI elements.
> > Concerns gradient Background feature only.
> ```
> 
> #### Value :
> ```markdown
> > Accepts array only.
> Can be of any <size>, add as much colors as you want.
> ```
> 
> #### Usage :
> ```json
> // Following ex sets UI element's gradient to a shade of black
> // Adding same color multiple times is needed if you want to tweak the spread
> "Colors": [ "262626", "262626", "262626", "262626", "262626" ]
> // Following ex sets UI element's gradient from red to green then blue
> // Starts with red, goes to green, then to blue
> "Colors": [ "FF0000", "00FF00", "0000FF" ]
> // Following ex sets UI element's gradient from white to darker shades
> // Adding same color multiple times is needed if you want to tweak the spread
> "Colors": [ "FFFFFF", "EEEEEE", "DDDDDD", "CCCCCC" ]
> ```

---

> ### Key `Direction` :
> 
> #### Description :
> ```markdown
> > Allows you to tweak gradient direction for supported UI elements.
> > Concerns gradient Background feature only.
> ```
> 
> #### Value :
> ```markdown
> > Accepts string only.
> Can be <TtoB>, <BtoT>, <LtoR>, <RtoL>, <TLtoBR>, <TRtoBL>, <BRtoTL> or <BLtoTR>.
> ```
> 
> #### Usage :
> ```json
> // Following ex sets UI element's gradient from top to bottom
> "Direction": "TtoB"
> // Following ex sets UI element's gradient from right to left
> "Direction": "RtoL"
> // Following ex sets UI element's gradient from bottom-left to top-right
> "Direction": "BLtoTR"
> ```

---

> ### Key `Enabled` :
> 
> #### Description :
> ```markdown
> > Allows you to enable or disable some features for supported UI elements.
> ```
> 
> #### Value :
> ```markdown
> > Accepts boolean only.
> Can be <false> or <true>.
> ```
> 
> #### Usage :
> ```json
> // Following ex enables related feature
> "Enabled": true
> // Following ex disables related feature
> "Enabled": false
> ```