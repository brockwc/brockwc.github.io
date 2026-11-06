---
layout: post
title: "The monsters move in"
date: 2026-11-05 17:02:57 -0800
categories: [capstone]
---

This week I added monsters to the game and made progress on their movement. Right now monsters spawn in rooms, watch for the player, and chase when they spot you. I also finished the last week's field of view tests early in the week but am going to need to do the same thing this week because I didn't complete the chase tests. The line-of-sight code from last week now has test coverage for the line calculation, walls blocking sight, and the view updating as the player moves.

The monsters reuse last week's line-of-sight work and it was a nice feeling to reuse parts of that feature to implement this one. Each monster checks whether it can see the player by casting a ray from its own position with its own sight radius, using the same code the player's camera uses. A monster that cannot see the player just stands still, so ducking around a corner actually loses one. When a monster does see the player it takes one step per turn toward the closer direction first, and falls back to the other direction if a wall or another monster is in the way. Monsters never stack on the same tile and never step onto the player. Combat comes in the next step, so for now they crowd around you harmlessly. In testing I had three of them following me down a corridor in single file, which felt a little like some of the games I really like (Path of Exile, Diablo, etc.).

I had one bug this week: the game crashed when the terminal got resized smaller mid-session. The drawing code looped over the whole map and wrote every tile to the screen without checking that the window was still big enough to hold them, so any window shorter than the map panicked on the next frame. The fix was to clip drawing to whatever fits, so a small window shows the top-left corner of the dungeon instead of crashing. It was a good reminder that "works on my machine" includes my window size and if I am doing 90% of my testing in a VS Code terminal pane, I am probably missing things like that. Next week: the chase behavior tests, then add hit points, bump-to-attack combat to start, and a message log.
