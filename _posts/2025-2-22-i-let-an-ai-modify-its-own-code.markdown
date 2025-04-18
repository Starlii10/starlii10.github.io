---
layout: post
title: "I let an AI modify its own code: attempt 1"
categories: "project"
author: "Starlii"
---

I had the random idea to create a simple terminal-based chatbot interface and let said chatbot mess with its own code. The idea was simple, but the execution kinda sucked. Here's the adventure I went on.

## Why?

I dunno! I just kinda thought it would be really funny to make, and even more so if it actually somewhat worked.

## Implementation

I already had an implementation of llama-cpp in Python with Vivia and the aptly named `llama-cpp-python` package, which allowed me to locally run LLMs on my machine, since I do NOT want to pay for an OpenAI API key. It needed a few minor changes to make the terminal interface instead of using Discord, but other than that it was essentially the same as what was in Vivia's code already.

The fun part came when I was implementing code replacement! It works by using code blocks, allowing the chatbot to simply show the code it wants to implement. Unfortunately, I ran into several issues, since using the string (insert three backticks here) in any way would be treated as the end of the code, and so anything past that point would not be detected. I tried to make the LLM escape the backticks in its code, but it never listened, and I never ended up getting it to fully work.

## Compiler Issues

I was ready to start testing, but I ran into a problem: on my laptop, the model would run on the CPU instead of the GPU. I tried to fix this, but no matter what I tried, it would either run on the CPU, or run out of VRAM and crash. I tried to switch to my desktop with a 3060 12GB, but I had a lot of trouble installing `llama-cpp-python` with CUDA on there. To quote [llama-cpp-python documentation](https://github.com/abetlen/llama-cpp-python?tab=readme-ov-file#are-there-pre-built-binaries--binary-wheels-available):

> The recommended installation method is to install from source... The reason for this is that llama.cpp is built with compiler optimizations that are specific to your system.

...which requires a C compiler that actually functions. Unfortunately, I had issues with my C compiler toolchain because I added a lot of things to my PATH to allow a previous toolchain for Super Mario 64 compilation to work. I tried a prebuilt version of the package, but every version available was either broken or wouldn't install at all. Eventually, I managed to compile and install `llama-cpp-python` with MSVC, CUDA 12.4, and the Windows installation of CMake. Now I could finally use my 3060 and 12GB of VRAM to run a basic model.

## Testing

Unsurprisingly, my implementation had a lot of issues. It took a lot of work, but I finally got it to replace some code and rerun itself. It did not perform very well, mainly because

1. It's running on a 3060 with 12GB VRAM, which isn't a whole lot in the grand scheme of things. You'd really want a higher VRAM card for local LLMs. Unfortunately, I do NOT feel like spending $1000 on a new GPU to run some silly LLM project (probably more for a new power supply too). I was also running it on Windows, which isn't ideal since it has a lot more background things eating up RAM and CPU; I really should look into moving to Linux for my desktop, since I use Linux for all my laptops.
2. I still had a ton of bugs in my code. The chatbot helped a little, but it would often suggest to replace code with something that either made no sense or simply crashed the program. I had to do it all manually, and that took a long while.
3. LLMs are hard to work with. The Vivia implementation worked pretty well, but that was only because it just needed to take in user input and spit out a message. This project was a lot more complex, and it pushed my Python skills way too far.

## Where Now?

I think I may have to revisit this project later when I have more Python skill. And maybe a 32GB RTX 5090.

I want to make the project open source, but it's not done and it's definitely still absolutely garbage. I do not think anyone would want to touch that bowl of spaghetti. If and when I ever finish it, I'll put it up on GitHub.
