These are some example syntax highlighting files I used as a starting point.

1. `GcodeSyntaxHighlightingDef.*`: [gcode-syntax-highlighting](https://github.com/themachinist/gcode-syntax-highlighting), by @themachinist.
    1. my fork of it: https://github.com/ElectricRCAircraftGuy/gcode-syntax-highlighting
1. `cnc*`: The [zip file version by @digex, here](https://github.com/themachinist/gcode-syntax-highlighting/issues/2#issuecomment-106274142).
    1. See my [full installation instructions and notes on it here](https://github.com/themachinist/gcode-syntax-highlighting/issues/2#issuecomment-1073127156).

For testing and comparison, you can temporarily re-enable the `cnc` syntax highlighting file called `cnc.tmLanguage.disabled` by simply removing the `.disabled` ending and renaming it to `cnc.tmLanguage`. Once you do this, it will automatically show up in the Sublime Text syntax highlighting menu under `gcode` --> `CNC`. The main syntax will then become `gcode` --> `gcode`. For details on how this works, see the main [README](../README.md) under the section titled ["Multiple syntax highlighting definitions in one package"](../README.md#multiple-syntax-highlighting-definitions-in-one-package).
