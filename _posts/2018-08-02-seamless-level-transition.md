---
layout: post
title: "How to make a seamless level transition in Unity."
---
How to make a seamless level transition in Unity.

We are trying to make the scene transitions between the main hub and the puzzles as seamless as we can.

A lot of feedback from the previous build of the game mentioned the abrupt scene changing.

Ideas

- Walk into elevator which closes and opens again in the new scene.
- Fade in an out when loading a level.


##### notes

- level loads, the departing elevator loads into the new scene. player is unparented from the elevator.

<iframe width="560" height="315" src="https://www.youtube.com/embed/3xB1tAUf9gE" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

##### things achieved
- Elevator will not destroy itself upon a new scene load.
- DontDestroyOnLoad elevators will position themselves at the designated elevator entry points.
  - the transform.position of these copied elevators will be matched with the transform.position of the elevator entry object.
  - *TODO* Need to fix the way rotation is brought over from the previous scene. It seems to be an issue with the mouselook rotation.
    - Ok so, the teleporting elevator retains its rotation in the destination scene. We can use this to fix this problem. Just align the rotation of the departing elevator with the rotation of the destination elevator entry point. To make this easier, use only increments of 90 degrees.
- *BUG* HeavyDoors stay open once triggered open. Removing its power does not return it back to its original state.
  - I have no idea why this could be.
