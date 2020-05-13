---
title: Mouse Events
module: 11
jotted: false
---

# Mouse Events

We can interact with our sketches using the mouse too. How do we do that?  We can use the **mousePressed** function to respond when pressing the mouse, and we can use the **mouseClicked** function, to respond when pressing and then releasing the moused.  We can also use the **mouseMoved()** function to respond to the mouse moving across the screen.

Let's look at mousePressed.

## mousePressed

Starting with our previous code, we an integrate mousePressed like this.

```js
    var x = 50;
    var y = 50;
    var diameter = 25;
    var mousex = 0;
    var mousey = 0;
    function setup() 
    {
      createCanvas(800, 600);
    }

    function draw() 
    {
      background(0);
      fill(24, 200, 29);
      circle(x, y, diameter);
    
      if (x >= 300) 
      {
        x = 50;
      }

      if (keyIsDown(83)) 
      {
        y += 10;
      } 
      else if (keyIsDown(87)) 
      {
        y -= 10;
      }

      if (y >= 300) 
      {
        y = 50;
      }

      if (diameter < 200) 
      {
        diameter += 2;
      } 
      else if (diameter >= 200) 
      {
        diameter = 25;
      }

      circle(mousex, mousey, 30);
    }

    function mousePressed()
    {
        mousex = mouseX;
        mousey = mouseY;
        
    }
    function keyPressed() 
    {
      if (key == 'd') 
      {
        x += 10;
      } 
      else if (key == 'a') 
      {
        x -= 10;
      }
    }
```

Now a circle is drawn whenever we click the mouse.  It appears right when we click the mouse.

What about the mouseClick function?

## mouseClick

```js
        var x = 50;
    var y = 50;
    var diameter = 25;
    var mousex = 0;
    var mousey = 0;
    function setup() 
    {
      createCanvas(800, 600);
    }

    function draw() 
    {
      background(0);
      fill(24, 200, 29);
      circle(x, y, diameter);
    
      if (x >= 300) 
      {
        x = 50;
      }

      if (keyIsDown(83)) 
      {
        y += 10;
      } 
      else if (keyIsDown(87)) 
      {
        y -= 10;
      }

      if (y >= 300) 
      {
        y = 50;
      }

      if (diameter < 200) 
      {
        diameter += 2;
      } 
      else if (diameter >= 200) 
      {
        diameter = 25;
      }
      ellipse(mousex, mousey, 15, 50);
     
    }

   
    function keyPressed() 
    {
      if (key == 'd') 
      {
        x += 10;
      } 
      else if (key == 'a') 
      {
        x -= 10;
      }
    }

    function mouseClicked() 
    {  
      mousex = mouseX;
      mousey = mouseY;
    
    }

```

To test out the difference, you have to press down and then release the mouse.  Now, the ellipse draws to the screen.  What about the last one? mouseMove().

## mouseMove

mouseMove tracks the mouse as it moves across the screen.

```js
        var x = 50;
    var y = 50;
    var diameter = 25;
    var mousex = 0;
    var mousey = 0;
    function setup() 
    {
      createCanvas(800, 600);
    }

    function draw() 
    {
      background(0);
      fill(24, 200, 29);
      circle(x, y, diameter);
    
      if (x >= 300) 
      {
        x = 50;
      }

      if (keyIsDown(83)) 
      {
        y += 10;
      } 
      else if (keyIsDown(87)) 
      {
        y -= 10;
      }

      if (y >= 300) 
      {
        y = 50;
      }

      if (diameter < 200) 
      {
        diameter += 2;
      } 
      else if (diameter >= 200) 
      {
        diameter = 25;
      }
      ellipse(mousex, mousey, 15, 50);
     
    }

   
    function keyPressed() 
    {
      if (key == 'd') 
      {
        x += 10;
      } 
      else if (key == 'a') 
      {
        x -= 10;
      }
    }

    function mouseMoved() 
    {  
      mousex = mouseX;
      mousey = mouseY;
    
    }

```

Now, you see the ellipse move with the mouse.  Pretty cool, right?  

<a href="https://umontana.zoom.us/recording/play/p-eUujm2CKkolQvO8PJN31LqJiqkqgWNRR4VAlpO8cUlyXnu6BDMFrLSH-2W-8It?autoplay=true&startTime=1572815264000" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>