[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FElectricRCAircraftGuy%2Fsublime_gcode&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=views+%28today+%2F+todal%29&edge_flat=false)](https://hits.seeyoufarm.com)

[>> Sponsor Me on GitHub <<](https://github.com/sponsors/ElectricRCAircraftGuy)

Gabriel Staples



# Table of Contents
<details>
<summary><b>(click to expand)</b></summary>
<!-- MarkdownTOC -->

1. [sublime_gcode](#sublime_gcode)
    1. [Status: done! It works!](#status-done-it-works)
    1. [Description](#description)
        1. [G-code formats, "flavors", and standards:](#g-code-formats-flavors-and-standards)
            1. [Standards:](#standards)
            1. [G-code "Flavors"](#g-code-flavors)
    1. [Inspired by these two projects:](#inspired-by-these-two-projects)
1. [Installation](#installation)
    1. [1. Package Control](#1-package-control)
    1. [2. Manual installation](#2-manual-installation)
1. [Issues](#issues)
1. [Developer Notes & Package Development Tutorial](#developer-notes--package-development-tutorial)
    1. [References:](#references)
    1. [Sublime Text packages and syntax highlighting--how it all works](#sublime-text-packages-and-syntax-highlighting--how-it-all-works)
        1. [1. Sublime Text packages](#1-sublime-text-packages)
        1. [2. Syntax highlighting](#2-syntax-highlighting)
            1. [Multiple syntax highlighting definitions in one package](#multiple-syntax-highlighting-definitions-in-one-package)
            1. [_`scope` --> Color Scheme mapping:_ How do syntax highlighting `scope` values map to actual syntax highlighting colors and formats?](#scope----color-scheme-mapping-how-do-syntax-highlighting-scope-values-map-to-actual-syntax-highlighting-colors-and-formats)
                1. [`scope` hierarchy](#scope-hierarchy)
                1. [Choosing `scope` names for your syntax definition file](#choosing-scope-names-for-your-syntax-definition-file)
                1. [Adding a unique subscope](#adding-a-unique-subscope)
            1. [To _check the syntax highlighting scope_ of a particular place in a source code file...](#to-check-the-syntax-highlighting-scope-of-a-particular-place-in-a-source-code-file)
            1. [Choosing scopes with desired color and formatting](#choosing-scopes-with-desired-color-and-formatting)
            1. [To _modify and test changes to this package locally_...](#to-_modify-and-test-changes-to-this-package-locally_)

<!-- /MarkdownTOC -->
</details>



<a id="sublime_gcode"></a>
# sublime_gcode


<a id="status-done-it-works"></a>
## Status: done! It works!

This is the PR that got this package into Sublime Package Control: https://github.com/wbond/package_control_channel/pull/8501. 

Here is this package on the Package Control website: https://packagecontrol.io/packages/gcode. As of its release into Package Control on 7 Apr. 2022, the existing number of downloads for the package were actually all for the package this one replaces, named [gcode-syntax-highlighting](https://github.com/themachinist/gcode-syntax-highlighting), by [@themachinist](https://github.com/themachinist). The existing number of downloads for that older package were (hover over the numbers on the package control website above to see them):
1. Total: 8453
2. Windows: 5113
3. Mac: 2107
4. Linux: 1233

Therefore, only numbers _beyond these counts_ are the number of downloads of this new `gcode` package provided by this repo.


<a id="description"></a>
## Description
`gcode` (g-code) syntax highlighting for the Sublime Text editor; useful for viewing or editing CNC or 3D printer gcode files, including those from the [Ultimaker Cura](https://ultimaker.com/software/ultimaker-cura) slicer, [PrusaSlicer](https://www.prusa3d.com/page/prusaslicer_424/), or [Slic3r](https://github.com/slic3r/Slic3r), for instance. 


Screenshots of Sublime Text 4 with Color Scheme `Monokai` and `gcode` syntax highlighter:

<p align="center" width="100%">
    <img width="42%" src="screenshots/small.jpg">
    <img width="56%" src="screenshots/gcode_in_menu.jpg">
</p>

![screenshots of gcode syntax highlighting](screenshots/side-by-side.jpg)

<a id="g-code-formats-flavors-and-standards"></a>
### G-code formats, "flavors", and standards:

This should be able to handle and highlight a variety of gcode formats and styles, including the following. If you have any problems, screenshot the syntax highlighting you see, [open a new Issue](https://github.com/ElectricRCAircraftGuy/sublime_gcode/issues), paste the screenshot _and_ a large chunk of the gcode for me to play with and test, _and_ links to any documentation pertaining to this flavor of gcode syntax, and explain what formatting or highlighting you would have _expected_ to see. The main reference for the following list is this: https://en.wikipedia.org/wiki/G-code.

<a id="standards"></a>
#### Standards:
1. RS-274
1. ISO 6983
1. DIN 66025
1. PN-73M-55256 and PN-93/M-55251

<a id="g-code-flavors"></a>
#### G-code "Flavors" 
(As shown from the drop-down menu for the Machine Settings in the [Cura 3D printer slicer software](https://en.wikipedia.org/wiki/Cura_(software))):

![image](https://user-images.githubusercontent.com/6842199/159841238-d71c1aff-6fba-42cc-92da-ace4b257bc84.png)

1. Marlin
1. Marlin (Volumetric)
1. RepRap
1. Ultimaker 2
1. Griffin
1. Makerbot
1. Bits from Bytes
1. Mach3
1. Repetier


<a id="inspired-by-these-two-projects"></a>
## Inspired by these two projects:
1. [gcode-syntax-highlighting](https://github.com/themachinist/gcode-syntax-highlighting), by [@themachinist](https://github.com/themachinist).
    1. my fork of it: https://github.com/ElectricRCAircraftGuy/gcode-syntax-highlighting
    1. The `gcode` syntax in my project is _strongly influenced by_ @themachinist's work above. I used his work as an example and starting point as I wrote and modified the regular expression `match` patterns and `scope`s. My work differs significantly enough, however, that I decided to make my repo from scratch rather than making it a fork of his repo.
1. The [zip file version by @digex, here](https://github.com/themachinist/gcode-syntax-highlighting/issues/2#issuecomment-106274142).
    1. See my [full installation instructions and notes on it here](https://github.com/themachinist/gcode-syntax-highlighting/issues/2#issuecomment-1073127156).
    1. The `gcode-alternate` syntax in my project is an _exact copy_ of @digex's work in the zip file above.


<a id="installation"></a>
# Installation

<a id="1-package-control"></a>
## 1. Package Control

Open the Command Palette via `Tools` --> `Command Palette...`, _or_ by pressing <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>. Then, search for `install package`, and click on `Package Control: Install Package`. Search for "gcode", and install the package by that name. `gcode` is now available as one of the syntax highlighting options. 

If you ever want to remove it, use <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> and then search for `Package Control: Remove Package`. Select it, and then search for `gcode`.

To list all installed packages, use <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> and then `Package Control: List Packages`.


<a id="2-manual-installation"></a>
## 2. Manual installation

In Sublime Text, find the path to your `Packages` folder by clicking `Preferences` --> `Browse Packages...`. This will open up your GUI file manager to the path where Sublime Text packages are stored. For me on Linux Ubuntu 20.04, that's `/home/gabriel/.config/sublime-text-3/Packages` (even though I am running Sublime Text **4**). 

Now, extract this package to that folder.

**Option 1: the GUI way:** click the green "Code" button above --> "Download ZIP" --> save the zip file, extract it to your `Packages` path above, and rename it to `gcode`. 

**OR Option 2 [what I prefer]: the command-line way:** 
```bash
# --------------
# Option 2.A: clone the repo directly into your "Packages" dir
# --------------

# cd to the Packages dir (change this path according to your Packages path above)
cd "$HOME/.config/sublime-text-3/Packages"
# clone the repo
git clone https://github.com/ElectricRCAircraftGuy/sublime_gcode.git
# rename the repo dir to "gcode"
mv sublime_gcode gcode

# --------------
# OR Option 2.B [what I prefer]: clone the repo into wherever you want, and then
# symlink it into your "Packages" dir
# --------------

# clone repo into ~/dev
mkdir -p ~/dev
cd ~/dev
git clone https://github.com/ElectricRCAircraftGuy/sublime_gcode.git
# now symlink it into your Packages dir
ln -si ~/dev/sublime_gcode ~/.config/sublime-text-3/Packages/gcode
```

That's it! The `gcode` entry is now instantly available in your syntax highlighting menu.



<a id="issues"></a>
# Issues

If anything doesn't work or look as expected with the the main `gcode` syntax highlighter, please open up an issue in this GitHub repo and I'll address it. That includes text that should be highlighted, but isn't, missing gcode file extensions, etc.



<a id="developer-notes--package-development-tutorial"></a>
# Developer Notes & Package Development Tutorial

If you are a regular user, you can stop here. These notes are for myself, and for other developers who want to learn how to make new Sublime Text packages, including syntax highlighting packages, or who want to edit the syntax highlighting of this or other packages, or who want to learn what I learned in order to contribute to this repo.

_Tested in Sublime Text 4 (build 4126) on Linux Ubuntu 20.04._


<a id="references"></a>
## References:

1. A ton of independent testing and experimenting on my own
1. https://en.wikipedia.org/wiki/G-code
1. `.tmLanguage` and `.YAML-tmLanguage` files are apparently some sort of ubiquitous [TextMate](https://en.wikipedia.org/wiki/TextMate)-inspired language grammar files used for specifying syntax highlighting rules. 
1. Marlin g-code (for 3D printers) official reference pages: https://marlinfw.org/meta/gcode/
1. Sublime Text pages:
    1. Syntax Definitions: https://www.sublimetext.com/docs/syntax.html - explains how `.sublime-syntax` files are built and work.
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
1. https://regex101.com/ - use this tool to build, check, and test your regular expressions to be used as syntax highlighting matching patterns.


<a id="sublime-text-packages-and-syntax-highlighting--how-it-all-works"></a>
## Sublime Text packages and syntax highlighting--how it all works

<a id="1-sublime-text-packages"></a>
### 1. Sublime Text packages

Any folder inside of your Sublime Text `Packages` folder (found via `Preferences` --> `Browse Packages...`) is automatically instantly loaded by Sublime Text as a "package". 

**Packages** installed by the `Package Control` package, however, come in two types:
1. **Packed**: most packages installed by Package Control are "packed" into a zip file named `packageName.sublime-package` and are located inside the `Installed Packages` dir which is at the same level as the `Packages` dir. 
    1. If you manually create a dir inside the `Packages` dir and name it `packageName` (to match the packed file above), then any files in it with the same name as those in the packed package will _override_ those in the packed package. See the "Overrides" section here: https://packagecontrol.io/docs/customizing_packages.
1. **Unpacked**: any package which is installed in the `Packages` dir is unpacked. 
    1. Developers can tell Package Control to unpack a package installed by Package Control by placing a file named `.no-sublime-package` at the root of their repo. See here: https://packagecontrol.io/docs/submitting_a_package. 
    1. Unpacked packages are required if they contain binary executables which need to be run by the system, for instance, as they apparently can't run from inside the packed zip file.

<a id="2-syntax-highlighting"></a>
### 2. Syntax highlighting

**Syntax highlighting packages** must contain a `*.tmLanguage` XML-format Textmate syntax highlighting definition file, OR a `*.sublime-syntax` YAML-format file. My personal testing shows that if you have _both_ types of files with the same syntax highlighting `name` value specified inside of them, then the `*.sublime-syntax` file takes precedence and is what Sublime Text uses. Note that Textmate files also come in a YAML-format variety named `*.YAML-tmLanguage`, but apparently (per my testing) this file does nothing for Sublime Text and is not recognized by Sublime Text. 

Note also that the name of the `*.tmLanguage` or `*.sublime-syntax` file _doesn't matter!_ The `name` field specified _inside_ that file is what matters! So, if you have a file named `whatever.sublime-syntax`, and it contains a `name` field inside of it set to `gcode`, then what you will see in the syntax highlighting selection menu is `gcode`. 

To have Sublime Text **auto-convert a Textmate `.tmLanguage` file into a `.sublime-syntax` file** for you, open up the `.tmLanguage` file in Sublime Text, then go to `Tools` --> `Developer` --> `"New Syntax from *.tmLanguage..."`. A file named `*.sublime-syntax` will be created and opened in Sublime Text, but you'll need to manually choose to save it somewhere if you want to keep it. This auto-conversion doesn't always work, however, and I can't pinpoint why it doesn't do anything sometimes. You can also go to `Tools` --> `Developer` --> `New Syntax...` to create a generic example `.sublime-syntax` file.

I recommend you use `.sublime-syntax` files to specify syntax highlighting. You can read official Sublime Text documentation about them here: https://www.sublimetext.com/docs/syntax.html. 

<a id="multiple-syntax-highlighting-definitions-in-one-package"></a>
#### Multiple syntax highlighting definitions in one package

If a single package contains only one syntax highlighting definition file (of the file format `*.tmLanguage` _or_ `*.sublime-syntax`), then the `name` value inside that file is what will show up in your syntax highlighting menus (again, the filename itself doesn't matter). However, if you place *multiple* syntax highlighting definition files inside the same package, then the syntax highlighting menu will place the _package directory name_ in the menu, with a little black arrow to the right of it, and if you hover on this menu entry it will expand to show the `name` field values of each file in the package. Example: this menu entry would be generated by a package directory named `Markdown`, containing two syntax highlighting definition files, one with its `name` field set to `Markdown` and the other with its `name` field set to `MultiMarkdown`:

[![image](https://user-images.githubusercontent.com/6842199/159187804-c2ec4820-0b39-4bbb-9a57-c0adc3f0da1e.png)](https://user-images.githubusercontent.com/6842199/159187804-c2ec4820-0b39-4bbb-9a57-c0adc3f0da1e.png)

To temporarily **_disable_ a syntax highlighting definition file**, simply rename it so it no longer has the `.tmLanguage` or `.sublime-syntax` extension. I like to just add `.disabled` to the very end to make it clear what I am doing. Example: rename `whatever.sublime-syntax` to `whatever.sublime-syntax.disabled`.

<a id="scope----color-scheme-mapping-how-do-syntax-highlighting-scope-values-map-to-actual-syntax-highlighting-colors-and-formats"></a>
#### _`scope` --> Color Scheme mapping:_ How do syntax highlighting `scope` values map to actual syntax highlighting colors and formats?

The highest-level `scope` entry in a `.sublime-syntax` file can be *anything* you want. It appears to have no bearing on the mapping to the formatting or colors. So, `gcode` below can be anything.

The `scope` entries which are associated with `match` regex expressions, however are important! They must match entries for your color theme!

Consider this `example.sublime-syntax` file:

```yaml
%YAML 1.2
---
# http://www.sublimetext.com/docs/syntax.html
# GS: https://macromates.com/manual/en/language_grammars
name: gcode
file_extensions:
  - eia
  - nc
  - ngc
  - prg
  - mpf
  - gcode
scope: source.iso6983
contexts:
  main:
    - match: G\d+
      comment: g commands
      scope: support.function
    - match: M\d+
      comment: m commands
      scope: support.constant
```

The `gcode` `name` entry can be _anything_. The `support.constant` scope name, however, _must match a `scope` entry in your color scheme file_ in order for it to receive any formatting!

In Sublime Text, go to `Preferences` --> `Customize Color Scheme` to see your color theme. Mine is set to `Monokai`, so it opens up this Sublime Text Color Scheme JSON file:

[![image](https://user-images.githubusercontent.com/6842199/159188792-92965883-f29e-42ed-b242-41dfc7a445e3.png)](https://user-images.githubusercontent.com/6842199/159188792-92965883-f29e-42ed-b242-41dfc7a445e3.png)

The left side contains all default definitions and values. You can't edit this. The right side contains your _custom overrides and additions_. You _can_ edit this. In the left-hand side you can see I have searched for `support.constant`, and it is set to `"var(blue)"` color. `blue` is defined in a `variables` list at the top of this JSON file, as this: `"blue": "hsl(190, 81%, 67%)",`. **So, the syntax definition file above says that if any string in a source file matches regular expression `M\d+`, then it will be assigned the `scope` name `support.constant`, and my Monokai color scheme has a definition for the `scope` `support.constant` which formats its foreground as blue!** That's how this mapping works!

<a id="scope-hierarchy"></a>
##### `scope` hierarchy

If my color scheme JSON file does NOT have any `scope` entry for `support.constant`, then it will go up one level in the scope namespace and look for an entry for `support`. If a `support` scope entry exists, then my `support.constant` will receive the formatting from the `support` scope. If no entry for `scope` `support` exists, then the text assigned to scope `support.constant` will get _no special formatting applied._ If that is the case, then you can either 1. change the `scope` name in the syntax highlighting definition file, or 2. add an entry to the user-side (right-hand side) of your color scheme in `Preferences` --> `Customize Color Scheme`.

<a id="choosing-scope-names-for-your-syntax-definition-file"></a>
##### Choosing `scope` names for your syntax definition file

TextMate describes recommended `scope` naming conventions in section **"12.4 Naming Conventions"** of their manual here: https://macromates.com/manual/en/language_grammars. Sub-bullets should be scoped with a dot (`.`), so when you see this in the document:

> - comment
>     - line
>     - block

...it means that you can have a scope named `comment`, `comment.line`, or `comment.block`. For the `support` scope, you'll see:

> - support
>     - function
>     - class
>     - type
>     - constant

etc.

It is a good idea to use the naming conventions established by TextMate as a starting point, as they seem to be a sort of "industry standard". **However, what matters even more are the `scope` names in your color scheme file,** so ensure whatever scope names you use, they are in your color scheme file (`Preferences` --> `Customize Color Scheme`), as that's even more important! **Choosing `scope` names from your color scheme file is the best thing to do.**

See the section below titled ["Choosing scopes with desired color and formatting"](#choosing-scopes-with-desired-color-and-formatting) for more tips and techniques.

<a id="adding-a-unique-subscope"></a>
##### Adding a unique subscope

In the example above, using a `scope` of `support.constant` works because that scope has a definition inside my color scheme. However, it is **recommended to add a unique subscope to the end of this!** By common convention, you should use the `name` value of this entire syntax highlighting definition file as the subscope, and therefore add `.gcode` to the end of all of your scopes to make them unique. This results in the following changes: `support.function` changes to `support.function.gcode`, and `support.constant` changes to `support.constant.gcode`. 

The advantage of this is now users of your syntax highlighting package, and other package maintainers, can customize colors and formatting to affect _just scopes for your package_, if they so wish. They can override the `support.constant.gcode` scope in their user settings for the color scheme with this rule, for instance:

```jsonc
// Documentation at https://www.sublimetext.com/docs/color_schemes.html
{
    "variables":
    {
    },
    "globals":
    {
    },
    "rules":
    [
        {
            "name": "gcode Library constant",
            "scope": "support.constant.gcode",
            "foreground": "var(grey)"
        }
    ]
}
```

If they do *not* override this scope, however, there is no problem! Scope `support.constant.gcode` may have no matching `scope` entry in the color scheme, but `support.constant` will, so the default `support.constant` formatting will be applied to your `support.constant.gcode` scope!

For an additional explanation of and example of this concept above, see [my comment on this PR here](https://github.com/wbond/package_control_channel/pull/8454#issuecomment-1073181257).

<a id="to-check-the-syntax-highlighting-scope-of-a-particular-place-in-a-source-code-file"></a>
#### To _check the syntax highlighting scope_ of a particular place in a source code file...
...in order to check to see if your syntax highlighting is working, or to see what scope a certain color and formatting come from for a syntax highlighting you like, place your cursor in the code where you want to check, then go to `Tools` --> `Developer` --> `Show Scope Name`. Click the "Copy" link in the little box that pops up over the source code if you'd like to copy that scope name.

<a id="choosing-scopes-with-desired-color-and-formatting"></a>
#### Choosing scopes with desired color and formatting

Read the sections just above first, to get full context on what I'm doing here, and why/how it works. 

Once you are ready to **choose desired colors and formatting _for a new syntax and file type_,** the trick I like to do to find the right `scope` for the job (ie: formatting that I like and that makes sense) is this: 

1. Ensure you have your desired color scheme activated in Sublime Text: `Preferences` --> `Select Color Scheme...` --> choose a color scheme. I really like `Monokai` the best, which was the default in Sublime Text 3. I still use it in Sublime Text 4.
1. Open up a file type you are very familiar with in this color scheme, such as a `.c` C source file.
1. Find a color and format you like and which makes sense for the job. Ex: in gcode files, `G` and `M` commands are essentially functions, so, in a C source file I'd find a function call, such as `printf()`, which has the formatting I want for a `G` command, and I'd put my cursor on it.
1. Go to `Tools` --> `Developer` --> `Show Scope Name` to see the scope. This is the scope for a C `printf()` function _call_ (not definition):
    ```
    source.c++ meta.function.c++ meta.block.c++ meta.function-call.c++ support.function.C99.c
    ```
1. The part I care about is the end scope, which is `support.function.C99.c`. As described in the ["Adding a unique subscope"](#adding-a-unique-subscope) section above, the `.C99.c` subscope parts don't matter here to me. So, strip them off. That leaves us with the `support.function` scope. 
1. Open up your color scheme via `Preferences` --> `Customize Color Scheme` in order to search the color scheme for this scope to ensure it exists there. In the left-hand pane, I search for `support.function`. I find this entry:
    ```jsonc
    {
        "name": "Library function",
        "scope": "support.function, support.macro",
        "foreground": "var(blue)"
    },
    ```
    Notice the `foreground": "var(blue)"` formatting! That's where this scope for the C `printf()` function gets its formatting! If I like that formatting and want it for `G` commands in `gcode` files, I'll use the `support.function` scope for those `G` commands as well, giving it a unique subscope to ultimately be this scope: `support.function.gcode`. 
1. Done! That's one way to find and set a desired scope. 
1. Going further: function _definitions_, not calls, in C, have this scope:
    ```
    source.c++ meta.function.c++ meta.toc-list.full-identifier.c++ entity.name.function.c++
    ```
    The scope part I care about is at the far right: `entity.name.function.c++`. Strip off the `.c++` and I get `entity.name.function`. I search for that in the color scheme as described above, and it doesn't exist. _But_, `entity.name` _does_ exist! That means this is the scope which sets the formatting in this case. This entry in the color scheme file for Monokai is:
    ```jsonc
    {
        "name": "Entity name",
        "scope": "entity.name - (entity.name.filename | entity.name.section | entity.name.tag | entity.name.label)",
        "foreground": "var(yellow2)"
    },
    ```
    The `entity.name - (...)` part means: "apply this formatting to the `entity.name` scope, and all its subscopes _except for_ these in the list we are subtracting off." You can see the formatting is setting the `foreground` to `var(yellow2)`. To be sure of this, copy and paste that block to the right-hand pane and change that to `var(blue)` and ensure the color for your function definitions in C instantly changes. Yep! It sure does! (I just tested this). So, that means I did indeed find the right scope! Anyway, if I like this scope format for something else in my `gcode` syntax highlighting, I'll use scope `entity.name.gcode` as my unique scope to map to this formatting!

    Don't forget to delete the customization you just made in the right-hand pane when done.

<a id="to-_modify-and-test-changes-to-this-package-locally_"></a>
#### To _modify and test changes to this package locally_...
...in case you'd like to change it or contribute to it, follow the "manual installation" instructions above. If you have already installed it via Package Control, then what is in your `/home/$USERNAME/.config/sublime-text-3/Packages/gcode` folder will _override_ what is in your `/home/$USERNAME/.config/sublime-text-3/Installed Packages/gcode.sublime-package` zip file which Package Control installed, so long as the folder and file names are the same. 

Modify any files in the `Packages/gcode` dir as desired. Each time you save, the changes will _instantly be reflected_ in all Sublime Text editors you have open. As a quick test:
1. Open a gcode file.
1. Click your cursor on some text in the file.
1. Use the `Tools` --> `Developer` --> `Show Scope Name` trick to see what the scope is for that text.
1. Open the corresponding `*.sublime-syntax` file.
1. Change or delete the regular expression in the `match` entry for that corresponding `scope` you just found, so that it no longer matches the text on which you placed your cursor.
1. Save the `*.sublime-syntax` file and you will instantly see the formatting of that text in the gcode file change. 
1. Undo your change to the `match` entry and save again. The formatting will return to how it was.
1. Go to `Preferences` --> `Customize Color Scheme`, and add a custom `rules` entry for that scope, with new formatting for that `scope`. Save it and watch the formatting instantly change again. Delete that custom entry when done, if desired.


DONE! 

**You're now a solid beginner at Sublime Text packages and syntax highlighting, just like me! ????**
