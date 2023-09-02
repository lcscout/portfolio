---
title: "Game Dev Study: Prototype 2"
date: 2021-07-28
publishDate: 2021-08-06
draft: false
description: "A Prototype to experiment and study multiplayer and networking in Unity."
layout: "project"
author: lcscout
tags:
    - Arena
    - Multiplayer
    - Unity
    - Study Project
    - Prototype
    - Unavailable
projectLinks:
    enable: true
    github: "https://github.com/lcscout/gdstd-2-unity"
    demo: "https://play.unity.com/mg/other/webgl-builds-49946"
image: /images/projects/gdstd2.png
---

<br>

I started to be interested in multiplayer so I did this prototype experiment to test some solutions and learn about networking.

<br>

## Download
---
You can download the latest release [here](https://github.com/lcscout/GDSTD-Prototype-2/releases/tag/v0.0.1). Although the **servers are down** you can always build it from a [clone](https://github.com/lcscout/gdstd-3-unity) and deploy your own server.

<br>

## Afterthoughts
---
Although I tested some other solutions, like [MLAPI](https://github.com/Unity-Technologies/com.unity.netcode.gameobjects) and [Forge Networking](https://github.com/BeardedManStudios/ForgeNetworkingRemastered), I kept using [Mirror](https://assetstore.unity.com/packages/tools/network/mirror-129321). My goal was to do something peer-to-peer (P2P) because I thought that way I wouldn't need to have a server, but I learned that the usual thing in P2P is to actually have a central server that helps the users connection with each other. Trying to do a decentralized P2P connection was way out of what I could do at the time.

Then I found [Noble Connect](https://assetstore.unity.com/packages/tools/network/noble-connect-free-141599), which is a cloud solution for doing the whole thing of keeping a relay server to help the connection of the users. I didn't really like to use an abstraction but I decided to learn things step by step, and learn how to create a relay server later.

One big mistake I made on this study though, was that I overscoped. I tried to turn it into an actual game without putting much thought in to it, instead of keeping it a prototype. Because of that I lost track of the code and the project was a mess with everything I was testing, making work on the project very frustrating ☹️
