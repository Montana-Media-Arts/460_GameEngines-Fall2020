---
title: Using Functions
module: 12
jotted: true
---

# Using Functions

With **setup** and **draw**, we use them, but we never had to call them. However, luckily, we have used some functions already. Do you remember which ones?

I am going to list some, and hopefully, they will sound familiar.

* Math.floor()
* Math.random()
* isKeyDown()
* circle()
* square()
* point()
* line()
* rect()
* ellipse()

Can you believe all the functions you have used already?  

There are a couple of things to notice. When we **defined** functions, it starts with function, and the body contains the curly braces.

However, when you use functions, you call the function name, and then the name is followed by parentheses.

Except for Math.random(), all the other functions required numbers between the parenthesis.  For example, the circle function requires an x, y, and a diameter.  These are called **parameters**.  When you call the function, then you pass **arguments** into the functions.

So, to recap, the function circle might look something like this.

```js
    // a potential function definition for circle
    function circle(x,y,diameter)
    {
        createCircle(x,y,diameter);
        drawCircle();
    }
```

** Keep in mind that this is NOT the actual definition of the circle function in p5.js **

```js
    function setup()
    {
        createCanvas(500,500);
    }
    function draw()
    {
        circle(10,20,100);
    }
```

When we call circle in the draw function, it calls the function **circle** sending in 10,20 and 100 as arguments into the function parameters.  Then, it creates the circle and then draws it to the screen.  

We can create a circle function that looks like this.

```js
function myCircle()
{
    fill(12,129,192);
    circle(100,200,100);
}
```
I can then call this function in the draw function like this.

```js
    function setup()
    {
        createCanvas(500,500);
    }
    function draw()
    {
        myCircle();
    }
```

I called the **myCircle** function in the draw function.  Did it work?  Good!  Now I can create a single circle in the draw function by calling myCircle.  However, if I call it again, it will generate another circle in the same place.

```js
function myCircle(x,y)
{
    fill(Math.floor(Math.random()*256),Math.floor(Math.random()*256),Math.floor(Math.random()*256));
    circle(Math.floor(Math.random()*x)+10,Math.floor(Math.random()*y),Math.floor(Math.random()*100)+10)
}
```

What did I do?  Now, I am creating a circle with random colors (red, green, and blue are somewhere between 0-255). In the second line, it creates a random x, y, and size. 

Now, when we call myCircle in the draw function, we have a random circle.

```js

function setup()
{
    createCanvas(500,500);
}

function draw()
{
    myCircle(500,500);
}

function myCircle(x,y)
{
    fill(Math.floor(Math.random()*256),Math.floor(Math.random()*256),Math.floor(Math.random()*256));
    circle(Math.floor(Math.random()*x)+10,Math.floor(Math.random()*y),Math.floor(Math.random()*100)+10)
}
```

You should see a random circle now. If you call the myCircle function again, it will draw a second circle in another location.

```js

function setup()
{
    createCanvas(500,500);
}

function draw()
{
    myCircle(500,500);
    myCircle(500,500);
}

function myCircle(x,y)
{
    fill(Math.floor(Math.random()*256),Math.floor(Math.random()*256),Math.floor(Math.random()*256));
    circle(Math.floor(Math.random()*x)+10,Math.floor(Math.random()*y),Math.floor(Math.random()*100)+10)
}
```

Cool huh?

<a href="https://umontana.zoom.us/recording/share/8aNSUGgCbsFCBb4FcUi-rc1REkJa1-qCpTZYqSWbK3ywIumekTziMw
" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>