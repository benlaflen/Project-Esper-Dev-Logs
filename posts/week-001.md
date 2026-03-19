---
title: Introduction
date: 2026-03-19
number: "001"
tags: meta, vision
excerpt: Overview of the game and current Project status
---

Hello y'all,

This site is going to be dedicated to hosting developer logs as I build Project: Esper. For today's first post, I ought to start out by covering where we're at, where we're going, and what we're doing. So without further ado...

## What is Project: Esper

It's a traditional roguelike directly in the vein of Nethack, Angband, and the original Rogue. While some inspiration is drawn from other semi-traditional roguelikes like Caves of Qud and Cogmind, structurally Project: Esper is much closer to those original precursors. You play as a hero with some stats and items in a big procedurally generated dungeon descending deep into the earth, with many branches, trials, monsters, and quests ahead of you. Your goal is to descend into this dungeon, dealing with all the boogeymen and accumulating more items, knowledge, and overall exploiting every mechanic the game has to offer to claw your way into being as strong as possible and hopefully manage to survive. When you inevitably meet a grisly demise, you restart back at the beginning to try your hand at a new dungeon, tell a new story, and find some cool new stuff to help you hopefully do a little better.

## Why is Project: Esper

I really like traditional roguelikes. The level of knowledge, mechanical mastery, and depth of simulation they allow for is truly unmatched in the video game genre. But, having played quite a few at this point, I see a consistent problem: the endgame. The problem with really deep, manipulable, mechanics, is that, well, the player will learn to manipulate them, and that means power-scaling and endgame kits become a thing. A checklist of items or effects that win the game if you acquire them. But even then, once you have all the stuff, you don't just win. You still have to fight through the rest of the dungeon and close it out, which takes time. So the question was, how can we keep the game interesting even once the player has a full endgame kit and is strong as Zeus?

Well, I think that Nethack's lategame is a good example of the problem and solution. Apologies for spoilers. About halfway through the game, the player reaches a Castle. After this they still have to trek through 40 more levels of the underworld, do several sidequests, then manually trek all the way back up the dungeon to reach the endgame. But the point is, by the time the player gets to the castle, they generally have or can assemble their full endgame equipment kit. And so for the rest of the game, their build doesn't substantially change, even though half or more of it is still left by level count. Without any significant combat or environmental changes, the entirety of the underworld and return trip is essentially homogenous and interminable. It's an attrition match, sure, but more of the player's patience than gear. But at the very end of the game, the player reaches the elemental planes. This is a series of 4 different, very special levels with unique environmental hazards and requirements. And then comes the very last level, the astral plane. The player's goal is (without being too explicit) to reach a particular furniture object out of 3 possibilities. But the level is embroiled in chaos, including powerful spellcasters, procedurally generated enemies, and 3 immortal bosses with unique attack rules that aren't present anywhere else in the game. This poses a **very** different kind of challenge, and requires new tactics and defenses to deal with, because despite being immune to everything in the game up to this point, the player is suddenly mortal again and vulnerable in very new ways.

The key is attack surface, and a good way to think about that principle is in terms of questions and answers. Each type of attack presents a question, and each defense that counters an attack is an answer. So the player is asked, "What do you do about fire damage?" An item that says "You are immune to fire damage" very succinctly answers that question. But that's not interesting because it reduces the overall questions, and therefore attack surface. An item that instead says "While touching water you are immune to fire damage" answers a question and asks a new one. Because we can now answer the fire damage question, but now we're asked "How can you make sure you're touching water?" It's a *different* attack surface, it's a more *complex* attack surface, it's potentially a *harder* attack surface to effectively exploit, but it is nonetheless a vulnerability. The fundamental design philosophy of Project: Esper is that every effect should non-strictly increase the attack surface; that is, never decrease it. Thus, in the late game, effect dependency trees get very convoluted indeed, but:

- All the basics are still covered: damage, defense, resistance, etc.
- We can gaurantee there is *some* vulnerability that can be exploited at any given time

This, in turn, allows for interesting problem-solving gameplay even into the lategame or once a build is complete.

## How is Project: Esper

Still very early development. With that said, two points:

First, we have the game engine working. We've built an internal demo (that frankly could implement Rogue) to get our basic data types and simulation structure figured out (we'll talk more about this in future weeks) so there is already a technically playable roguelike.

Second, the main engine for effects in Esper is a custom DSL (that stands for Domain-Specific Language), basically a custom, fully-fledged programming language designed specifically for enumerating effects for the game. We are currently implementing the language (more on this as well in the future). While it's being implemented, there is not much to show (or even test), but once it is up and running and integrated, we will be able to add content extremely quickly. This is the opposite model of most projects, because they need something flashy right off the bat for funding, build a vertical slice, and then can't get the rest of the tech working. We're going to have our architecture and engine ready for anything we throw at it. We do have certain mathematical guarantees about correctness, so we aren't flying completely in the dark, though.