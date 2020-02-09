This app is a proof of concept for a detail of the [prolog_trace](https://github.com/watchduck/prolog_trace) app.<br>
It turns a formula in prefix notation into a tree structure, realized as an HTML table.

The formula in the following screenshot is the [law of cosines](https://en.wikipedia.org/wiki/Law_of_cosines).
(*ang* means *angle opposite of*.)<br>
The cursor is on the *c* highlighted in orange. All other occurences are highlighted in yellow.

![treetable_law_of_cosines](https://user-images.githubusercontent.com/8267930/74094615-79854f00-4ae4-11ea-86fe-6d96eee27c9c.png)

The app allowes functions with different arity to have the same name, and be treated as different.<br>
(That is motivated by the fact that Prolog allowes this.)

The following screenshot shows that only 1-ary *f* is highlighted, but not the others.<br>
It also shows that the entered names can be replaced by custom names.

![Screenshot from 2020-02-09 02-56-10](https://user-images.githubusercontent.com/8267930/74094835-f5cd6180-4ae7-11ea-9b44-a92fbeb91b3f.png)
