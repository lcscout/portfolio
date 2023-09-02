---
title: "Game Dev Study: Prototype 3"
date: 2021-08-13
publishDate: 2021-08-28
draft: false
description: "A simple recreation of the board game Quarto in Unity3D."
layout: "project"
author: lcscout
tags:
    - Strategy
    - Multiplayer
    - Unity
    - Study Project
    - Prototype
    - Unavailable
projectLinks:
    enable: true
    github: "https://github.com/lcscout/gdstd-3-unity"
    demo: "https://github.com/lcscout/gdstd-3-unity"
image: /images/projects/gdstd3.png
---

<br>

This is a simple recreation of the board game Quarto in Unity that was actually meant to be a fully-fleshed out project but it turned out to be just a study subject for online gaming and networking.

<br>

## Download
---
For this game I didn't even created a release because the **servers are down**, so I didn't see a point on creating one. But you can always build it from a [clone](https://github.com/lcscout/gdstd-3-unity) and deploy it on your own server.

<br>

## Afterthoughts
---
It all began with the thought that I wanted to do a online game so I could play along with my friends and also practice newly adquire knowledge on networking from my [last study project](https://lucascoutinho.me/projects/gdstd2). So, while brainstorming ideas I stumbled across the board game Quarto and I thought it would be easy to implement so I went with it. 🤭

I realized it was a bad choice for my purpose right on my first play test because it was only two players and the fun was on being strategic and trying to think ahead of your opponent, that's when I realized that I actually wanted a party game, where you it play casually with the game acting as a catalyst for the fun you'd already been having by just chatting with a group of friends. This was one of the reasons to drop it.

As for a more technical aspect, I had two goals for the network connection: I wanted it to be peer-to-peer; and I wanted it to work with WebGL. However, I didn't want to use Noble Connect again because I thought it abstracted too much, this time I wanted to setup my own relay server. 🌐

I also wanted to test Unity's netcode, MLAPI, but since it didn't support WebGL I stuck with Mirror. I then set up a listen server using Amazon's EC2 and [LRM](https://github.com/Derek-R-S/Light-Reflective-Mirror).

I have to say I loved LRM, although it was still an abstraction it met everything I wanted to do and it was pretty easy to use and understand. It was truly a finding, I was almost changing my plans and restarting the whole project to use another netcode solution. 😮‍💨

Well, in the end I didn't finish it. One of the reasons I already said, the other one was that I was doing [another project](https://lucascoutinho.me/projects/streetracing) in parallel to it. I had various problems with that other project that consequently affected this one as well, and when I decided to put this one in hold to come back later I lost the interest. Still, maybe someday I'll come back to it cuz I had some different ideas that I think it would be cool to implement.
