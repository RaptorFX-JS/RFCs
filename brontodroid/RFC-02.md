# Brontodroid - API Decisions

As discussed in the first RFC, Brontodroid will use Deno's API while also providing another API with the namespace of `Brontodroid`, which would allow developers to control the android app window. On top of that, we aim to add an extensions API which would allow you to easily extend the API in your own way. The following is a list of API Features (methods, classes etc) that will come with Brontodroid's API. 

## Deno

For Deno's API Recreation, we will have a few exceptions. This is to ensure stability and ease of development for both, users and contributors of Brontodroid. The exceptions are as follows: 

- FFI System: Deno FFI is a system to load shared libraries (`.so`) and functions from them, which can be in-turn used for executing tasks directly from the WebView JS VM (V8 in this case). We are excluding this feature for 2 major reasons: Security and Replacement. Deno allows people to use shared libraries from across the web by fetching them and then executing on them, this however, is a security flaw as per we do not get the same permissions API on android, meaning, we can not sandbox this. Another issue is the fact that this will be inherently slower. Now for the second reason, we are considering having functions being executed from the JVM instead, as it's more easy and secure to do with our upcoming plans. For more details, look below at the 'Extensions' section. 

- FMT: Formatting Module will not be ported as per there is nothing to 'format' if you will, even if we do port it, it will not be the traditional FMT from Deno, but rather something for rendering (or related to CSS). 

- Logger: Mostly the same reason as formatting module, there is nothing to 'log' to unless we consider logging to text files stored somewhere on the disk. 

The listed deprecated modules above are not confirmed to be deprecated but there is highly a chance they will be or will be replaced, another note to be taken is that we might provide a much better replacement for them if we can.  

## Brontodroid 

The following will be available under the `Brontodroid` namespace (and class: `dev.remod.brontdroid` if you're modifying source directly): 

- `onCreateWV`: This function is executed on app's launch. This is specified in the `load.json` file on what JS/Java to evaluate.

- `onCloseWV`: This function is fired on the closing of the App Process. This is specified in the `load.json` file on what JS/Java to evaluate.

- `rotateDisplay`: Rotates the user display to either `Rotation.PORTRAIT` or `Rotation.LANDSCAPE`, depending on the argument passed. 

- `toggleFullScreen`: This will toggle the full-screen from on to off and vice-versa.

- `changeStatusBarColor`: This takes a string with the Hex Code of a color as argument, and will change the color of the status bar to that of the argument passed.

- `nativeNotificationBuilder`: Takes in arguments and builds a notification that can be deployed at any point in time.

- `nativeWidgetBuilder`: Similar to `nativeNotificationBuilder`, this function takes in arguments and an event listener to fire the widget creation and other actions.

## Extensions

Extensions are a way to 'extend' Brontodroid further, it requires you to make your own module and bundle that it in with your output Android Package. This isn't necessarily a part of Brontodroid itself, but rather Android WebView, which has binding functions in-built. However, we do want to make the process easier and at one point 100% doable just from the JS/TS API.

---

Thank you for reading. Please provide feedback and critique things where necessary.
