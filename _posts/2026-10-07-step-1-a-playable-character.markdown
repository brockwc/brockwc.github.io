---
layout: post
title: "Step 1: a playable character"
date: 2026-10-07 11:50:00 -0700
categories: [capstone]
---

This week the project started to come together as I built out the game state and input controls to allow players to move a character around the terminal window. After doing some research, I decided on the stack: ratatui 0.29 with crossterm, for a terminal roguelike, because it is actively maintained and (it says) it works well within a Windows terminal. The game repo is also live now at github.com/brockwc/path-of-rust, with CI running on every push. There is nothing complicated with how I set up github actions.

Step 1 of my build plan is complete: users can interact with a playable "character". The app takes over the terminal, renders a header and a green "@", and you move with wasd or the arrow keys; q or Esc quits. Pressing movement keys emits an event and I handle that event with a method that matches the input to an item in a Message enum. Two unit tests cover it, one for basic movement and one for staying on the map. I built it in five small commits, each one ending in a compile or a run, so mistakes surfaced right where I made them.

I also made progress in the rustlings exercises after last week's pause: the vecs, move semantics, structs, and enums sections are done, plus the first strings exercise. I still have to finish the strings exercise and the error handling exercise. While I am still using the book regularly to check on syntax, I am not reading full chapters as much as I thought I would be.

Plan for next week: turn the full map into actual data and render the first room, introducing some new challenges like collision handling (with walls, furniture, etc.) and a little bit of art as I need to figure out a system for representing elements of the world to the player consistently.

I don't have any blockers right now.
