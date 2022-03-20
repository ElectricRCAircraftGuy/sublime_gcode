[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FElectricRCAircraftGuy%2Fsublime_gcode&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=views+%28today+%2F+todal%29&edge_flat=false)](https://hits.seeyoufarm.com)

[>> Sponsor Me on GitHub <<](https://github.com/sponsors/ElectricRCAircraftGuy)

Gabriel Staples


# Table of Contents
<details>
<summary><b>(click to expand)</b></summary>
<!-- MarkdownTOC -->

1. [sublime_gcode](#sublime_gcode)
1. [Installation](#installation)
    1. [1. Package Control](#NOT YET FUNCTIONAL; use manual method below for now)
    1. [2. Manual installation](#2-manual-installation)
1. [Developer Notes](#developer-notes)
    1. [References:](#references)
    1. [Misc. Tips & Tricks](#misc-tips--tricks)
    1. [Sublime Text packages and syntax highlighting--how it all works](#sublime-text-packages-and-syntax-highlighting--how-it-all-works)

<!-- /MarkdownTOC -->
</details>


<a id="sublime_gcode"></a>
# sublime_gcode
gcode (g-code) syntax highlighting for the Sublime Text editor; useful for viewing or editing CNC or 3D printer gcode files, including those from the [Ultimaker Cura](https://ultimaker.com/software/ultimaker-cura) slicer, [PrusaSlicer](https://www.prusa3d.com/page/prusaslicer_424/), or [Slic3r](https://github.com/slic3r/Slic3r), for instance. 

[todo: add screenshot of the syntax highlighting here]


**Inspired by these two projects:**
1. [gcode-syntax-highlighting](https://github.com/themachinist/gcode-syntax-highlighting), by @themachinist.
    1. my fork of it: https://github.com/ElectricRCAircraftGuy/gcode-syntax-highlighting
1. The [zip file version by @digex, here](https://github.com/themachinist/gcode-syntax-highlighting/issues/2#issuecomment-106274142).
    1. See my [full installation instructions and notes on it here](https://github.com/themachinist/gcode-syntax-highlighting/issues/2#issuecomment-1073127156).


<a id="installation"></a>
# Installation

<a id="NOT YET FUNCTIONAL; use manual method below for now"></a>
## 1. Package Control [NOT YET FUNCTIONAL; use manual method below for now]

Open the Command Palette via `Tools` --> `Command Palette...`, _or_ by pressing <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>. Then, search for `install package`, and click on `Package Control: Install Package`. Search for "gcode", and install the package by that name. `gcode` is now available as one of the syntax highlighting options. 


<a id="2-manual-installation"></a>
## 2. Manual installation

In Sublime Text, find the path to your `Packages` folder by clicking `Preferences` --> `Browse Packages...`. This will open up your GUI file manager to the path where Sublime Text packages are stored. For me on Linux Ubuntu 20.04, that's `/home/gabriel/.config/sublime-text-3/Packages` (even though I am running Sublime Text 4). 

Now, extract this package to that folder.

**Option 1: the GUI way:** click the green "Code" button above --> "Download ZIP" --> save the zip file, extract it to your `Packages` path above, and rename it to `gcode`. 

**OR Option 2: the command-line way:** 
```bash
# cd to the Packages dir
cd path/to/Packages
# clone the repo
git clone https://github.com/ElectricRCAircraftGuy/sublime_gcode.git
# rename the repo dir to "gcode"
mv sublime_gcode gcode
```

That's it! It's now instantly available in your syntax highlighting menu.


<a id="developer-notes"></a>
# Developer Notes

If you are a regular user, you can stop here. These notes are for myself, and for other developers who want to learn how to make new Sublime Text packages, including syntax highlighting packages, or who want to edit the syntax highlighting of this or other packages, or who want to learn what I learned in order to contribute to this repo.

_Tested in Sublime Text 4 (build 4126) on Linux Ubuntu 20.04._



<a id="references"></a>
## References:
1. https://en.wikipedia.org/wiki/G-code
1. `.tmLanguage` and `.YAML-tmLanguage` files are apparently some sort of ubiquitous [TextMate](https://en.wikipedia.org/wiki/TextMate)-inspired language grammar files used for specifying syntax highlighting rules. 
1. Marlin g-code (for 3D printers) official reference pages: https://marlinfw.org/meta/gcode/
1. Sublime Text pages:
    1. Syntax Definitions: http://www.sublimetext.com/docs/syntax.html
    1. https://www.sublimetext.com/docs/syntax.html - explains how `.sublime-syntax` files are built and work.
1. Package Control: 
    1. \*\*\*\*\*Customizing Packages: https://packagecontrol.io/docs/customizing_packages
    1. \*\*\*\*\*Submitting a [new] Package: https://packagecontrol.io/docs/submitting_a_package
1. \*\*\*\*\*TextMate language grammars documentation: https://macromates.com/manual/en/language_grammars; ex:
    1. `support.variable`, `comment.line`, `markup.bold`, `support.function`, etc.
1. http://ilkinulas.github.io/programming/2016/02/05/sublime-text-syntax-highlighting.html - showed me that editing Monokai.tmTheme with your scope names and formatting is how you modify formatting for your custom syntax highlighting scopes. 
    1. NB: I later discovered on my own that I should NOT modify the Monokai color theme directly (since it now comes in a compressed location anyway, which location is intended NOT to be modified directly--see [my answer here](https://stackoverflow.com/a/71261397/4561887) and [this comment here](https://stackoverflow.com/questions/71261218/where-is-the-default-settings-file-which-stores-thing-such-as-font-size-loca/71261397#comment125983189_71261397)), but rather I should go to `Preferences` --> `Customize Color Scheme` and then edit the user settings in the right-hand side of the JSON file that comes by adding new dictionary entries for custom formatting under the `rules` list of dicts.
1. https://github.com/va9iff/SublimeNotePad - **incredibly** simple example of a package plugin in Sublime Text, with Python code to interact with the Sublime Text GUI and menus and things! See its request to be added to Package Control here: https://github.com/wbond/package_control_channel/pull/8481.
1. \*\*\*\*\*Scope namespacing (my comments about it) for syntax highlighters in Sublime Text: https://github.com/wbond/package_control_channel/pull/8454#issuecomment-1073181257
1. See my [full installation instructions and notes on the gcode syntax highlighting by @digex here](https://github.com/themachinist/gcode-syntax-highlighting/issues/2#issuecomment-1073127156).


<a id="misc-tips--tricks"></a>
## Misc. Tips & Tricks
1. To have Sublime Text **auto-convert a Textmate `.tmLanguage` file into a `.sublime-syntax` file** for you, open up the `.tmLanguage` file in Sublime Text, then go to `Tools` --> `Developer` --> `"New Syntax from *.tmLanguage..."`. A file named `*.sublime-syntax` will be created and opened in Sublime Text, but you'll need to manually choose to save it somewhere if you want to keep it.
1. To **check a syntax highlighting scope of a particular place in a source code file**, in order to check to see if your syntax highlighting is working, or to see what scope a certain color and formatting come from for a syntax highlighting you like, place your cursor in the code where you want to check, then go to `Tools` --> `Developer` --> `Show Scope Name`. Click the "Copy" link in the little box that pops up over the source code if you'd like to copy that scope name.
1. To **modify and test changes to this package locally**, in case you'd like to change it or contribute to it, follow the "manual installation" instructions above. If you have already installed it via Package Control, then what is in your `/home/$USERNAME/.config/sublime-text-3/Packages/gcode` folder will _override_ what is in your `/home/gabriel/.config/sublime-text-3/Installed Packages/gcode.sublime-package` zip file which Package Control installed, so long as the folder and file names are the same. 


<a id="sublime-text-packages-and-syntax-highlighting--how-it-all-works"></a>
## Sublime Text packages and syntax highlighting--how it all works

todo
