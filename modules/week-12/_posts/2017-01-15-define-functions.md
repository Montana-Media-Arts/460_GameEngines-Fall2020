---
title: Create Our Functions
module: 12
jotted: true
---

# Create Our Functions

How do we create more complex functions?  Let's start with where we left off.

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

What can put into a function?

Let's make a few changes.

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

      // call the function created
      controlCircle();

      ellipse(mousex, mousey, 15, 50);
     
    }

    /* This function controls all the variables of the circle */
    function controlCircle()
    {
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

What did we do?  We created a new function called **controlCircle**, which handles all variable changes with the circle, including keyboard events and what do when we leave an area as well as change the size of the circle.

## Functions in Functions

We can even call a function instead of a function.  Do we do that?  Let's first define another function.

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

      // call the function created
      controlCircle();

      ellipse(mousex, mousey, 15, 50);
     
    }

    /* This function controls all the variables of the circle */
    function controlCircle()
    {
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
        
        // we call the function here.
        changeDiameter();

    }

    // This function updates the size of the circle
    function changeDiameter()
    {
        if (diameter < 200) 
        {
            diameter += 2;
        } 
        else if (diameter >= 200) 
        {
            diameter = 25;
        }

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

We create a new function called **changeDiameter**, and then we called the new function in the **controlCircle** function.  Cool huh?

Why do we do this?  (Always a good question and you should always ask this question). We want to separate our code and make things more readable.  We created the first function **controlCircle** to reduce the amount of code in the draw.  We don't want it to get too crazy in there.

Then, we created the changeDiameter so that we can reduce some code in controlCircle.

Finally, let's add **myCircle** function into this.

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

      // call the function created
      controlCircle();

      ellipse(mousex, mousey, 15, 50);

      myCircle(800,600);
      myCircle(800,600);
     
    }

    /* This function controls all the variables of the circle */
    function controlCircle()
    {
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
        
        // we call the function here.
        changeDiameter();

    }

    // This function updates the size of the circle
    function changeDiameter()
    {
        if (diameter < 200) 
        {
            diameter += 2;
        } 
        else if (diameter >= 200) 
        {
            diameter = 25;
        }

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

    function myCircle(x,y)
    {
        fill(Math.floor(Math.random()*256),Math.floor(Math.random()*256),Math.floor(Math.random()*256));
        circle(Math.floor(Math.random()*x)+10,Math.floor(Math.random()*y),Math.floor(Math.random()*100)+10)
    }

```

Did you see the circles?  Wow right?  Let's go onto the homework.

<a href="https://umontana.zoom.us/recording/share/qulcCEV49wgQRpcphjmCAosNTZYJkLZyku_bMA8pPliwIumekTziMw
" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>