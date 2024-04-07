This Vue.js app is a proof of concept for a detail of the [prolog_trace](https://github.com/watchduck/prolog_trace) app,
and uses the same Python backend.<br>
It turns a formula in prefix notation into a tree structure, realized as an HTML table.

The formula in the following screenshot is the [law of cosines](https://en.wikipedia.org/wiki/Law_of_cosines).
(*ang* means *angle opposite of*.)<br>
The cursor is on the *c* highlighted in orange. All other occurences are highlighted in yellow.

![treetable_law_of_cosines](https://user-images.githubusercontent.com/8267930/74094615-79854f00-4ae4-11ea-86fe-6d96eee27c9c.png)

The app allows functions with different arity to have the same name, and be treated as different.<br>
(That is motivated by the fact that Prolog allowes this.)

The following screenshot shows the result for the input "f(f, f(f), f(f, f(f)))".<br>
Only 1-ary *f* is highlighted, but not the others.<br>
This example also shows, that entered names can be replaced by custom names.<br>
3-ary *f* has been renamed to "X", and 0-ary *f* is shown as a dot. 

![Screenshot from 2020-02-09 02-56-10](https://user-images.githubusercontent.com/8267930/74094835-f5cd6180-4ae7-11ea-9b44-a92fbeb91b3f.png)

Custom names must not be empty, and together with the arity they must be unique.<br>
(One could even used parentheses as custom names &ndash; which is probably not a good idea.)
