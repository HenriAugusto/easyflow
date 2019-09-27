## Abstractions

### Lists

- *[addList]* - adds a incoming list to a message box
- *[arrayList]* - holds a list and provides index based get, set and remove methods. Similar to java's ArrayList.
- *[copyList]* - copies a incoming list on a message box.
- *[left2right][l2r]* - outputs one element of a list at a time, from left to right
- *[right2left][r2l]* - outputs one element of a list at a time, from right to left
- *[funnel]* - outputs a list one element at a time (switches between [l2r] and [r2l]. It's like both in the same abstraction).
- *[passNthElement]* - takes an incoming list and let only it's nth element pass
- *[listCompare]* - compare two lists then output left if they're equal or right if they're different.
- *[listConcatenate]* - listConcatenate takes a message and outputs a symbol which is a concatenation of all of its elements
- *[listsOfLength]* - passes lists of the desired length to the left outlet and other lists to the right outlet.
- *[listPick]* - pick elements from a previously stored list
- *[listReplace]* - replaces all occurences of an element on a list
- *[listReplaceAtIndex]* - substitutes the n-th element of a incoming list. 
- *[listSplitOnChar]* - splits a list on a given symbol.
- *[popLastN]* - outputs a list without it's last n elements
- *[searchIncomingLists]* - search for the position of elements on a list
- *[sublist]* - takes a sublist from a list. Understands negative indexes and has a special variable "L" for the list length!
- *[listReverse]* - reverses a list
- *[listMoses]* - passes a list through it's left or right inlet by running a [moses] on the list length
- *[listOperator]* - runs a binary operator in each of a list's elements
- *[listRemove]* - takes a list and remove it's n-th element
- *[listSearchAndRemove]* - removes every instance of a given element in a list
- *[listUniques]* - removes duplicates on a list
- *[listIntersection]* - outputs the intersection of two lists
- *[iterator]* - more powerful iterator inspired by Java's Iterator interface.
- *[sublistIterator]* - iterator that allows you to get sublists. You can specify a 
- *[listMin][listMax]* - find minimum and maximum values on a list. Optionally ignores symbols.
- *[weightedRandom]* - draws a random element from a list of the format |elem1 weight1 elem2 weight2 ...(
- *[randomList]* - creates lits of random numbers
- *[listCollect]* - reconstructs (recollects) a list after changes to all it's elements

### Collections!

- *[dictionary]* - associative array for (key,value) pairs!


### Symbols 

- *[symbolize]* - Just a shortcut to add a symbol selector to messages
- *[numberSymbol]* - allows you to have symbols that contain only numeric chars
- *[lowerCase][upperCase]* - converts a symbol to lowerCase/upperCase
- *[getFolder]* - get the folder from a symbol containing a file path (and additionally outputs the file name)
- *[getFile]* - get the file name from a symbol containing a file path (and additionally outputs the folder path)
- *[stringLength]* - convenient abstraction to shorten your code when you need to get a symbol's length.
- *[substring]* - takes a substring from a symbol. Understands negative indexes and has a special variable "L" for the string length!
- *[symbolSplit]* - splits a symbol in a specified char
- *[symbolToFloat]* - converts "numeric symbols" back to floats
- *[searchIncomingStrings]* - search for occurences of a given substring on a incoming string
- *[searchString]* - search for occurences of an incoming substring on a given string


### Signals

- *[spigot~]* - [spigot] for signals
- *[switch2~]* - lets you control if a singnal passes through it's left or right outlet (like [switch2] but for signals)
- *[mixAB~]* - easy equal-power panning with a built-in gui and ramps.
- *[sample~]* - easily load play audio files. Great for experimenting without having spend much time doing the setup. Uses the new [soundfiler] ability to get the sample rate! (bugged as 0.48.0 but working on 0.48.1)
- *[scope~]* - simple and easily controllabe osciloscope!


### Utilities

- *[any]* - object able to store any kind of control data. It's like [float][symbol]and [list] packed into one. Also stores custom selectors.
- *[counter]* - simple counter object to output sequences of numbers
- *[doubleClick]* - outputs a bang whenever it receives two bangs in a specified period of time.
- *[for]* - works like until, but with an integrated counter on it's right outlet. It "bangs" on it's left outlet when it's done.
- *[keyChange]* - works like vanilla's [keyname] but only output changes (ie: if you hold a key it will not trigger constantly)
- *[hold]* - Interpolates linearly from a input number to 0 in a give time.
- *[metrosnap~]* - simple [snapshot~] and [metro] bundle
- *[mixAB]* - general purpose utility to mix two signals. Implements useful ramp methods.
- *[var]* - behaves just like [value] but stores any kind of data (using [anything]) including custom selectors.
- *[public][private][member][getMember][setMember][method][callMethod][methodInput][methodOutput][objAccess]* - Objects for neat access to objects members and methods. See [public]'s help file.
- *[valueOp][valueOpSet]* - perform operations on two [value] objects
- *[value++][value--][++value][--value]* - *pre* and *post* in/decrement operators to work on [value] objects
- *[error]* - trackable errors for abstractions
- *[repeat]* - takes whatever you send to it's inlet and outputs it N times
- *[chanceBang]* - outputs a bang according to a random number

### Flow Control

- *[alternate]* - alternates banging on the left and right inlet
- *[compare]* - lets you compare symbols and floats on the same stream
- *[switch2]...[switch7]* - having from 2 to 7 outlets it gives you control of which outlet will be used to pass what comes through it's inlet
- *[ifValue]* - passes it's input through the left if a given [v] is true and left otherwise

### Math

- *[nearest]* - rounds to the nearest integer ([i] rounds to th elowest). Works exactly like [expr rint($f1)] but it's name is easier to remember (heh)
- *[numbersBetween]* - part a numeric stream depending on a specified given range (inside, over and under the range)
- *[map]* = Converts a numeric stream from one range to another. Easy linear interpolation, baby!
- *[keepMax][keepMin]* - Outputs the biggest/smallest number received since initialization or last bang on cold inlet.
- *[hexCharToDec]* - converts an Hexadecimal char to an Decimal number 
- *[roundIfVeryClose]* - rounds numbers that are close to an integer (1.6401e-8 to 0, for example). 
- *[curves][curvesmap]* - an abstraction for converting numeric streams between different curves.
- *[curves~][curvesmap~]* - just like [curves] and [curvesmap] but for signals
You can use arbritary precision.
- *[addNoise]* - takes a number and output a sum with a random number between -X and X where X is 

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
* *[colorCurly][colorCurlyF]* - Colorhighlighting abstractions containing a "{}". See the wiki for more information.
* *[rColor][sColor]* - Automatic color highlighting and [send]/[receive] bundled together. See the wiki for more information.

#### Debugging and utilities

- *[gopTool]* - abstraction to quickly manage your graph-on-parent settings without suffering with PD's gui.
- *[printHere]* - in-patch console for debugging without having to switch windows.

###Data Structures
- *[getNthScalar]* - outputs a pointer to the Nth scalar in a given subpatch.
- *[getNofScalars]* - outputs the number of scalars in a given subpatch.
- *[getAllScalars]* - reads a data holding subPatch and outputs pointers to all the scalars it contains, one at a time.