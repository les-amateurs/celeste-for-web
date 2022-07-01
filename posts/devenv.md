---
title: Dev Environment
description: Proper dev environment recommendations.
date: 2022-06-25
tags:
  - howto
layout: layouts/post.njk
---

The requirements for recompiling Celeste into a web browser runnable version are a bit tedious. Due to the nature of the ahead of time compilation, you'll need Windows Subsystem for Linux. According to the docs it does not matter that much whether you use WSL 1 or 2, however 1 might be faster for this use case. However I ended up setting mine with WSL 2 before reading that bit of documentation. 

Also for audio, only FMOD 2 has a webassembly version but Celeste's bank files are on an earlier version so we'll need to regenerate the bank files from the public Celeste FMOD project.  Simply download the project and open it with fmod studio 2 and it should automatically upgrade it. Then rebuild the bank files as needed. Instead of putting them in the Desktop folder, we'll be putting them in the Web folder later on.

If you've already gotten a setup suitable for making Everest mods then **GOOD JOB**! If not you should probaly get one. In addition since the packaging runs on .NET 5 you should get .NET 5 installed. 

Throughout this "DIY" tutorial I will be referencing a couple of things. 

# Resources (for when you are stuck)
* Google and other search engines
* [The FNA to WASM gist](https://gist.github.com/TheSpydog/e94c8c23c01615a5a3b2cc1a0857415c)
* [Massive Uno Wasm Bootstrap 2.1 README](https://github.com/unoplatform/Uno.Wasm.Bootstrap/tree/2.1)
* [XNA Reference](https://docs.microsoft.com/en-us/previous-versions/windows/xna/bb196942(v=xnagamestudio.10))

Remeber, FNA aims to be a better reimplementation of XNA!
* [FNA Source](https://github.com/FNA-XNA/FNA)
* [Everest Wiki for Modding](https://github.com/EverestAPI/Resources/wiki)

# A few other things we'll need