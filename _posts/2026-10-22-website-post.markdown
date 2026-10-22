---
layout: post
title: "The dungeon generates itself now"
date: 2026-10-22 13:30:00 -0700
categories: [capstone]
---

This week the dungeon got a dungeonfunction. The third goal on my roadmap is done so every game now starts
with a randomly generated layout of rooms connected by corridors, and the player spawns in the center of the
first room. The map starts as solid "Wall", and the generator carves rooms into it, then digs
L-shaped hallways between them. The trick that keeps the whole dungeon reachable is that each new
room only connects to the one before it, which chains every room back to the first one. No room
can end up as an island.

The new part this week was randomness using the rand crate in rust. Everything the generator does comes from one
random number generator, and it can be started from a fixed seed so that a given layout can be revisted. That also changed how I test 
because I can write a test that builds the same dungeon twice and check that they are identical, plus
one that checks the player always lands on a walkable tile in the first room no matter the layout.

There were two bugs worth mentioning. The first bug was in the room-overlap check. I had it detecting
overlap correctly but not touching: two rooms sharing an edge counted as separate, so the generator
would happily place rooms wall-to-wall basically causing them to merge into one blob. The fix was a slight
change to the comparison operators being used, but finding it meant walking through the condition by hand and watching
the two versions disagree on the exact edge case. The second bug was a crash on first run: the
generator tried to connect each new room to the previous one, but the very first room has no
previous room. This was fixed with a guard, but it was the first time I had seen the error about panicking which was kind of funny.

One process note: I committed part of this week's work to main before remembering to use a feature-branch,
which turned out to be a ten-minute fix of just moving branch pointers around, since nothing
had been pushed yet.

Plan for next week: field of view, so the dungeon stops showing itself all at once and
the player has to actually explore it. Also still working through the Rustlings strings and error
handling exercises.

No blockers.
