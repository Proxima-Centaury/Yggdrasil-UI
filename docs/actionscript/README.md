## ActionScript Understanding

### Why do you need ActionScript to make things happen :

> ---
> **ActionScript** is a programming language based on **ECMAScript** ( similar to **JavaScript** if you're a fullstack or front web developer, this may ring a bell in your head ).
>
> This language is used to bring UI elements ( built using tool's features or **.png**, **.bmp**, and similar files ) to life.
>
> It allows you to manipulate your UI components and allow users to interact with your UI making it do magical things whenever a user presses a button or scrolls on a list.
>
> Without any script, your UIs will work somehow, by that I mean that your transitions and animations will work, but they'll loop for ever or remain static without having the possibility to manipulate the transitions or animations according to user inputs.
>
> ---

### How to bind a script to a .png file :

> ---
> First of all, don't bind **Scripts** to **.png** files directly, that's not clean and not sure if would work as intended.
>
> Most of the time, you'll turn your **.png Assets** to **Symbols/Shapes** ( I would recommend turning all of your assets to **Shapes**, I faced some issues myself trying to leave everything to **.png** only ) and then to **Movie Clips** ( if they're animated ).
>
> That way you make sure users will benefit from the animations resulting of their interactions with your UI components.
>
> When you create a new UI component in **Adobe Flash Professional CS6**, you can bind an **ActionScript Class** to it through the component's properties context menu.
>
> ---


#### Examples :
For example, if I want to create a **Press Start** interface in **startmenu.swf** :
1. Create a new **Movie Clip** named **Press Start**.
2. Create a **PressStart.as** file ( **.as** is the extension for **ActionScript** files ).
3. Create a **class** named **PressStart** inside of **PressStart.as** file.
4. Right click on the **Movie Clip** named **Press Start**.
5. Go to its properties and write the name of the **PressStart** file inside of the **class** field.
6. Fill the field right above **class** as it stands for the **ActionScript linking**.
    - Allows to bind your **ActionScript class** to the **Movie Clip**.
    - For this example, I'll name it **PressStartObject**.
    - This is required to let **Flash** register everything as intended ( **Object.registerClass("PressStartObject", PressStart);** ).

````javascript
// The "extends MovieClip" is a way to tell to our UI that this class is bound to a MovieClip.
// That way you'll be able to access MovieClip's built-in properties and functions.
// A few example of accessible functions : "gotoAndPlay()", "stop()", "attachMovie()" and so on.

class PressStart extends MovieClip {

    // Code goes here.

};
````

> ---
> Note that there are many other approaches, this is just an example, an other approach would be something like the following ( **see below** ).
>
> ---

````javascript
// Let's pretend we've created a "StartMenu" MovieClip that holds multiple child components, such as "PressStart" and "MainMenu".
// You'd create your "StartMenu" class, and then access your "PressStart" and "MainMenu" MovieClips directly from the parent.
// Note : In this case our parent component is "StartMenu".

class StartMenu extends MovieClip {
    
    // First of all, we declare our child components like so.
    // /!\ Note : IMPORTANT ! To access your child components in ActionScript, you have to make sure you added them as well in Adobe Flash Professional CS6 inside of "StartMenu" MovieClip !
    public var PressStartMovieClip: MovieClip;
    public var MainMenuMovieClip: MovieClip;

    // Then we can access them using "this.PressStartMovieClip" and "this.MainMenuMovieClip" without the quotes of course.
    // Note : The variables ( names ) were set through Adobe Flash Professional CS6's interface.
    // You can put any name you want, just make sure to do it through Adobe Flash Professional CS6 and use the same names in your code.

    // Below, you can find the class constructor, this function runs when the component is loaded.

    public function StartMenu() {

        // Here's and example that shows you how to trigger an animation on a child component.
        // The value "10" here stands for the frame where the animation starts.
        // Note : Assuming you created an animation on Adobe Flash Professional CS6 starting at frame 10 on the targeted child component.

        this.PressStartMovieClip.gotoAndPlay(10);

        // Note that the animation will run until the end or loop for ever, starting from frame 10 depending on your code.
        // You can stop the animation at a specific frame through "onEnterFrame" event ( refer to the code below ).

        this.PressStartMovieClip.onEnterFrame = function(): Void {

            // The "currentFrame" variable stores the current frame of the component that is being watched / observed by the "onEnterFrame" event.

            var currentFrame: Number = this._currentframe;

            // ---------------------------------------------------------------------------------------------------------------------------------------
            // The following piece of code is a piece from my coding approach that is not available yet.
            // Don't follow this code blindly as it is incomplete and stands as an example of what you could achieve, that's all.
            // ---------------------------------------------------------------------------------------------------------------------------------------

            // The "loop" variable contains a boolean ( 0 or 1 / false or true ) that tells me whether the animation is supposed to loop or not.
            // Note : I created this variable, this is not a built-in feature in this case.

            if(!loop && currentFrame == 30) {

                this.stop(); // Stops the animation.

                // The "onAnimationEnd" variable contains a boolean ( 0 or 1 / false or true ) that tells me whether a component has an animation end action that needs to be triggered or not.
                // I decided myself to assign endings to custom animations stored as "objects" with other data to ease the animations manipulation.

                if(onAnimationEnd) {

                    // The "selectedAnimation" variable is an object with various data representing an animation in Adobe Flash Professional CS6.
                    // Example of selectedAnimation : { label: "Loading ( Start )", frames: [ 1, 30 ], onAnimationEnd: [ "PressStart", "displayPressStartMenu" ] }.

                    var onAnimationEndData: Object = selectedAnimation.onAnimationEnd; // Stores the "selectedAnimation.onAnimationEnd" data.

                    // The "scope" variable refers to the first item of "onAnimationEndData" array : "PressStart" in this case ( which is the name of the component where I want to trigger a function ).

                    var scope: Object = Extension.getComponent(onAnimationEndData[0]);

                    // The "methodName" variable refers to the second item of "onAnimationEndData" array : "displayPressStartMenu" in this case.
                    // This is the name of the function inside "PressStart" component that I want to trigger for example.

                    var methodName: String = onAnimationEndData[1];
                    
                    // The "freeze" variable refers to another component that has an animation running at the same time as my "Loading ( Start )" animation.
                    // This variable helps me freeze the other animation when this one has ended.
                    // Note : "freeze" is passed as a third value in "selectedAnimation.onAnimationEnd" inside of my "selectedAnimation" variable.
                    
                    var freeze: String = onAnimationEndData[2];

                    if(!Validator.isUndefined(scope[methodName]) && Validator.isUndefined(freeze)) {

                        // The "scope" : -> Component's class.
                        // The "methodName" : -> The name of the function to trigger inside of the "scope".
                        scope[methodName](); // According to this example, this executes "displayPressStartMenu" function inside of "PressStart" component's class.

                    } else if(Validator.isUndefined(scope[methodName]) && !Validator.isUndefined(freeze)) {

                        // The "Animation" here refers to a utility-custom class created to handle animations separately.
                        // The "stopAnimation" here refers to a method ( function ) that exists in the "Animation" class.

                        Animation.stopAnimation(freeze); // Stops any animation currently playing in another component.

                    } else if(!Validator.isUndefined(scope[methodName]) && !Validator.isUndefined(freeze)) {

                        scope[methodName]();
                        Animation.stopAnimation(freeze);

                    };
                };
            };

            // This is a quick addon if I want to delay an animation for some reason.

            if(delay > 0) { clearTimeout(delayedAnimation); };

            // Note : Every single variable and function presented in this piece of code is from me besides the following :
            // -> this._currentframe; This is a built-in property.
            // -> this.stop(); This is a built-in function.
            // -> clearTimeout(); This is a built-in function.

            // ---------------------------------------------------------------------------------------------------------------------------------------
        };

    };

};
````