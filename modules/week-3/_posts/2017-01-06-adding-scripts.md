---
title: Adding Scripts
module: 3
---

# Adding Scripts to Project

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Adding</button>
  <button class="tablinks" onclick="openTab(event, 'Project')">Project Window</button>
<button class="tablinks" onclick="openTab(event, 'Component')">Script as a Component</button>

</div>

<div id="Overview" class="tabcontent" style="display:block">

<p>If we use existing scripts, we can design a game with custom assets.  This gives us the ability to create prototypes and create proof of concepts before diving into the customization of game programming.  It also allows game designers to focus on what is most important to them - game play.</p>

<p>If you want to move scripts over from your Playground project, copy the <b>Scripts</b> and the <b><i>_INTERNAL_</i></b> folder into your <b>Assets</b> folder.  Then, you will need to change the following in the code.</p>

<div style="background-color:blue;color:white">
  [AddComponentMenu("[name of Playground project]/Movement/Auto Move")]
</div>
to
<div style="background-color:blue;color:white">
[AddComponentMenu("[new project]/Movement/Auto Move")]
</div>

</div>
<div id="Project" class="tabcontent">

<p>In the Project window, you will find the movement scripts.</p>

<p><img src="../imgs/MovementScript.png" alt="Movement Scripts" /></p>

<p>After this script is found, then you want to drag the script into the Inspector window to add it to the object.</p>

<p><img src="../imgs/DragScript.png" alt="Drag Script" /></p>

</div>
<div id="Component" class="tabcontent">

<p>Notice that after the script is added as a component, it adds not only the script, but also the RigidBody2D which is what allows the object to interact in the scene.</p>

<p>Don't forget to adjust the gravity so the object doesn't fall straight down.</p>

<p><img src="../imgs/ComponentsAfterScript.png" alt="Components after Script" /></p>

<p>Finally, press play to see how the script and the object work together.</p>

<p><img src="../imgs/PressPlay.png" alt="Press Play" /></p>
</div>
