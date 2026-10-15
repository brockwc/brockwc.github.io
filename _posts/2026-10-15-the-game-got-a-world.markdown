---
layout: post
title: "The game got a world"
date: 2026-10-15 14:10:00 -0700
categories: [capstone]
---

This week the game got a world. The second goal on my build roadmap is done: the map is now actual data
(a 40x20 grid of wall and floor tiles), the room renders on screen, and the player can no longer
walk through walls or off any edge. That last part is the real milestone - movement now works by
figuring out where the player wants to go, asking the map if that tile is walkable, and only
moving if it is. It replaces the edge clamping from the first goal, and it is the same question the
procedural generation and monster AI features will need answered later, so it felt worth getting
right.

This goal was also a change in how I worked. The first goal was fully scripted: I followed complete code
and made sure I understood each part. For this one the guide gave me the structure (types,
function signatures, checkpoints) and I wrote the core logic myself: the walkability check, the
collision handling, the tile rendering, and the tests. The walkability check fought back the
hardest - mostly around edge cases like positions outside the map - and an off-by-one loop bug
crashed the game on first run with a message naming the exact line and index. Two-minute fix,
but the kind of error message that makes me appreciate the toolchain.

The test suite grew from two tests to six, covering walls, out-of-bounds positions, blocked
movement, and the index math that maps (x, y) coordinates onto the tile array. All green, CI
clean. I also set up a screen layout that keeps the header text and the game board from
overwriting each other, which will matter more as the UI grows.

The mid-project update report was due today and is submitted; writing it was a useful forcing
function to compare the plan against reality. Short version: the ramp-up ran about a week long
and I cut the three standalone CLI programs (the exercises plus the game cover the same ground),
but the game itself is on schedule with two of eight roadmap goals done and the scope frozen.

Plan for next week: the next roadmap goal, procedural generation - replacing the single hand-placed room with
rooms and corridors that generate at random, with a guaranteed walkable path. Also continuing
the Rustlings strings and error handling exercises.

No blockers.
