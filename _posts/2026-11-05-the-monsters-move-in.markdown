---
layout: post
title: "The monsters move in"
date: 2026-11-05 17:02:57 -0800
categories: [capstone]
---

This week the dungeon got monsters. Step 5 of the build guide is implemented: monsters spawn in rooms, watch for the player, and chase when they spot one. The chase tests are still on my list, so this is a gameplay-complete, tests-pending checkpoint.

I also finished the field of view tests early in the week. The line-of-sight code from last week now has coverage for the line calculation, walls blocking sight, and the view updating as the player moves. The full suite sits at 18 tests and passes.

The monsters reuse last week's line-of-sight work, which was a nice payoff. Each monster checks whether it can see the player by casting a ray from its own position with its own sight radius, using the same code the player's camera uses. A monster that cannot see the player just stands still, so ducking around a corner actually loses one.

When a monster does see the player it takes one step per turn toward the closer direction first, and falls back to the other direction if a wall or another monster is in the way. Monsters never stack on the same tile and never step onto the player. Combat comes in the next step, so for now they crowd around you harmlessly. In testing I had three of them following me down a corridor in single file, which is exactly the mood the roadmap promised.

One real bug this week: the game crashed when the terminal got resized smaller mid-session. The drawing code looped over the whole map and wrote every tile to the screen without checking that the window was still big enough to hold them, so any window shorter than the map panicked on the next frame. The fix was to clip drawing to whatever fits, so a small window shows the top-left corner of the dungeon instead of crashing. It was a good reminder that "works on my machine" includes my window size.

Next up: the chase behavior tests, then step 6 adds hit points, bump-to-attack combat, and a message log. The monsters stop being harmless.
