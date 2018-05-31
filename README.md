# EasyFlow

_EasyFlow_ is an library of PureData abstractions with two objectives:

- Simplify your work by solving common problems of data flow.
- Suggest and exemplify good Pure Data programming practices and stimulate thought and discussion on writing better organized and maintainable PD code.

While the former is very straight-forward the latter is far from that. I've spent much time dealing with dataflow problems, spending time tasks that a lot of times are effortlessly done in textual languages like C++, Java and Python. For that reason i've set the first objective.

Also, due to it's graphical nature, programming PD means managing space and dealing with all the problems of connecting a lot of objects and avoiding bugs when using wireless connections.  I've wrote some abstractions and the easyflow wiki to share my experience of how i've started better organizing my code. This is why i've set the second objective. See the [easyflow wiki](https://github.com/HenriAugusto/easyflow/wiki) regarding that matter.

If you think about it those objectives are somewhat different sides of the same thing.

_I've made those abstractions throughout the years and some, but not many, are old and most are new (designed after my experience). Everytime i face a problem and i think it's a common dataflow-related problem i write an easyflow abstraction. I try my best to exemplify my suggestions of good PD programming practices but some old objects might still need to be updated in terms of better organization. Nonetheless they're intended to work perfectly, of course._

The library was designed to be basic so it is 100% vanilla.

### Highlights

Here are some highlights. Some are simple yet very useful because PD lacks some basic functionality and others are complex.

- **[for]** = Convenient object to iterate over numeric intervals. Similar to a for in textual languages.
- **[map]** = Converts a numeric stream from one range to another. "One-line" linear interpolation!
- **[printHere]** - a portable console-like abstraction that you can use directly on your patch. No more switching windows!
- **[GOPTool]** = controls the Graph-on-parent values directly from pd. No more editing vlaues then clicking apply!
- **[listToSymbol]** - converts a list to a symbol, adding the special char " " between words. Great to add more than one word to labels.
- **[HSB][HSL][RGB][colorNames][hexColor][colorSyntax]** = Easily generate colors to edit Pure Data vanilla GUI objects.
- **[left2right][right2left][l2r][r2l]** - Miss Java iterators, huh? Yeah, me too. Let's fix this.
- **[sublist][substring]** - Takes subsets on lists or symbols (strings).
- **[colorHighlighting]+related** - color highlighting for better code. See the [easyflow wiki](https://github.com/HenriAugusto/easyflow/wiki) for more information
* **[arrayList]** - holds a list and provides index based get, set and remove methods. Similar to Java's ArrayList.
* **[curves][curvesmap][curves~][curvesmap~}** - an abstraction for converting numeric streams between different curves.
* **[any]** - object able to store any kind of control data. It's like [float][symbol]and [list] packed into one. Also stores custom selectors.
* **[var]** - behaves just like [value] but stores any kind of data (using [anything]) including custom selectors.

## Some gifs

**[hueSaturationBrightness]**

![hsbDemo](https://github.com/HenriAugusto/easyflow/blob/master/wikiFiles/hueSaturationBrightnessDemo.gif)

**[printHere]**

![printHereDemo](https://github.com/HenriAugusto/easyflow/blob/master/wikiFiles/printHereDemo.gif)

**[GOPTool]**

![GOPToolDemo](https://github.com/HenriAugusto/easyflow/blob/master/wikiFiles/GOPToolGif.gif)

## Installing and how to use

If you don't have one create a path where you're going to store all of your externals. For example: _"C:\Users\User\Dropbox\PureData\shared extras"_;

Open Pure Data and go to **File->preferences->path** and add a path to that directory.

Do **not** create a path directly to your externals. By using a shared folder you can use folders like namespaces.

See [How to install externals, libraries, gui plug-ins, etc.](https://forum.pdpatchrepo.info/topic/6743/how-to-install-externals-libraries-gui-plug-ins-etc) on that. The method you should use is the one described in that page on the section _"Loading objects or abstractions using namespaces"_. 

This way you can avoid naming conflicts. Easyflow have an abstraction called [counter]  which is very likely to conflict with other libraries and an abstraction called [hsl] which is **guaranteed** to conclift with vanilla's [hsl]. Easyflow is a 100% so you don't need to use [declare].

## Abstractions

### Lists

- *[addList]* - adds a incoming list to a message box
- *[copyList]* - copies a incoming list on a message box.
- *[left2right][l2r]* - outputs one element of a list at a time, from left to right
- *[right2left][r2l]* - outputs one element of a list at a time, from right to left
- *[funnel]* - outputs a list one element at a time (switches between [l2r] and [r2l]. It's like both in the same abstraction).
- *[passNthElement]* - takes an incoming list and let only it's nth element pass
- *[passPair]* - takes an incoming list and a pair starting at it's nth element to pass
- *[listPlus]* - add a value to each element on an input list
- *[listCompare]* - compare two lists then output left if they're equal or right if they're different.
- *[listConcatenate]* - ListConcatenate takes a message and outputs a symbol which is a concatenation of all of its elements
- *[listPick]* - pick elements from a previously stored list
- *[listPickPair]* - pick element pairs from a previously stored list
- *[listReplace]* - replaces all occurences of an element on a list
- *[listReplaceAtIndex]* - substitutes the n-th element of a incoming list. 
- *[listSplit]* - splits a list on a given symbol.
- *[popLastN]* - outputs a list without it's last n elements
- *[searchElem]* - search for the position of elements on a list



### Symbols 

- *[symbolize]* - Just a shortcut to add a symbol selector to messages
- *[numberSymbol]* - allows you to have symbols that contain only numeric chars
- *[lowerCase][upperCase]* - converts a symbol to lowerCase/upperCase
- *[getFolder]* - get the folder from a symbol containing a file path (and additionally outputs the file name)
- *[getFile]* - get the file name from a symbol containing a file path (and additionally outputs the folder path)
- *[symbolSplit]* - splits a symbol in a specified char


### Signals

- *[spigot~]* - [spigot] for signals
- *[switch2~]* - lets you control if a singnal passes through it's left or right outlet (like [switch2] but for signals)
- *[mixAB~]* - easy equal-power panning with a built-in gui and ramps.
- *[sample~]* - easily load play audio files. Great for experimenting without having spend much time doing the setup. Uses the new [soundfiler] ability to get the sample rate! (bugged as 0.48.0 but working on 0.48.1)


### Utilities

- *[counter]* - simple counter object to output sequences of numbers
- *[for]* - works like until, but with an integrated counter on it's right outlet. It "bangs" on it's left outlet when it's done.
- *[keyChange]* - works like vanilla's [keyname] but only output changes (ie: if you hold a key it will not trigger constantly)
- *[hold]* - Interpolates linearly from a input number to 0 in a give time.
- *[metrosnap~]* - simple [snapshot~] and [metro] bundle
- *[mixAB]* - general purpose utility to mix two signals. Implements useful ramp methods.

### Flow Control

- *[alternate]* - alternates banging on the left and right inlet
- *[compare]* - lets you compare symbols and floats on the same stream
- *[switch2]...[switch7]* - having from 2 to 7 outlets it gives you control of which outlet will be used to pass what comes through it's inlet

### Math

- *[nearest]* - rounds to the nearest integer ([i] rounds to th elowest). Works exactly like [expr rint($f1)] but it's name is easier to remember (heh)
- *[numbersbetween]* - part a numeric stream depending on a specified given range (inside, over and under the range)
- *[map]* = Converts a numeric stream from one range to another. Easy linear interpolation, baby!
- *[keepMax][keepMin]* - Outputs the biggest/smallest number received since initialization or last bang on cold inlet.
- *[hexCharToDec]* - converts an Hexadecimal char to an Decimal number 

### Color

- *[colorNames]* - outputs a color depending on it's name (green, navyBlue, hotPink, etc)
- *[redGreenBlue][rgb]* - Uses Red, Green and Blue information and outputs a integer representing an color to be used with PD vanilla objects.
- *[hueSaturationBrightness][hsb]* - Uses Hue, Saturation and Brightness information and outputs a integer representing an color to be used with PD vanilla objects.
- *[hueSaturationLuminosity][easyflow/hsl]* - Uses Hue, Saturation and Luminosity information and outputs a integer representing an color to be used with PD vanilla objects. (use the slash declaration to avoid confusion with vanilla's [hsl])
- *[hexColor]* - Uses hexadecimal Red, Green and Blue information and outputs a integer representing an color to be used with PD vanilla objects.
- *[colorSyntax]* - parses the color syntax used in [easyflow] and outputs a integer representing an color to be used with PD vanilla objects. Can be used in any object.

### Tables

- *[tabCopy]* - copies an array into another, resizing the destination when needed.
- *[tabReverse]* - reverses an array and write on the same array
- *[tabReverseCopy]* - reverses an array and writes writes on other array

### Coding

#### Color highlighting

- *[colorHighlighting]* - process colors for the automatic highlighting abstractions
- *[colorDef]* - define (unique name,color) associations
- *[colorCirc]* - automatically colored abstraction for color highlighting [send][receive][value] objects
- *[colorCnv]* - automatically colored abstraction for telling what "names" are inside a subpatch
- *[colorTri]* - automatically colored abstraction for marking variable wireless connections
- *[labelCnv]* - automatically colored and resized abstraction to display a labeled [cnv]. Multi-purpose abstraction
- *[colorCircF][colorCnvF][colorTriF][labelCnvF]* - factory abstraction for color highlighting and tagging

#### Debugging and utilities

- *[GOPTool]* - abstraction to quickly manage your graph-on-parent settings without suffering with PD's gui.
- *[printHere]* - in-patch console for debugging without having to switch windows.



## Conventions

### Lists base index

When dealing with lists indexes always start at 1! For me it makes more sense in Pure Data because it matches the $1, $2, $3, ... $n notation.

_(yet on pd table indexes starts at 0, so future table objects might have indexes starting at 0)_

Also, some objects like [easyflow/substring] use 0-based indexes because substring methods traditionally work like this (Java, etc) and symbols are not lists.

_But note how [sublist] and [arrayList] use 1-based indexes because it deals with lists!_

This innocent-seeming question is not so simple. It was not an easy choice but it seems to me this fits pd best.

See those links about that:

[Stack Overflow: Why does the indexing start with zero in 'C'?](https://stackoverflow.com/questions/7320686/why-does-the-indexing-start-with-zero-in-c)

[Edsger W. Dijkstra - Why numbering should start at zero](http://www.cs.utexas.edu/users/EWD/transcriptions/EWD08xx/EWD831.html)

There is no right or wrong. Each context has it's needs.
Some languages like Lua, Mathematica and R use 1-based indexes.

[Wiki - Array system cross-reference list - default base indexes](https://en.wikipedia.org/wiki/Comparison_of_programming_languages_%28array%29#Array_system_cross-reference_list)

Nevertheless its useful to a program to be able to "convert" between those ranges. You can always do arithmetic in the range that is easier for you and then simply convert it back with a [+ 1] or [- 1].

The sample below generates 50 numbers to iterate 5 times over a hipotetical list of 10 elements.

![zeroAndOneIndexBase.png](https://github.com/HenriAugusto/easyflow/blob/master/wikiFiles/zeroAndOneIndexBase.png)

By the way **[easyflow/map]** is there to help you in difficult cases.