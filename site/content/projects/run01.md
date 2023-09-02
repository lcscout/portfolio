---
title: "Run01 'til Mayhem"
date: 2022-01-09
publishDate: 2022-04-03
draft: false
description: "A side-scrolling endless runner game for mobile."
layout: "project"
author: lcscout
tags:
    - Endless Runner
    - Mobile
    - Unity
    - Study Project
    - Available
projectLinks:
    enable: true
    github: "https://github.com/lcscout/run01-unity-game"
    demo: "https://github.com/lcscout/run01-unity-game/releases"
image: /images/projects/r01-Gif.gif
---

<br>

Run01 is a side-scrolling endless runner game for mobile where you're helping a mutant experiment with its task. The game is similar to Chrome's Dino Game, with a twist on having two runnable planes and being able to teleport between them. Collect the dark stones and keep running, until mayhem.

<br>

## Contributions
---
As the sole dev, I pretty much designed and crafted everything but the assets themselves (sounds, models, etc).

Some noteworthy systems I fully implemented:
- The endless-runner gameplay
- The UI & UX for mobile
- The player controller
- The skins system, and
- The audio manager, capable of handling multiple tracks

<br>

## Play the game
---
Download it [here](https://github.com/lcscout/run01-unity-game/releases).

<br>

## Tech in-depth
---
Well, the game was made using Unity and C#. And, although I'm still very newbie to software architecture and design patterns I wanted to practice so I first structured the project following a MVC-ish design structure, in particular for having the data separated.

Since my goal was to decouple as much as I could without sacrificing understandability (since I was going to publish the game as open source), I mostly written event-driven systems, but — seeing now that is finished — I also mixed in some singletons here and there which are totally against my goal and probably made the code worse to understand, specially in some systems that had characteristics of both (in these, I should've just committed to the singletons, for simplicity's sake, or tried to make them event-driven single instances).

Looking back at everything now I realized that since I mostly used event-driven architecture I could have created an Event Manager for subscribing events where they're needed without making it manually — as I did. For a game of this size probably wouldn't make a significant difference but this is something I'll definitely keep in mind for the next projects.

### Endless-runner gameplay

What I did was to keep the player still while everything else moves towards him/her. The player has a base speed (actually the speed of objects) that is increased any amount by time — both configurable, the to-increase quantity and the to-repeat time.

Besides, to truly make the impression of it being endless the environment assets should be seamlessly doubled. That way when the object is too far it's simply translated to a nearer position hence, because it's doubled, the infinity illusion.

##### Code Snippet - Infinite Move Left

Below is the snippet that handles this. The `_repeatWidth` takes in account that the object **x** position is 0 (and also that it has a *BoxCollider* attached to it).

{{< gist lcscout a4827c59c100a2ee1c9771f75241a752 >}}

### Spawner logic (for collectables and obstacles)

For this I created a base class called *Hitable* which handled the common methods like moving towards the player, defining the spawn rate, etc. Them, the inherited classes *Collectable* and *Obstacle* implemented specifics functions like what to do when collide with something and generating a random position for every spawn.

The spawner, or better, the spawners ****(one for each inherited class) receives an array of *Hitable* prefabs and creates an object pool for each element. Each time there's a call for a spawn they check if it should spawn (according to the spawn rate of the object) or try another.

##### Code Snippet - Spawn Manager Core

While the game was running (not in menu) the spawner would keep spawning at a configurable rate.

{{< gist lcscout 26282e31ed45079017cdfa27c8a6835a >}}

Below is the spawn method, it selects a random pool and sets the kill behaviour (just a release back to the pool), them it checks whether that hitable is supposed to actually spawn or not, and if not the spawner tries another.

{{< gist lcscout df30b4956496117237b95c2d67f982e2 >}}

### User Interface implementation

I've used only one scene because of it's complexity — or lack of — so the UI was pretty simple to implement. I created an UI Manager that was an event-driven single instance and whenever another system asked for an element from the UI the manager handled it by properly coroutining and waiting animations before showing or hiding the proper element.

### Skins system

For the skins system I've created a *Skin* model that holds an array of materials (needed because the model I used has multiple materials) and a *Condition*, which in turn is a model that holds all the information for unlocking a skin.

The system class itself holds a list of skins and their configurable conditions, simply accessing the *Condition* model of a skin whenever needed.

##### Code Snippet - Condition Model

{{< gist lcscout 924a314ef61e8adbc2ec091ebabf31b6 >}}

### Audio manager
Quite simply the audio manager handles a list of *AudioSources*, each of which I call a **track.** For every method (except for a few that changes all the list) is given the number of the track and they proceed to perform their action (play sound, stop, etc) on the respective track.

<br>

## Afterthoughts
---
This project was quite fun to do. My ultimate goal was a simple game, one that I could actually publish, something I haven't done yet. So, I took the simplest game I could thought of (Chrome's Dinosaur Game) and built on top of that, for mobile — because it's was also something I haven't tried. 😎

Well, because of the mistakes I was doing in my projects regarding planning stuff in this one I tried to spent more time in that stage and I think it actually paid off, specially for the coding because I already had a base of the systems I would use and how I'd build them.

One thing that I didn't like though was that I had this objective of doing all the assets by myself, you know, so I planned for doing these assets to match the game initial's concept (the player would be a monkey that would run on top of a trunk) but making assets is not my strongest skill so It was taking a lot of time (and also looking pretty bad 😛) which went the opposite of another objective I had — don't take too long to finish.

In the end, I decided to use third party assets — I'll probably keep using them until I'm comfortable making my own. Besides, the game concept changed because of that but the only downside was the flexibility for making new skins.

Overall I had a great time and learned a lot concerning mostly mobile and optimizations. The game is available as an APK in my [github](https://ww.github.com/lcscout), funny story about that: I didn't know that I had to pay to publish in a store, yeah I know should've thought that, looking now it's seems pretty obvious 🥲. Anyway, until I'm able to afford that it will stay an APK.
