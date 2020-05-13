---
title: Bouncing Shapes
module: 10
jotted: true
---

# Bouncing Shapes

Now that you know how to make the shape stop, how to we make it go the opposite way when it hits the wall?

Let's start where we left off.

```js

var redColor = 123;
var greenColor = 39;
var blueColor = 21;

var x = 100;
var y = 200;
var diameter = 50;
// this function is called only once
function setup()
{

    createCanvas(800,600);
}
/* this function is called continuously
    while the sketch is open in the browser
*/
function draw()
{
    background(redColor,greenColor,blueColor);
    fill(255);
    circle(x,y,diameter);
    fill(redColor,greenColor,blueColor);
    circle(x,y,25);
    if(x <= 800)
    {
        x+=13;
    }
}
```

The trick is that we need the x to go the opposite way.  How do we make the shape go to the left?  If adding to the x made it go to the right, then yes, subtracting makes it go to the left.  Remember, everything starts at 0,0 in the upper left-hand corner.  So, all we are doing is adding or subtracting to make this work.

So, what if we did this?

```js

var redColor = 123;
var greenColor = 39;
var blueColor = 21;

var x = 100;
var y = 200;
var diameter = 50;
// this function is called only once
function setup()
{

    createCanvas(800,600);
}
/* this function is called continuously
    while the sketch is open in the browser
*/
function draw()
{
    background(redColor,greenColor,blueColor);
    fill(255);
    circle(x,y,diameter);
    fill(redColor,greenColor,blueColor);
    circle(x,y,25);
    if(x <= 800)
    {
        x+=13;
    }
    else
    {
        x-=13;
    }
}
```

Does this work?  What did you see?  Why did it just wiggle?  It actually did go back 7 pixels, but when the draw function runs again, it is less than or equal to 800, and then it tries to go to the right, and then it does this little dance over and over.  How can we make it work?

Instead of trying to add or subtract directly, what if we added all the time.  Let's not focus on adding, but rather, **what** we are adding.  We are going to make a couple of changes.  Check out this code.

```js

var redColor = 123;
var greenColor = 39;
var blueColor = 21;

var x = 100;
var y = 200;
var diameter = 50;

var movement = 13;
// this function is called only once
function setup()
{

    createCanvas(800,600);
}
/* this function is called continuously
    while the sketch is open in the browser
*/
function draw()
{
    background(redColor,greenColor,blueColor);
    fill(255);
    circle(x,y,diameter);
    fill(redColor,greenColor,blueColor);
    circle(x,y,25);
    if(x <= 800)
    {
       
    }
    
     x+=movement;
}
```

If you run this code, it will work just as did before, where the circles will continue forever.  Notice, I created a new variable **movement** and added that instead of 7.  What about the if statement?  Here is where the magic is going to happen.

```js

var redColor = 123;
var greenColor = 39;
var blueColor = 21;

var x = 100;
var y = 200;
var diameter = 50;

var movement = 13;
// this function is called only once
function setup()
{

    createCanvas(800,600);
}
/* this function is called continuously
    while the sketch is open in the browser
*/
function draw()
{
    background(redColor,greenColor,blueColor);
    fill(255);
    circle(x,y,diameter);
    fill(redColor,greenColor,blueColor);
    circle(x,y,25);
    if(x >= 800)
    {
       movement*=-1;
    }
    
     x += movement;
}
```

Did you notice the changes?  I did two things.  I switched the direction of the relational operator from less than or equal to and made it "greater than or equal to."  The second thing I did was multiply movement by -1.  Why would I do that?  Okay, let's break it down.

```js
    if(x >= 800)
    {

    }

    x += movement;
```

I changed the if statement so that the body only runs when x is equal to or beyond the right border.  What happens in there?  Now, the big reveal.

```js

    movement *= -1;

```

Multiplying movement by -1 is where the magic happens. After movement is multiplied by -1, the movement variable gets added back to the x variable.  However, now, movement is -7, and movement doesn't get multiplied by -1 again because x is not greater or equal to 800.

Cool right?  However, what about the other side?  Do you think you can do it?

<a href="https://umontana.zoom.us/recording/share/THnkqC-qVmVlY8bvZrnOvEYncfCfuxJcfKav8morgmawIumekTziMw" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>