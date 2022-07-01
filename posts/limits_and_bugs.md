---
title: Limitations and Bugs v1
description: Porting fun mountain game to browser, what could go wrong? So here's a little summary of bugs.
date: 2022-06-30
tags:
  - bugs
layout: layouts/post.njk
---
The web version is not 100% perfect in matching the original game. Here are some slight problems I discovered during testing. 
# Limitations
* Mods are unsupported. Main reason I can't just throw Everest in there is because MonoMod is upset that I changed out the FMOD. 
* Performance is bad on the following areas: The maze of Huge Mess, Reflection's Lake (lots of water there, could be related?), last room of Farewell (probaly due to the huge size of the room). 
# Bugs
## Major (usually gamebreaking)
* Core Blocks yeet you to the nearest left/right wall. Not sure why it does that.

<video src="/video/core_block_yeets.mp4" controls></video>
* Firefox has a really hard time getting good fps for some reason especially at the sections outlined in Limitations.
* DOES NOT WORK IN IOS SAFARI YET. How in the world I will debug for ios I don't know yet. Perhaps a custom onError.
* Improper coordinates are used for casette block textures. Annoying especially with big casette blocks. 
![Casette go transparent](/img/recon_casette.png)
   
## Minor
* Lighting texture is calculated wrong
* Immediately entering the Presidential Suite, Madeline is tped to (0,64) and starts flying due to an unknown force. During that time the camera sees an empty room. This was somewhat fixed by making transitions not wait for you to move to the proper position, so you die first and then trigger the cutscene. The cutscene then partially completes and stalls. You then need to skip the cutscene and it'll result in another death afterwards the mysterious flying will actually stop.
* Bird catching cutscene before Farewell section needs to be skipped.
<video src="/video/bird_stuck.mp4" controls></video>
* Bird doesn't always render properly. Sometimes we might see a bird doing the flying animation but not actually changing it's position.
* In a lot of cutscenes, whenever the camera zooms, it zooms at the wrong section of the scene. 
* Related to the above, some text/overlays do not render at the correct position.   
* Funny Graphical Glitch: Badeline's hair looks like it's made out of a bunch of triangles so it's all spiky. 
![Badeline has a Bad hair day](/img/bad_hair.png)
* Pressing escape while fullscreen will exit fullscreen but the game is not aware. You have to go to options and retoggle fullscreen. A workaround is to open devtools and do a `navigator.keyboard.lock()` on supported devices, that way you hold escape to actually exit fullscreen. 
* Abnormal shadows/outlines of text
![Titlescreen Bug](/img/titlescreen_text.png)
![Shadow overboard](/img/shadow_gone_too_far.png)
* Abnormal shadows/outlines of dash crystals and fireballs
![Fireballs and Dash Crystals in Core](/img/core_fireballs.png)
* The death wipe for Ch2 looks like a toddler scribbling furiously (not pictured). 
# Intentional Features
* Exclusive property in Binding is missing. This was a workaround because XmlSerializer kept serializing it when it was supposed to be ignored and it contained a reference to Binding so it'd error out with a circular reference error.
* Options screen says "Da Options". This is intended to be a quick and easy way for me to check if I'm running the modified version or not. (probaly might disable later to be more friendly to non-english users)
* Save files may not be 100% the same as their vanilla counterparts, some stuff is being serialized that shouldn't like audio stuff, however it doesn't seem to be enough to cause a problem. 
* Audio loops when the game exits. This is probaly because the game's shutdown method is actually never called, it just stops running Update calls. Haven't found any side effects yet for now. 
* Game doesn't load under http: AudioWorklet for FMOD WASM requires a secure context.
# Audio
And yes audio works, just doesn't sound great when your pc is lagging.
<video src="/video/reconcilation_1.mp4" controls></video>