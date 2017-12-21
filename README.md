# EasyFlow

_EasyFlow_ is an library of PureData abstractions with two objectives:

- Simplify your work by solving common problems of data flow.
- Suggest and exemplify good practices of Pure Data programming.

While the former is very straight-forward the latter is far from that. I've spent much time dealing with dataflow problems, dealing tasks that a lot of times are effortlessly done in textual languages like C++, Java and Python. Due to it's graphical nature programming PD means managing space and dealing with all the problems of connecting a lot of objects on the screen and avoind bugs when using wireless connections. Those good practices of PD programming come from my years of experience with PD which, curiously, i've spent more in the "control part" than in the "dsp" part. I guess i liked the challenge.

I've made those abstractions throughout the years and some, but not many, are old and most are new (designed after my experience). Everytime i face a problem and i think it's a common dataflow-related problem i write an easyflow abstraction. I try my best to exemplify my suggestions of good PD programming practices but some old objects still needs to be updated (nonetheless they're intended to work perfectly, of course)

The library was designed to be elementar so it is %100 vanilla an has no dependencies.

## Highlights

- **[for]** = convenient object to iterate over numeric intervals. Similar to a for in textual languages
- **[map]** = Converts a numeric stream from one range to another. Easy linear interpolation, baby!
- **[HSB][HSL][RGB][colorNames][hexColor]** = Easily generate colors to edit Pure Data vanilla GUI objects.
- **[colorcnv]** - the best way to organize your code. Lets you find matching **[s]** and **[r]** in an instant.
- **[copylist]** - very useful for debugging. You can use it like a list box. Just put a message box after it. This way you don't need to watch the console all the time.
- **[printHere]** - a console-like that you can use directly on your patch. No more switching windows!
- **[GOPTool]** = controls the Graph-on-parent values directly from pd. No more editing vlaues then clicking apply!
- **[colorcnv][labelcnv][colorcirc][colortri]** - make your code easier and faster to read and organize
- **sample~** - easily play audio files. Uses the new [soundfiler] ability to get the sample rate! (bugged as 0.48.0 but working on 0.48.1)

(Lots of EasyFlow abstractions uses other abstractions from the library. In most of those cases, that other abstractions were included
as subpatches to eliminate dependencies. This way you can simply copy the abstractions you need if you don't want the entire library).

## Abstractions

- *[addList]* - just like |add2 $1( but with an entire list
- *[alternate]* - Passes it's input one time to the left, then to the right, then to the left...
- *[audioSpigot~]* - just like [spigot], but for signals, with a [line~]
- *[counter]* - Simple counter object.
- *[compare]* - this abstraction solves the problem of dealing with selectors and [sel] for you.
- *[concatenate]* - Concatenate a list of symbols that it receives into one symbol.
- *[copyList]* - Copies a list on a message box.
- *[invert]* - just like |$2 $1(
- *[keychange]* - like [keyname] but only outputs when a key change
- *[for]* - Works like until, but with an integrated counter on it's right outlet. It "bangs" on it's left outlet after it's done.
- *[l2R]* - (Left to Right) - Takes a list and outputs it's elements one at a time, from left to right order.
- *[r2L]* - (Right to Left) - Takes a list and outputs it's elements one at a time, from right to left order.
- *[funnel]* - Abstraction that switches between l2r and r2l.
- *[getNthElement]* - Receives an index N on it's cold inlet and when it receives a list on it's hot inlet,
it outputs it's Nth element. See _ListPick_.
- *[getPair]* - Just like _GetNthElement_ but outputs a pair. (the Nth element and it's sucessor)
- *[listPick]* - Store a list on it's cold inlet and get it's elements by sending it's indexes on ListPick
hot inlet. Works with the inverse order of GetNthElement. Notice what triggers the output on each abstraction.
- *[l2r]* - outputs elements of a list one at a time in left to right order. See _r2l_
- *[list+]* - Sums an argument to every float in a list
- *[listCompare]* - Compare two lists
- *[listConcatenate]* - Concatenate two lists
- *[popNthElement]* - Passes a list through without it's N-th element.
- *[popLastN]* - Passes a list without it's last N elements.
- *[r2l]* - outputs elements of a list one at a time in right to left order. See _l2r_
- *[search]* - Search for a specific value on a list and outputs it's indexes. Outputs -1 if not found.
- *[searchNDestroy]* - Store symbols as variables and call them by their ID.
- *[substituteNthElement]* - Passes a list through without it's N-th element.
- *[switch]* - Passes it's input through it's left or right outlet depending on what you send to it's cold inlet.
- *[symbolize]* - convenient shortcut to [list prepend symbol] ==> [list trim].
- *[nearest]* - rounds a float to the nearest integer (easier to remember than [expr rint($f1)])

## Conventions

### Lists base index

When dealing with lists indexes always start at 1! For me it makes more sense in Pure Data because it matches the $1, $2, $3, ... $n notation.

This innocent-seeming question is not so simple. It was not an easy choice but it seems to me this 

See those links about that:

https://stackoverflow.com/questions/7320686/why-does-the-indexing-start-with-zero-in-c

http://www.cs.utexas.edu/users/EWD/transcriptions/EWD08xx/EWD831.html

There is no right or wrong. Each context has it's needs.
Some languages like Lua, Mathematica and R use 1-based indexes.

https://en.wikipedia.org/wiki/Comparison_of_programming_languages_%28array%29#Array_system_cross-reference_list

Nevertheless its useful to a program to be able to "convert" between those ranges. You can always do arithmetic in the range that is easier for you and then simply convert it back with a [+ 1] or [- 1].

The sample below generates 50 numbers to iterate 5 times over a hipotetical list of 10 elements.

|set 0, 50(             % numbers from 0 to 49
|
[easyflow/counter]
|
[% 10]                   % numbers from 0 to 9
|
[+ 1]                    % numbers from 1 to 10
|
[easyflow/listPick]




[easyflow/map] is there to help you in difficult cases
