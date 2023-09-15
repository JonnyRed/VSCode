
* 2023/9/5 reset VScode:
* 2023/9/15 Added Jupyter VScode documentation

# Visual Source Documentation
* [Documentation for Visual Studio Code][]
* [User and Workspace Settings][]


# Tutorials
* Very good youtube tutorial on [setting up][Shaffer tutorial] 
vscode by  [Corey Schafer][]

# VScode setup

1. Did not [delete VScode][Delete VSCode and settings].
1.  To remove all user data after uninstalling VS Code, delete the folders 
    * %APPDATA%\Code (%APPDATA% is `C:\Users\John\AppData\Roaming`)
    * %USERPROFILE%\.vscode  (%USERPROFILE%\ is `C:\Users\John`)
1. Sync settings restores all setting from github turn this off if you do 
not want this to happen

# Pico and Pico-Go

A lot of electronics is performed using the [Pico board][]
and [Cytron Maker board][] (Pico based). Most of the [Grove Pico Starter Kit][] can be performed on the [Cytron Maker board][]. Documentation for Starter Kit can be found at  [Grove Pico Starter Kit][]. In essence the Grove Pico header is replaced by the Cytron Maker.

The extension [Pico-Go][] enables the Pico to be managed from vscode.
The extension [Pico-Go][] required some effort to install because of misunderstanding of the process.

* The linking LED did not work until
```json
"terminal.integrated.env.windows": {
        "PYTHONPATH": "${workspaceFolder}\\.;${workspaceFolder}\\test"
    }
```
was added to `settings.json`

* Use of the FTP server in [Pico-Go][] is essential to upload Micropython code to the Pico.
* It seems much easier to develop code on vscode and executed it through [Thonny][]

# Useful Global settings

Use json instead of the standard UI

```json
	// Determines which settings editor to use by default.
	//  - ui: Use the settings UI editor.
	//  - json: Use the JSON file editor.
	"workbench.settings.editor": "json",
```

A list of all the default settings can be opened through the settings option.
```json
// Controls whether opening settings also opens an editor showing all default settings.
	"workbench.settings.openDefaultSettings": true,
```

```json
// Controls which editor is shown at startup, if none are restored from the previous session.
	//  - none: Start without an editor.
	//  - welcomePage: Open the Welcome page, with content to aid in getting started with VS Code and extensions.
	//  - readme: Open the README when opening a folder that contains one, fallback to 'welcomePage' otherwise. Note: This is only observed as a global configuration, it will be ignored if set in a workspace or folder configuration.
	//  - newUntitledFile: Open a new untitled file (only applies when opening an empty window).
	//  - welcomePageInEmptyWorkbench: Open the Welcome page when opening an empty workbench.
	"workbench.startupEditor": "none",
```

# Tips and Tricks

[Visual Studio Code Tips and Tricks][]

[Visual Studio Code Tips and Tricks]:https://code.visualstudio.com/docs/getstarted/tips-and-tricks#_basics

# Settings

The set of of Visual Studio code proved a challenge. Here are the settings to enable the local source files to be accessible from VScode. The settings `"python.defaultInterpreterPath"` for python and `"terminal.integrated.env.windows"` are important to execute python and pico correctly.

From default settings:

```json
// Object with environment variables that will be added to the VS Code process to be used by the terminal on Windows. Set to `null` to delete the environment variable.
	"terminal.integrated.env.windows": {},
```

The following is `settings.json`

```json
{
    "editor.formatOnSave": true,
    "python.defaultInterpreterPath": "D:\\Users\\John\\Anaconda3\\envs\\3.7\\python.exe",
    "python.testing.unittestArgs": [
        "-v",
        "-s",
        "./test",
        "-p",
        "test*.py"
    ],
    "python.analysis.typeshedPaths": [
        ".vscode\\Pico-Stub"
    ],
    "python.languageServer": "Pylance",
    "python.analysis.typeCheckingMode": "basic",
    "python.analysis.extraPaths": [
        ".vscode\\Pico-Stub\\stubs"
    ],
    "terminal.integrated.env.windows": {
        "PYTHONPATH": "${workspaceFolder};${workspaceFolder}/test"
    }
}
```

# Jupyter

Jupyter description in VScode is described well in [VScode Jupyter documentation][]. Custom notebook diffing is especial interesting


# Micropython source
The `.env` can be used to specify the origin of source files is as follows

```json
WORKSPACE_FOLDER=D:/Users/John/Documents/Computers/RaspberryPi/MicroPython
PYTHONPATH=${workspaceFolder};${WORKSPACE_FOLDER}/test
```
# Pico source
The `.env` is as follows

```json
WORKSPACE_FOLDER=D:/Users/John/Documents/Computers/RaspberryPi/pico_project
PYTHONPATH=${WORKSPACE_FOLDER};${WORKSPACE_FOLDER}/test
```

[Shaffer tutorial]: https://youtu.be/-nh9rCzPJ20
[Corey Schafer]:https://www.youtube.com/channel/UCCezIgC97PvUuR4_gbFUs5g
[User and Workspace Settings]:https://code.visualstudio.com/docs/getstarted/settings
[Documentation for Visual Studio Code]:https://code.visualstudio.com/docs
[Thonny]:https://thonny.org/
[Pico-Go]:http://pico-go.net/docs/start/quick/
[pico Grove wiki]:https://wiki.seeedstudio.com/Grove_Shield_for_Pi_Pico_V1.0/
[Grove Pico Starter Kit]:https://wiki.seeedstudio.com/Grove_Shield_for_Pi_Pico_V1.0/
[Cytron Maker board]:https://docs.google.com/document/d/1JoHsZk5IipQPCLXWbZYpDKjGlnkyACOJ1taUrKVsRg8/edit
[Pico board]:https://www.raspberrypi.org/documentation/rp2040/getting-started/#rp2040-boards
[Delete VSCode and settings]: https://code.visualstudio.com/docs/setup/uninstall
[VScode Jupyter documentation]: https://code.visualstudio.com/docs/datascience/jupyter-notebooks
