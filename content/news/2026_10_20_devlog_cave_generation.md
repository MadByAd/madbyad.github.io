---
title: "Developing Cave Generation for Our Craft-Like Game"
date: 2026-10-20
image: "/images/2026_10_20/image_8.png"
summary: "Its not a craft-like (voxel) game without an underground exploration. In this post we will tell our story of developing cave generation"
tags:
  - Devlog
  - Gamedev
  - Game
categories:
  - Development
---

Its not a craft-like (voxel) game without an underground exploration. But cave generation isn't an easy thing to made, there was multiple attempts and iteration to get the cave generation algorithm as what we needed. We need a cave generation that feels like the pre cave & cliffs Minecraft, yet also included large open underground space for an underground biome, enemy, and even boss fight (it. still an idea though).

![Minecraft Cave](/images/2026_10_20/image_1.jpg)

*credit: windowscentral.com*

## River Method

generating a river using Perlin Noise was easy, you just grab the middle value, and you get this result. At first we though this method could be used for generating 3d tube or worm like cave but we were wrong. turns it doesn't look as what we wanted.

![Noise Texture for Generating Rivers](/images/2026_10_20/image_2.png)

at first we thought generating 3d caves would be as simple as generating a river (see image above). Generating river works by grabbing the middle value of the noise, but it turns out it didn't quite work in what we expected

![Cave Generation using the River Method](/images/2026_10_20/image_3.png)

## Double Noise Test

after a bit of searching, we found out that to get better result, we must merge two 3D noise and get the highest value in order to get a more better looking cave, and it turns out it did, it looked better than previously.

![Noodle Cave](/images/2026_10_20/image_4.png)

We decided to keep this for later an call it noodle cave type. although this wasn't the worm / tube like cave that we wanted.

## The Worm Algorithm

it turns out, to generate a worm looking cave, we don't use noise function, instead we simulate a worm that drill and make path underground, the code is quite complex but this resulted in a cave that we were looking for. We decided to call this worm cave, we were planning to have cave types.

![Worm Cave](/images/2026_10_20/image_5.png)

## Cheese Cave

The last cave type we wanted to include is what we call cheese cave, this cave type is much more easier to implement, although at first the cave were symetrical in vertical and horizontal. But we quickly found out, that if we wanted a more flat horizontal cave, we must squish / scale the noise

![Cheese Cave](/images/2026_10_20/image_6.png)

## Combining the Three

Our game has 3 cave types, worm, noodle, and cheese. But how could we generate and balance between the 3 cave types? We used another noise map which we called `cave_openness` which determine whether the area is very open (it has worm, noodle, and cheese) or closed (only has worm).

![Cave Openness Noise Texture](/images/2026_10_20/image_7.png)
![Cave Generation](/images/2026_10_20/image_8.png)

## Summary

Creating caves that feel natural while supporting large underground spaces took several iterations. We experimented with different generation techniques, from Perlin Noise to a simulated worm algorithm, eventually developing three cave types: Worm, Noodle, and Cheese. By introducing a `cave_openness` noise map, we combined these cave types to create varied underground environments, ranging from narrow tunnels to vast open spaces.

![Terrain Generation](/images/2026_10_20/image_9.png)

And that's how we brought our underground world to life! There's still plenty of room to expand these caves with unique biomes, enemies, and perhaps even a boss fight someday.