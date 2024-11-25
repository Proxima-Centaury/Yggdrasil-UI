# UI Development Understanding

## Quick introduction about the files

The files used to create UI components :

> <br/>
> 
> - Each interface ( such as : `loadwaitspinner.swf`, `startmenu.swf`, ... ) is built from an `.fla` file which is a flash based project.
>
> - The language used to develop the UI is `ActionScript` and is contained in `.as` files.
>   - `ActionScript` has to 2 versions called respectively `ActionScript 2.0` and `ActionScript 3.0`.
>
> </br>

## Quick introduction about UI content

The various components used to create UIs :

> <br/>
> 
> - For example, let's say we want to create a new main menu built from scratch ( *from the ground* ).
>   - First of all, you will need to create a new flash project, and name your `.fla` file according to Skyrim's file name for the same UI component.
>   - In Skyrim, the main menu is called `startmenu.swf`, so you will need to name your `.fla` file `startmenu.fla`.
> 
> - Now that your flash project is created, you can open it using `Adobe Flash Professional CS6`.
>   - When you open your project, `Adobe Flash Professional CS6` opens with a default view called `Scene`.
>   - The `Scene` serves as a root container for your UI components, the `Scene` is the parent component of your UI.
>
> - Besides the `Scene`, your flash-based UI project will be made using at least `5 elements` specific to game UI creation / modding.
>   - The `Layer` that will show-up in the `timeline` section of each of your UI components.
>   - The `MovieClip` element serving as a `script-bound component` ( *not necessarily, but most-likely* ) containing multiple `Layers` for `animating` and `scripting`.
>   - The `Button` element serving as an action trigger through `scripting`.
>   - The `Graphic` element serving as an asset usually holding `bitmaps`, `shapes` and `texts`.
>   - The `Asset` element that is simply each visual resource imported as a `.jpg` or `.png` for example.
>
> </br>

## Summary

So, to sum up things, just remember the followings :

- Each `.swf` file is an in-game interface.
- Each `.swf` file is built from a `.fla` file, using a flash design tool such as `Adobe Flash Professional CS6`.
- Each `.swf` file contains various elements called :
  - `Scene`
  - `Layer`
  - `Movie Clips`
  - `Button`
  - `Graphic`
  - `Asset`
  - But also :
    - `Animation`
    - `Font`
    - `Script`
    - `Video`
- Each `Script` in a `.swf` file is written using `ActionScript 2.0` or `ActionScript 3.0`.
- You cannot interact with UI components without adding `Scripts` to them.
- You'll find a quick tutorial about `ActionScript 2.0` [here](../actionscript/README.md).