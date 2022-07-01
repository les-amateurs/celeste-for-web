---
title: Intro
description: Here I describe a bit about why I persued this project and why I'm documenting it. 
date: 2022-06-25
tags:
  - howto
layout: layouts/post.njk
---
# Backstory
I first got Celeste actually...according to Itch.io, 99 days ago from the writing of the post. I ended up starting the game on my school's Spring break so I had plenty of time to figure out the game. Like everyone I was somewhat amazed by the game and how fun and frustrating it was at the same time. So I thought, "hey I'd be nice if I could play this in school if I needed to". Unfortunately I actually got the project to a playable amount only one day after school ended. 
# First Attempts
So I managed to google around, to [this helpful gist by](https://gist.github.com/TheSpydog/e94c8c23c01615a5a3b2cc1a0857415c) TheSpydog. After reading some documentation on the Everest modlaoder I managed to use ILSpy to decompile the game. For a while I was actually not able to figure out how to get a meaningful stack trace in the browser so I was very unmotivated for the time being. I ended up writing an Everest to get a feel of how everything works and coming back to it later. 
# Overview
The process pretty much was like this
1. Compile game for web (8 to 11 minutes normally, 5 minutes in Interperter mode)
2. Wait for game to load (1 minute without a lot of optimizations, approx 15 seconds with optimizations)
3. Trace errors, in non-interperter mode you don't always get nice stack traces. Interperter mode works until FNA initalizes it's screen due to a Pinvoke signature bug. 
4. Repeat above