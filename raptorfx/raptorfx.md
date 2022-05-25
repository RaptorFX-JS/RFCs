# RaptorFX
![RaptorFX Logo - by ArathainFarqou and LePichu](https://cdn.discordapp.com/attachments/890845937243684886/921414193423466536/rfx_text_logo.png)
## Aim 
RaptorFX aims to centralise app development into one codebase while targetting multiple platforms at once, we will make use of web technologies to make it easier for anyone to dive in and start developing. People may even contribute to the main codebase of RaptorFX if they wish to improve it in any way, shape, or form. 

## Core

### API 
RaptorFX while shipping a Deno instance, will also ship its own set of functions like Electron, Tauri or Neutralino to make it easier to work across platforms with ease. We also aim to blend in with existing Web APIs and Standards. The following is a list of classes, functions, enums, and related, all of which come under the namespace of `RaptorFX`, with their description on what they do: 

#### Classes
- `Clipboard`: Relates to user's clipboard (store of keyboard copy items).
- `Notifications`: Manage notifications; push, group, pop.
- `Window`: Window-related activites like Maximise, Minimize, and Position.
- `System`: System related class which returns Architecture, OS, etc.

#### Interfaces
- `NotificationData`: 
-- `title (string)`: Main Title of notification.
-- `description (string)`: Description/Secondary Title of notification.
-- `icon (url)`: URL of icon to show in notification.

- `PositionData`:
-- `x (number)`: Starting cordinate in X-Axis of Window.
-- `y (number)`: Starting cordinate in Y-Axis of Window.
-- `height (number)`: Height of Window.
-- `width (number)`: Width of Window.

#### Functions 
- `Clipboard`: 
-- `copy (content: string) [void]`: Push copy content to user's clipboard. 
-- `cut (content: string) [void]`: Push cut content to user's clipboard.
-- `read () [string]`: Reads and returns content from the user's clipboard.

- `Notifications`:
-- `build (object:  NotificationData) [void]`: Takes in `NotificationData`, to create pushable/referencable notification block.
-- `push (data: NotificationData, mode: NotificationMode) [Promise]`: Pushes the notification built from data, with configuration and channel to send to.
-- `createToast (data: String, length: ToastLength) [void]`: Creates a Toast with data provided. [*¹]

- `Window`:
-- `maximize () [void]`: Maximizes the context window.
-- `minimize () [void]`: Minimizes the context Window.
-- `exit (code: number) [void]`: Completely exits the context window with an exit code.
-- `position (cords: PositionData) [PositionData]`: If given arguments, changes the position of the window, without any arguments, the current cordinates of window are returned as `PositionData`.

- `System`:
-- `arch () [string]`: Returns the architecture (`x86`, `arm64` etc.) of system as a string.
-- `os () [string]`: Returns the operating system (`windows_11`, `android_12` etc.) of system as string.

#### Variables
- `LocalStorage`: Points to path to internal app storage, which could mean a folder under `$USER\LocalAppData\YourApp\` (on Windows), or `data/data/YourApp` (on Android).
- `ExternalStorage`: Points to root of file system, usually `/mounted/0/` (on Android), or any absolute/relative path on other operating systems like Windows or Linux.

#### Enums
- `ToastLength`: Accepts `SHORT` and `LONG`, self-describing length of Toast displayed on screen. [*¹]
- `NotificationMode`: Accepts `SINGLE` and `GROUP`, where `SINGLE` creates a new notification for each push, while `GROUP` collects it into a single grouped notification. 

_Classes and Interfaces are available as `RaptorFX.<Name>`, functions as `RaptorFX.<ClassName>.<FunctionName>`, while variables as `RaptorFX.Variables.<VariableName>`, and enums as `RaptorFX.Enums.<EnumName>`._

[*¹] refers to being exclusive to the mobile platform or either one of them, i.e either on Android or iOS.

### CLI
The RaptorFX CLI is a tool to helps scaffhold and handle RaptorFX projects quickly and efficiently, it has several commands and flags listed below as part of the CLI:

[CLI Documentation/Specification on scrapped/on-hold; next design coming with next RFC.] 

## Toolbox
Toolbox is a cross-platform on-the-fly compiler for RaptorFX Projects to scaffhold or test projects anywhere at anytime. They will can compile apps on the fly while running them in a testing WebView which does share all the capabilities a normal RaptorFX App would, exceptions being a few functions will function differently, like `RaptorFX.Window.exit()` will now exit the current running app, instead of closing the entire toolbox app. 
