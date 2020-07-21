---
title: Teleporting
module: 5
jotted: false
---

# Teleporting

Teleporting the Player
It is possible to teleport a player from one area in a Scene to another, or between different levels.
Teleporting within a Scene
To teleport the player within a Scene, we need to set up a transition. For this, we’re going to make two prefabs:
TransitionStart
TransitionEnd
First we need to setup the starting point of the transition:
In the Project window, go to Prefabs > SceneControl
Find the TransitionStart Prefab
Drag TransitionStart to the Scene View. Place it at a position where the player will touch the Collider (the green box) when walking. In the example above, we’ve placed it on the other side of the door:

To set up the destination;
Drag another TransitionStart Prefab from the SceneControl folder into the Scene View
In the Inspector, rename this to TransitionEnd:

Now let’s link the two together:
In the Hierarchy, select the TransitionStart GameObject
In the Inspector, find the TransitionPoint Component
Drag the Ellen GameObject from the Hierarchy into the Transition Point Component’s Transitioning Game Object slot
Set Transition Type to Same Scene

This ensures that Ellen is the only object teleported, and that she is teleported within the same Scene.
Now let’s set the destination:
Drag the TransitionEnd GameObject into the TransitionPoint Component’s DestinationTransform slot
Set Transition When to On Trigger Enter
On Trigger Enter means that the Transition only activates when the player enters the Collider and not on a key press. If you’d rather teleport only when the player press the interact key (E), set Transition When to Interact Pressed.
Teleporting to another Scene
To make the player transition to a new Scene, we need two prefabs:
TransitionStart is the same prefab we used in the previous section; it “sends” the player to the destination. It contains a Transition Point Component, which defines all the properties for where the teleportation starts, and where the teleportation should take the player. Place this prefab where you want the transition to start.
TransitionDestination is a prefab which “receives” the player. It contains a Transition Destination Component. Place this prefab in a different Scene, where you want the transition to finish.
Setting up TransitionDestination
Let’s set up the destination first, so that we have all the information we need later when we set up the start point. To add a transition to a Scene, open that Scene, navigate to the Project window, and go to Prefabs > SceneControl > TransitionDestination. Place it in your Scene, in the location you want the teleporter to lead to.
The TransitionDestinaton prefab contains a Scene Transition Destination Component:

First, set the Destination Tag to a letter. It doesn’t really matter which letter, as long as it is the only Scene Transition Destination Component in this Scene with that letter.
Next, tell it which GameObject it should expect to receive. Drag the player GameObject (Ellen) from the Hierarchy window to the Transitioning Game Object slot.
Finally, make sure your destination Scene is in your Editor’s Build Settings. To do this, go to File > Build Settings and click Add Open Scenes.
Setting up TransitionStart
These settings are mostly the same as they were in the previous section, with a few changes:

Set Transition Type to Different Level
Set New Scene Name to the Scene you want to send it to.
Set Transition Destination Tag to the Destination Tag letter you set in the Transition Destination Component.
Example
Let’s make the player teleport to the first level of the game. In your Transition Start Component, change the settings as follows:
Set Transition Type to Different Level
Set New Scene Name to Zone1.
Set Transition Destination to A

Press Play, and walk to where the transition is. You should travel all the way to the start of Zone1!