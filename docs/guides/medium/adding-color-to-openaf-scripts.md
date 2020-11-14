---
layout: default
title: Adding color to OpenAF scripts
parent: Medium
grand_parent: Guides
---

# Adding color to OpenAF scripts

Black and white scripts can be tedious and many times when something errors out and you are tired you may not even notice it. So color not only helps to make it more "colourful" but also helps errors and warnings to stand out from the rest of the logging or printing.

In OpenAF, if the current terminal supports ANSI color you can use the ansi* functions in any script. These functions will detected if ANSI color is supported and return the proper escape sequences to produce "color".

Here is a quick description of the 3 main functions:

  * ansiStart() - Detects and prepares to output ansi color escape sequences.
  * ansiStop() - Stops the output of ansi color escape sequences.
  * ansiColor(aAnsiSetting, aString, force) - Returns aString within the appropriate ANSI color escape sequences for the provide aAnsiSetting

The attributes are self-explanatory but some might only work on specific terminals (colors will work pretty much everywhere). You can have a set of attributes separated by commas. You can get a list of possible attributes on the ansiColor help:

````javascript
> help ansiColor
-- ansiColor(aAnsi, aString, force) : String
-- -----------------------------------------
-- Returns the ANSI codes together with aString, if determined that the current terminal can handle ANSI codes (overridden by force = true), with the attributes defined in aAnsi. Please use with ansiStart() and ansiStop(). The attributes separated by commas can be:
 
BLACK; RED; GREEN; YELLOW; BLUE; MAGENTA; CYAN; WHITE;
FG_BLACK; FG_RED; FG_GREEN; FG_YELLOW; FG_BLUE; FG_MAGENTA; FG_CYAN; FG_WHITE;
BG_BLACK; BG_RED; BG_GREEN; BG_YELLOW; BG_BLUE; BG_MAGENTA; BG_CYAN; BG_WHITE;
BOLD; FAINT; INTENSITY_BOLD; INTENSITY_FAINT; ITALIC; UNDERLINE; BLINK_SLOW; BLINK_FAST; BLINK_OFF; NEGATIVE_ON; NEGATIVE_OFF; CONCEAL_ON; CONCEAL_OFF; UNDERLINE_DOUBLE; UNDERLINE_OFF;
````

Examples of usage:

Writing part of a string with white foreground and red background:

![openaf-red-color.jpg](openaf-red-color.jpg)

Writing part of a string with black foreground and yellow background:

![openaf-yellow-color.jpg](openaf-yellow-color.jpg)