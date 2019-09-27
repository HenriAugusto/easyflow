# easyflow version 0.3.0

## backwards-incompatible changes

- *[searchElem]* was renamed to [searchIncomingLists]
- *[rgb][hsb][hsl]* all gone from 4 to 3 inlets to be more consistent with pd's default (hot + colds)
- *[listPlus]* was deleted in favor of [listOperator]
- *[listPickPair]* was deleted because [listPick] accepts an argument for how much elements to pick
- *[listSplit]* was renamed to [listSplitOnChar]

## improvements

- *[left2right][right2left]* - now has a second inlet for stopping iteration
- *[easyflow-info-help]* - improvements to the list of "lists-related abstractions".
- *[printHere]* - for some deep reason PD replaces # (raute) in it's labels with $ (dollar). For that reason [printHere] now replaces '#' replace with '♯' wich is the char for sharp. I doesn't look that good but at least it doesn't modify the meaning of anything like the $.
- *[printHere]* - now it blinks when receiving an input, like [else/display].
- *[printHere]* - now the GOP (Graph-on-Parent) settings are adjusted as well as the canvas size for a seamless look!
- *[sublist]* - now accepts floats (1 element lists)
- *[arrayList]* - new |send( method to sending sublists to a named [receive] objects
- *[rgb][hsl][hsb]* are now copies of the "full name" versions to avoid instatiation problems (see issue #16)

## new abstractions

- *[listReverse]* - reverses a list
- *[symbolToFloat]* - converts "numeric symbols" back to floats
- *[public][private][member][getMember][setMember][method][callMethod][methodInput][methodOutput][objAccess]* - Objects for neat access to objects members and methods. See [public]'s help file.
- *[valueOp][valueOpSet]* - perform operations on two [value] objects
- *[value++][value--][++value][--value]* - *pre* and *post* in/decrement operators to work on [value] objects
- *[ifValue]* - passes it's input through the left if a given [v] is true and left otherwise
- *[error]* - trackable errors for abstractions
- *[listMoses]* - passes a list through it's left or right inlet by running a [moses] on the list length
- *[listOperator]* - runs a binary operator in each of a list's elements
- *[listRemove]* - takes a list and remove it's n-th element
- *[listSearchAndRemove]* - removes every instance of a given element in a list
- *[listUniques]* - removes duplicates on a list
- *[listIntersection]* - outputs the intersection of two lists
- *[iterator]* - more powerful iterator inspired by Java's Iterator interface.
- *[listCollect]* - reconstructs (recollects) a list after changes to all it's elements
- *[sublistIterator]* - iterator that allows you to get sublists. You can specify a repeating pattern of sublist sizes!
- *[listMin][listMax]* - find minimum and maximum values on a list. Optionally ignores symbols.
- *[searchString]* - search for occurences of an incoming substring on a given string
- *[searchIncomingStrings]* - search for occurences of a given substring on a incoming string
- *[dictionary]* - associative array for (key,value) pairs!
- *[chanceBang]* - outputs a bang according to a random number
- *[weightedRandom]* - draws a random element from a list of the format |elem1 weight1 elem2 weight2 ...(
- *[addNoise]* - takes a number and output a sum with a random number between -X and X where X is the noise amplitude
- *[repeat]* - takes whatever you send to it's inlet and outputs it N times
- *[randomList]* - creates lits of random numbers

## bugfixes

* Fixed an issue regarding letter case inconsitencies (https://github.com/HenriAugusto/easyflow/issues/13)
- *[sublist]* - fixes a bug on sublist where [sublist n n] would NOT get the nth element and [sublist n n+1] would only get the n-th element.
- *[for]* - Now i initialize the spigot on the [pd stop] subpatch so cases like |1 1( work if they are the first thing a [for] object receives
- *[switch]* family - fixed a nasty bug in the *[switch]* family - i wrote about it here [pure data vs text languages return and side effects part 2](https://henriaug.wordpress.com/pure-data-vs-text-languages-return-and-side-effects-part-2/)


# easyflow version 0.2.0

## backwards-incompatible changes

* [audiospigot~] was renamed to [spigot~]

## improvements

- *[getFolder]* - new outlet: outputs file name
- *[sample~]* - now displays sample name

## new abstractions

- *[getFile]* - just like [getFolder] but outputs the file on the left outlet and the folder on the right
- *[getNthScalar]* - outputs a pointer to the Nth scalar in a given subpatch.
- *[getNofScalars]* - outputs the number of scalars in a given subpatch.
- *[getAllScalars]* - reads a data holding subPatch and outputs pointers to all the scalars it contains, one at a time.
- *[listsOfLength]* - passes lists of the desired length to the left outlet and other lists to the right outlet.
- *[scope~]* - simple and easily controllabe osciloscope!
- *[substring]* - takes a substring from a symbol. Understands negative indexes and has a special variable "L" for the string length!
- *[sublist]* - takes a sublist from a list. Understands negative indexes and has a special variable "L" for the list length!
- *[stringLength]* - convenient abstraction to shorten your code when you need to get a symbol's length.
- *[curves][curvesmap]* - an abstraction for converting numeric streams between different curves.
- *[curves~][curvesmap~]* - just like [curves] and [curvesmap] but for signals
- *[roundIfVeryClose]* - rounds numbers that are close to an integer (1.6401e-8 to 0, for example). You can use arbritary precision.
- *[colorCurly][colorCurlyF]* - Colorhighlighting abstractions containing a "{}". See the wiki for more information.
- *[rColor][sColor]* - Automatic color highlighting and [send]/[receive] bundled together. See the wiki for more information.
- *[arrayList]* - holds a list and provides index based get, set and remove methods. Similar to java's ArrayList.
- *[any]* - object able to store any kind of control data. It's like [float][symbol]and [list] packed into one. Also stores custom selectors.
- *[var]* - behaves just like [value] but stores any kind of data (using [anything]) including custom selectors.
- *[switch2~] family* - the family is now complete from [switch2~] up to [switch7~]
- *[doubleClick]* - outputs a bang whenever it receives two bangs in a specified period of time.

## bugfixes

* [MixAB~] now starts with amplitude 1 on the left outlet's [vline~] so you don't need to click the [hsl] to initialize the amplitude. (Sending |1( to the [vline~] objects on [loadbang])
* [listReplace-help] file name was corrected. There was an typo: "helpp"

# easyflow version 0.1.0

## New abstractions

### Lists

[addList][copyList][left2right][l2r][right2left][r2l][funnel][passNthElement][passPair][listPlus][listCompare][listConcatenate][listPick][listPickPair][listReplace][listReplaceAtIndex][listSplit][popLastN][searchElem]


### Symbols 

[symbolize][numberSymbol][lowerCase][upperCase][getFolder][symbolSplit]

### Signals

[audiospigot~][switch2~][mixAB~][sample~]

### Utilities

[counter][for][keyChange][hold][metrosnap~][mixAB]

### Flow Control

[alternate][compare][switch2]...[switch7]

### Math

[nearest][numbersBetween][map][keepMax][keepMin][hexCharToDec]

### Color

[colorNames][redGreenBlue][rgb][hueSaturationBrightness][hsb][hueSaturationLuminosity][easyflow/hsl][hexColor][colorSyntax]
### Tables

[tabCopy][tabReverse][tabReverseCopy]

### Coding

#### Color highlighting

[colorHighlighting][colorDef][colorCirc][colorCnv][colorTri][labelCnv][colorCircF][colorCnvF][colorTriF][labelCnvF]

#### Debugging and utilities

[gopTool][printHere]