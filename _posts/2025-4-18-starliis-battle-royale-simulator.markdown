---
layout: post
title: "Starlii's Battle Royale Simulator: Python Edition"
categories: "project"
author: "Starlii"
---

A long time ago, I created a Scratch project similar to those Hunger Games simulators on various websites around the internet. I never expected to do much with it, but it was fun to develop and mess with. However, about five months ago, following my boost in Python confidence after the creation of Vivia, I decided to give the entire thing new life in the programming language I've spent way too much time in. Thus, let me tell you the tale of the development story of Starlii's Battle Royale Simulator (SBRS).

## Scratch Version

The original Scratch version had several features I was pretty proud of for my Scratch skills at the time:

- Games could be saved and then replayed
- Players could have "playertypes", which determined additional actions that they could take
- Theoretically infinite players
- A GUI built with [-Rex-'s](https://scratch.mit.edu/users/-rex-/) [Pen Text Engine++](https://scratch.mit.edu/projects/406678232/)

However, it really wasn't very useful as it was running in Scratch (which also made it hard to find and fix bugs/add new features).

## Rewrite: Part 1

I rewrote the entire thing in Python around December 2024. This version didn't actually work; rather, it just played a very basic game with little to no customization. It didn't have any fancy playertypes or GUI or even saving. Kinda boring.

## Rewrite: Part 2

In February 2025, I remembered the rewrite existed and decided, "eh, why not, let's mess with this" (which in hindsight was probably the best decision I could have ever made). It took a while and a lot of bug fixing, but eventually I got it working very similar to the Scratch version.

For this version, players and playertypes could be defined in text files, which would be loaded by a configuration JSON file. Actions were hardcoded, and there was no addon support, meaning to modify the game behavior beyond the simple config file, you'd have to make modifications to the game script. I also implemented colored messages with one of my favorite third-party libraries, [Colorama](https://pypi.org/project/colorama/). This version was pretty good, but I would eventually implement the best change ever...

## Rewrite: Part 3

Addons are real. I rewrote the main game behavior into an addon, and exposed a lot of information about the game in classes that could be accessed by an addon that you'd load by dropping it into the addons folder. This led me to realize how to actually build and organize an object-oriented structure in Python, which is something I will absolutely be using in future projects. I even made a miniature Pokémon addon that turned the entire game into a Pokémon battle royale where a Jirachi can use Sandstorm against a Milotic for exactly 8 damage. Not kidding. That is possible.

## It's out now

At this point, I've been keeping this from the world for too long. If you want to use it, it's ready for you, and the source code is on [GitHub](https://github.com/Starlii10/sbrs). Can't wait to see what horrific battle royales people come up with.
