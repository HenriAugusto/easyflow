# easyflow

_easyflow_ is an library of PureData abstractions with two objectives:

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
- **[any]** - object able to store any kind of control data. It's like [float][symbol]and [list] packed into one. Also stores custom selectors.
- **[var]** - behaves just like [value] but stores any kind of data (using [anything]) including custom selectors.
- **[left2right][right2left][l2r][r2l]** - Miss Java iterators, huh? Yeah, me too. Let's fix this.
- **[printHere]** - a portable console-like abstraction that you can use directly on your patch. No more switching windows!
- **[listToSymbol]** - converts a list to a symbol, adding the special char " " between words. Great to add more than one word to labels.
- **[HSB][HSL][RGB][colorNames][hexColor][colorSyntax]** = Easily generate colors to edit Pure Data vanilla GUI objects.
- **[sublist][substring]** - Takes subsets on lists or symbols (strings). Includes a special "L" variable that resolves to the list/string length.
- **[colorHighlighting]+related** - color highlighting for better code. See the [easyflow wiki](https://github.com/HenriAugusto/easyflow/wiki) for more information
- **[arrayList]** - holds a list and provides index based get, set and remove methods. Similar to Java's ArrayList.
- **[curves][curvesmap][curves~][curvesmap~}** - an abstraction for converting numeric streams between different curves.
- **[gopTool]** - controls the Graph-on-parent values directly from pd. No more editing vlaues then clicking apply!
- **[dictionary]** - associative array for (key,value) pairs!
- **[listCollect]** - reconstructs (recollects) a list after changes to all it's elements

## Some gifs

**[hsb]** or **[hueSaturationBrightness]**

![hsbDemo](https://github.com/HenriAugusto/easyflow/blob/master/wikiFiles/hueSaturationBrightnessDemo.gif)

**[curves]**

![curves demo bounce](https://github.com/HenriAugusto/easyflow/blob/master/wikiFiles/curves%20bounce%20demo.gif)

![curves demo exp](https://github.com/HenriAugusto/easyflow/blob/master/wikiFiles/curves%20exp%20demo.gif)

**some automatic color highlighting**

![sColor rColor demo](https://github.com/HenriAugusto/easyflow/blob/master/wikiFiles/sColor%20rColor%20demo.gif)

**[printHere]**

![printHereDemo](https://github.com/HenriAugusto/easyflow/blob/master/wikiFiles/printHereDemo.gif)

**[gopTool]**

![gopToolDemo](https://github.com/HenriAugusto/easyflow/blob/master/wikiFiles/GOPToolGif.gif)

## Installing and how to use

If you don't have one create a path where you're going to store all of your externals. For example: _"C:\Users\User\Dropbox\PureData\shared extras"_;

Open Pure Data and go to **File->preferences->path** and add a path to that directory.

Do **not** create a path directly to your externals. By using a shared folder you can use folders like namespaces.

See [How to install externals, libraries, gui plug-ins, etc.](https://forum.pdpatchrepo.info/topic/6743/how-to-install-externals-libraries-gui-plug-ins-etc) on that. The method you should use is the one described in that page on the section _"Loading objects or abstractions using namespaces"_. 

This way you can avoid naming conflicts. Easyflow have an abstraction called [counter]  which is very likely to conflict with other libraries and an abstraction called [hsl] which is **guaranteed** to conclift with vanilla's [hsl]. Easyflow is 100% vanilla so you don't need to use [declare] (like you would with some monolithic libraries like *zexy*).

## Abstractions

[List of abstractions](https://github.com/HenriAugusto/easyflow/blob/master/abstractions.md)

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
