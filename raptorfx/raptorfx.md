# RaptorFX
![RaptorFX Logo - by ArathainFarqou and LePichu](https://cdn.discordapp.com/attachments/890845937243684886/921414193423466536/rfx_text_logo.png)
## Aim 
RaptorFX aims to centralise app development into one codebase while targetting multiple platforms at once, we will make use of web technologies to make it easier for anyone to dive in and start developing. People may even contribute to the main codebase of RaptorFX if they wish to improve it in any way, shape, or form. 

## Core
### Standard Library
RaptorFX while shipping a Deno instance, will also ship its own set of functions like Electron, Tauri or Neutralino to make it easier to work across platforms with ease. In addition to the standard library, we will provide platform exclusive feature plugins that only work either on mobile or desktop, if the said functionality work on both, we will ship it in standard library instead. The following is a list of functions with their description on what they do: 

#### Global API
- `loadURL`: Loads the webpage from the provided URL onto current WebView.
- `manageWindowMetadata`: Manages metadata of the current WebView window like Min/Max Sizes of Height/Width, is the Window Fullscreen, is it frameless, what is the window icon etc.
- `injectCustomCSS`: Injects a CSS File onto current WebView.
- `getSystemTheme`: Returns the System's current theme as either `LIGHT` or `DARK` depending on theme type respectively.
- `getOS`: Returns the current operating system of the machine being used, possible return values are `WINDOWS`, `MACOS`, `LINUX`, `ANDROID` and `IOS`.
-  `getSystemLanguage`: Returns the language code (ex: `fr-FR`, `en_US`etc)  of the current default system language set for use.
- `setWindowTitle`: Sets the title of the current window the JS is being executed from.
- `setWindowIcon`: Sets the icon of the current window the JS is being executed from.
- `setWindowBarColor`: Set the color of the window accent color (on Windows 10+) and the status bar (on Android and iOS).
- `exitWindow`: Destroys the current WebView in the window and proceeds to close the window. 
- `nativeDialogueBuilder`: A Class to make customizable native dialogue boxes across platforms, these dialogues can include Icons, Texts, Buttons, Scrollbars, and Input fields.
- `nativeNotificationBuilder`: A Class to deploy native notifications which can hold text-based descriptions and titles and images as notification icons.
	
#### Desktop-Exclusive
- `createNewWebView`: Creates a new WebView Window for use, similar to `createWindow()` from Electron.

#### Mobile Exclusive
- `showHudToast`: Shows a toast with provided text.
- `nativeSnackbarBuilder`: A Class to make Android Snackbars.

### CLI
The RaptorFX CLI is a tool to helps scaffhold and handle RaptorFX projects quickly and efficiently, it has several (sub)commands and flags listed below as part of the CLI:
#### Subcommands:
- `init`: Initializes an empty RaptorFX project with a git repository in it, and recreates every file and folder seen in `RaptorFX/Example-App` repository.	
- `build`: Builds the final app for the platforms listed in the local manifest file. 
- `debug`: Launches the debug client with the current app if there is any in the workspace folder.
- `version`: Prints out the version of RaptorFX CLI you are using alongside if there are any future versions available.
- `upgrade`: Upgrades the CLI and restores project templates if they are missing. 

#### Flags
- `-h, --help`: Provides syntax for a sub-command or a flag.
- `-m, --mode`:	Release mode of how to build the app, possible values are `debug` and `release.`
- `-f, --force`: Executes a command even if warnings were issue prior.

### Debug Client (RaptorFX Toolbox)
Debug Clients are on-the-fly compilers for RaptorFX Projects to scaffhold or test packages anywhere at anytime. They will can compile apps on the fly while running them in a testing WebView which does share all the capabilities a normal RaptorFX App would, exceptions being a few functions will function differently, like `RaptorFX.exitWindow()` will now exit the current running app, instead of closing the entire toolbox app. 
