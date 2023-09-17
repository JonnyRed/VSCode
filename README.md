
* 2023/9/5 reset VScode:
* 2023/9/15 Added Jupyter VScode documentation
* 2023/9/16 Added CSpell VScode documentation
* 2023/9/16 Reinstalled CSpell VScode documentation as stopped working


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
and [Cytron Maker board][] (Pico based). Most of the 
[Grove Pico Starter Kit][] can be performed on the [Cytron Maker board][]. 
Documentation for Starter Kit can be found at  
[Grove Pico Starter Kit][]. In essence the Grove Pico header is replaced 
by the Cytron Maker.

The extension [Pico-Go][] enables the Pico to be managed from vscode.
The extension [Pico-Go][] required some effort to install because of 
misunderstanding of the process.

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

# Pylance

**[Pylance][]** is a language server extension for **Visual Studio Code 
(VS Code)** that provides 
**[fast and feature-rich language support for Python][]**.
It works alongside the Python extension in VS Code to enhance the Python 
development experience. Pylance is powered by **Pyright**, Microsoft's 
static type checking tool, which enables it to provide performant 
language support. By leveraging Pyright, Pylance enhances the Python 
IntelliSense experience by offering rich type information, helping 
developers write better code more efficiently

Some of the key features provided by Pylance include:
- **Docstrings**: Pylance offers signature help with type information, 
parameter suggestions, and code completion.
- **Auto-imports**: It provides automatic import suggestions and actions 
to add or remove import statements
- **Code error and warning reporting**: Pylance reports code errors and 
warnings as you type, helping you catch potential issues early on¹.
- **Code outline and navigation**: It offers a code outline for easy 
navigation within your Python codebase.
- **Type checking mode**: Pylance supports different levels of type 
checking analysis, allowing you to choose the desired level of type 
checking.
- **Native multi-root workspace support**: It seamlessly integrates 
with multi-root workspaces in VS Code.
- **IntelliCode compatibility**: Pylance is compatible with IntelliCode, 
which provides AI-assisted code completions based on your coding patterns 
and practices.

To get started with Pylance, you can install the Python extension from 
the VS Code marketplace. Pylance will be installed as an optional 
extension alongside it. Once you open a Python (.py) file, the Pylance 
extension will activate automatically.

Please note that Pylance is specifically designed for Python development 
in VS Code and may not be applicable to other programming languages or 
IDEs.

----

```python.analysis.typeCheckingMode```

* Used to specify the level of type checking analysis performed.
    * Default: off.
    * Note that the default value is set to "basic" when using VS Code 
    Insiders, and to "off" otherwise.

* Available values:
    * off: No type checking analysis is conducted; unresolved 
    imports/variables diagnostics are produced
    * basic: Non-type checking-related rules (all rules in off) + basic type 
    checking rules
    * strict: All type checking rules at the highest severity of error 
    (includes all rules in off and basic categories)

* ```"python.analysis.typeCheckingMode": "basic"```

----


```python.analysis.diagnosticSeverityOverrides```

* Used to allow a user to override the severity levels for individual 
diagnostics should they desire.
* Accepted severity values:
    * error (red squiggle)
    * warning (yellow squiggle)
    * information (blue squiggle)
    * none (disables the rule)

* [Available diagnostic severity overrides rules][] 


    ```
    "python.analysis.diagnosticSeverityOverrides": {
        "reportGeneralTypeIssues": "warning"
    }

    ```

# Jupyter

Jupyter description in VScode is described well in 
[VScode Jupyter documentation][]. 
Custom __notebook diffing__ is especially interesting

# cSpell
Add words to the dictionary by right clicking on the word and selecting 
`Add to dictionary` and `Add to workspace dictionary`   

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
[Available diagnostic severity overrides rules]: https://github.com/microsoft/pylance-release/blob/main/DIAGNOSTIC_SEVERITY_RULES.md
[Pylance]: https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance
[fast and feature-rich language support for Python]: https://devblogs.microsoft.com/python/announcing-pylance-fast-feature-rich-language-support-for-python-in-visual-studio-code/

