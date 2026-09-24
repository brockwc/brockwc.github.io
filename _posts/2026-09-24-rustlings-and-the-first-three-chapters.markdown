---
layout: post
title: "Rustlings, the guessing game, and the first three chapters"
date: 2026-09-24 12:00:00 -0700
categories: [capstone]
---

This week was the first full week of the Rust ramp-up for Path of Rust. I split the time
between Rustlings and The Rust Book, and the exercises won.

On the Rustlings side I finished the intro, variables, functions, control flow, and
primitive types sections, passed the first quiz, and started in on vectors. On the reading
side I got through the first three chapters and built the chapter 2 guessing game with
Cargo. The guessing game was the first moment things connected: reading stdin, parsing to a
number, looping until a correct guess, matching on Results, and pulling rand from crates.io.

Two observations so far. First, the Rustlings format suits me: fixing compiler errors
teaches faster than reading alone, and the borrow checker has stayed quiet because the
early exercises are small and mostly immutable. I expect move semantics and error handling
to be where it actually gets hard. Second, the book is denser than the exercises. My
original plan had me at chapter 9 by now; I am at chapter 3. I am adjusting the split to
keep Rustlings as the main line and backfill chapters as the sections they pair with come
up.

Next week: the vecs, move semantics, structs, enums, and error handling Rustlings sections,
more book chapters, and the ratatui vs bracket-lib decision so the game repo can actually
start. I will include the repo in the next update.

One question for anyone who has used Rustlings: which sections paid off the most when you
moved on to real projects?

No blockers right now.
