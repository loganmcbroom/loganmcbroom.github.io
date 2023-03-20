---
layout: default
title: Falter
---

Falter is a frontend for Flan that aims to remove as many obstacles as it can while adding little else. It handles loading and saving audio from and to disk, managing processing threads, loading Flan algorithms into a Lua enviornment, and watching a script to recompute whenever that script is updated. When using Falter, Lua is used to avoid c++ compilation time for faster iteration of ideas. This comes at a cost of some runtime speed, but the lack of compilation makes up for this. If you need the absolute maximum speed, use Flan directly.

Falter is made up of a header, a body, and a footer. The header contains a "begin process" button, a "select script" button, and a display of the loaded script's name. The body contains, in left to right order, a view of files on disk, the input file list, the thread list, and the output file list. Files can be drag-and-dropped between areas when appropriate. Individual items in lists can be removed with the "x" next to them, or the whole list can be cleared with the "x" above the list. The footer is where any information coming from processing threads or Falter itself that might be useful to the user is sent.

Falter watches the selected script for updates. Updates are only registered when changes are saved to disk. When those changes are noticed, Falter will automatically rerun the watched script on the current input file list. This feature is very cool, and you can't turn it off unless you email me and ask for that feature.

To access the input file list from the script, use "f[i]" to get the ith input. Keep in mind, Lua is 1-indexed, so "f[1]" will be the first input.

###LTMP
You can work with Audio and PVOC types normally in Falter scripts, but each basic sound type also has a "____Vec" type associated with it, e.g. AudioVec is a Lua type associated with Audio. There are a number of shorthands employed by Falter to allow quickly testing ideas with a range of inputs using these Vec types.
TODO: explain
If I don't get around to explaining that ever, you can write things like "bah:repitch( { 2, 3 } )" to get an AudioVec containing bah repitched by 2 and 3. You could then extend this as "bah:repitch( { 2, 3 } ):setVolume( .8 )". Each Audio in the AudioVec will have its volume set to .8, and an AudioVec will be returned.