---
title: Home
layout: home
nav_order: 1
---

TODO:
Some kind of page for extremely common ideas
Main isomorph page

---

Note, this site is a work in progress and is largely unfinished in its current state.

This website is dedicated to cataloguing and organizing any research that could be important to solving the Noita eye puzzle into a searchable format. No approach is too far fetched, but low effort documents will not be included. Some documents will be translated from their original form into markdown so they are easily searchable, but this may at times cause formatting errors. Some documents may remain only as links; for these documents, tags will be added adjacent to the link for better searchability.

This page serves as a jumping off point for anyone wanting to join in on solving the puzzle. Keep in mind, the low hanging fruit have been picked. It is hard to find ideas that haven't been explored to some degree. That's not to say the first thing you think of is not the answer, but it is worth searching here first for information on how others have approached the idea, and what information they might have gleaned from it. A spoiler warning is now in effect. The remainder of this page is transcribed from the [Noita Eye Glyph Messages](https://docs.google.com/document/d/1s6gxrc1iLJ78iFfqC2d4qpB9_r_c5U5KwoHVYFFrjy0/edit#heading=h.tf3tc7h8he20) document by Xkeeper with some minor modifications.

---

There are nine messages that can be displayed via “eye” glyphs. Four of these are in West parallel worlds, five in East worlds. Internally, the messages are placed in East, West, East, West, etc. in alternating order.

Note that the code that spawns the eyes is not a Lua script and cannot be extracted from the archive. It is built into the engine itself. The graphics are also not in the archive but are generated on the fly.

### Frequently Asked Questions

Q: Does this tell me how to find the eyes?
A: No. The only known way to find the eyes right now involves pure luck, or using something like CheatEngine.

Q: Are the eyes always in the same place? Can I follow the map to them?
A: No. However, a given seed will always spawn them in the same locations. If you know where the eyes are in seed 12345678, they will always be in the same place if you make a world with that seed via save editing, tools, or mods.

Q: Do we know what the eyes mean?
A: No.

Q: How long have the eyes been in-game?
A: The general consensus is that these showed up with the release of Noita 1.0.

Q: I want to update information here.
A: That’s not really a question… in any case, this website is generated from a [github repository](https://github.com/loganmcbroom/loganmcbroom.github.io) which you can submit a pull request to with any modifications you see fit. I'm not going to cover how to do that here, but there are plenty of guides online.

Q: What’s this about Cheat Engine? Was Noita disassembled?
A: There is a script you can run in Cheat Engine’s Lua Engine that will trigger when visiting an East or West biome and will print out the generated coordinates of the eyes. Unfortunately, when Noita updates, the script needs to be updated for the new version. The game was also partially disassembled; details on how the messages are generated will be explained later.

### Spawning Details

The eye messages will be visible even if the game is saved and reloaded. A save with the eyes visible can be transferred to different computers, copied, and reloaded without issue.

- The eyes are only spawned once you cross over into an East or West biome area. They will not appear until the “Entered East/West” message is triggered, even if they would otherwise be visible.
- The game will only spawn the eye messages in locations with the background “background_cave_02.png”. This includes some areas that do not have visible backgrounds, like some above-ground areas (notably EDR walls and the Lake area).
- Every eye message, except the last one in East, has a corresponding message in the opposing parallel world. For example, if you find an eye message above East Lake, there will be one in the same place in West Lake. Note that they are not the same message, they’re just in the same locations across parallel worlds.
- The eyes can spawn above or below ground. The reason they are often seen above the Lake or in the sky is simply because they’re more visible -- underground, they blend into the background.
- The actual spawning coordinate generation is unknown but appears to be based on the world seed.

For the eyes to appear, the “mods_have_been_active_during_this_run” flag must not be set. This doesn’t mean that you can’t use mods, the game just can’t know about it. Using mods, saving and quitting, and manually editing world_state.xml will accomplish this (assuming you turned the mods off, of course). The eye messages will not be visible as long as the game thinks you have used mods during the run.

Visual example of parallel world placement
# image here
Notice how W1/E1, W2/E2 etc. correspond with one another in their own words.
Note that this is an example, and the messages will not be in this spot in your world.
See [Finding the eyes](TODO) for how to find the eyes yourself in-game.

### Messages And Trigrams

Each message is displayed as a series of eye glyphs, with every other line offset slightly to mesh together. The game uses a string of digits from 0 to 5 to store the eye data like so:

| 0 | 1 | 2 | 3 | 4 | 5 |
| center | up | right | down | left | new line |

All of the messages have an eye count divisible by three. This, along with the strange looking ending of each message, suggests the eyes should be grouped into alternating up and down triangles which are dubbed "trigrams". Note that the number of eyes in one message is exactly three times a prime number, so there are no further quantities into which they can be grouped. Converting each eye into its numeric representation, there are thirty six ways that these numbers can be ordered (accounting for up and down triangles having different ordering. Treating these numbers as the digits of a single base five number yields no discernable pattern in all but one arrangement, the canonical reading order. That arrangement yields every value from 0 to 82, and none of the values from 83 to 124, the maximum possible value for a three digit base five number. The chance of this happening randomly is small enough to be ruled out as having happened by chance, and so this reading is generally accepted as the correct interpretation. The base five numbers given by this reading, along with other raw formats for the eye data can be found [here](https://docs.google.com/spreadsheets/d/195Rtc8kj4b74LtIyakqGP-iHhm36vyT5i8w7H5JjOV8/edit#gid=202652133). Note the tabs at the bottom for changing the data representation.

### Observable Patterns

The majority of the work put into the eye puzzle has been attempts do decipher the canonical reading of the eye messages using standard cryptographic techniques. See the cryptography section in the sidebar for comprehensive information on the techniques applied. Despite no solution having been found, a number of unusual properties are expressed by the data. The following properties listed by Pyry are the most notable.

1. The messages have a relatively uniform frequency distribution.
1. The messages contain all contiguous values from 0 to 82, and none above.
1. The messages have significant shared sections.
1. The shared sections are not disrupted by the first character of each message differing.
1. The messages contain [isomorphs](TODO)
1. The isomorphs have slightly differing compositions.
1. No trigram appears twice in a row within the same message.
1. The trigrams can appear at adjacent positions in different messages.

### What Next?

From here you can head in any direction. Very little (if any) progress exists outside the cryptography section, so that is likely the best place to start. The discord linked in the sidebar is where most active discussion on the puzzle happens, join there and ask Harry or Slurrps to give you access to the eye channels.