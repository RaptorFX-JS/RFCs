# RaptorFX
![RaptorFX Logo - by ArathainFarqou and LePichu](https://cdn.discordapp.com/attachments/890845937243684886/921414193423466536/rfx_text_logo.png)
![Our Motive!](https://cdn.discordapp.com/attachments/890845937243684886/979286337016430632/sub_text.png)
   
## Aim 
RaptorFX aims to centralise app development into one codebase by targetting multiple platforms at once. It will make use of web technologies to make it easier for anyone to dive in and start developing. People may even contribute to the main codebase of RaptorFX if they wish to add features or fix bugs.

## Core

### API 
RaptorFX, while shipping a Deno instance, will also ship its own set of functions (like Electron, Tauri, or Neutralino) to make it easier to work across multiple platforms with ease. We also aim to blend in with existing Web APIs and Standards. The following is a list of classes, functions, enums, and related, all of which come under the namespace of `RaptorFX`, each with a description of what they do: 

#### Classes
- `Clipboard`: Relates to the user's clipboard (store of keyboard copy items).
- `Notifications`: Manages notifications; push, group, pop.
- `Window`: Window-related activities like Maximise, Minimize, and Position.
- `System`: System-related class which returns Architecture, OS, etc.

#### Interfaces
- `NotificationData`: 
    * `title (string)`: Main title of the notification.
    * `description (string)`: Description/secondary title of the notification.
    * `icon (url)`: URL of the icon to show in the notification.

- `PositionData`:
    * `x (number)`: Starting coordinate in the X-Axis of the Window.
    * `y (number)`: Starting coordinate in the Y-Axis of the Window.
    * `height (number)`: Height of the Window.
    * `width (number)`: Width of the Window.

#### Functions 
- `Clipboard`: 
    * `copy () ['type/text' | 'type/image']`: Copies contents of user's clipboard. 
    * `cut () ['type/text' | 'type/image']`: Cuts content from user's clipboard and empties it..
    * `push (content: 'type/text' | 'type/image') [void]`: Pushed custom data to user clipboard.

- `Notifications`:
    * `push (data: NotificationData, mode: NotificationMode) [Promise]`: Pushes the notification built from data, with the given configuration and channel to send to.
    * `createToast (data: String, length: ToastLength) [void]`: Creates a Toast with data provided. [*¹]

- `Window`:
    * `maximize () [void]`: Maximizes the context window.
    * `minimize () [void]`: Minimizes the context window.
    * `exit (code: number) [void]`: Completely exits the context window with an exit code.
    * `position (newPosition: PositionData) [PositionData]`: If given arguments, changes the position of the window, without any arguments, the current cordinates of window are returned as `PositionData`.
    * `statusBarColor (mode: WindowBarMode, hex?: String) [string]`: Sets or gets/returns the color of the status bar/window accent color if provided a hex color as paramater, defaults to set mode. 

- `System`:
    * `arch () [string]`: Returns the architecture (`x86`, `arm64` etc.) of the system as a string.
    * `os () [string]`: Returns the operating system (`windows_11`, `android_12` etc.) of the system as a string.
    * `locale () [string]`: Returns the system's locale, for example: `en_US`, `fr_FR`, `hi_IN` etc.

#### Variables
- `LocalStorage`: Points to the path of the internal app storage, which could be a folder under `$USER\LocalAppData\YourApp\` (on Windows), or `data/data/YourApp` (on Android).
- `ExternalStorage`: Points to the root of the file system, usually `/mounted/0/` (on Android), or any absolute/relative path on other operating systems like Windows or Linux.

#### Enums
- `ToastLength`: Accepts `SHORT` and `LONG`, self-describing length of Toast displayed on the screen. [*¹]
- `NotificationMode`: Accepts `SINGLE` and `GROUP`, where `SINGLE` creates a new notification for each push, while `GROUP` collects it into a single grouped notification. 
- `WindowBarMode`: Accepts `SET` and `GET`, where `SET` would make the function overwrite the current color of status bar if provided and return the hex provided, otherwise `GET` will simply return the current color without modifying.

_Classes and Interfaces are available as `<InterfaceName>`, functions as `RaptorFX.<ClassName>.<FunctionName>`, while variables as `RaptorFX.Variables.<VariableName>`, and enums as `<EnumName>.<EnumValue>`._

[*¹] refers to being exclusive to the mobile platform, or either one of them (i.e either on Android or iOS).

### CLI
The RaptorFX CLI is a tool to help scaffold and handle RaptorFX projects quickly and efficiently, it has several commands and flags listed below as part of the CLI:

[CLI Documentation/Specification scrapped/on-hold; new design coming with next RFC.] 

## Toolbox
Toolbox is a cross-platform on-the-fly compiler for RaptorFX Projects to scaffold or test projects anywhere. It will compile apps on the fly while running them in a testing WebView which shares all the capabilities a normal RaptorFX App would, except for a few functions operating differently - such as `RaptorFX.Window.exit()`, which will exit the currently running app (instead of closing the entire toolbox app). 

