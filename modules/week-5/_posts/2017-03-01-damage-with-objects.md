---
title: Damage with Objects
module: 3
jotted: false
---

# Damage with Objects

Damaging with Objects
In this section, we’ll explore the damage system. To do this, we’ll go through the steps of dropping a box on a Spitter to kill him. Sorry, little guy!
Start by drawing out a level where Ellen is higher up, and the Spitter is on a platform underneath a drop, like this:

Go to Prefabs > Enemies and drag a Spitter into the Scene View
Place him on the lower portion of your level, close to the cliff-face
With Spitter selected, locate the Enemy Behaviour Script
Reduce the View Distance number so that Spitter does not shoot you immediately while you test this gameplay

In the Project Window go to Prefabs > Interactables, and click and drag the PushableBox Prefab into the Scene View
Select the PushableBox in the Hierarchy window, and, in the Inspector click Add Component
In the Search Box, type Damage
Click on Damager to add it to the PushableBox
The Damager Component tells any GameObject that has a Damageable Component on it (like a Spitter or a Chomper) to give it damage. There is more in-depth information on this system in the Components Documentation.

The Damager is represented by a green collision box as shown above. This is the area which causes damage. This is not covering the PushableBox right now, so when we push the box onto the Spitter, it will not damage him.
Let’s move this box so that it’s roughly the size and position of the PushableBox. There are two ways to do this:
Select and drag the green dots on the edges of the green collision box to be over the PushableBox

In the Inspector locate the Damager Component
Adjust the Offset and Size to position and size the collision box. The easiest way to do this is to left-click on the words and drag left and right to scrub through values.

Lastly, we need to make sure the damage is given to the right GameObjects. We separate objects into Layers in the Editor so that they can easily be found and seperated:
Select the PushableBox
In the Inspector, find the Damager Component
On the HittableLayers dropdown select the Enemy Layer

The PushableBox will now cause damage to anything on the Enemy Layer, like our Spitter.
Experiment with causing damage to other enemies, and even Ellen herself!
