---
title: Setup the Scene
module: 11
jotted: false
---

# Setup the Scene

I find in programming that often is it is useful to have some context indicating why I am creating something.  That is why  I had you create a self-portrait. Now, we are going to create some interactive art using events.

Have any of you played Spore?  Let's make something like that.  (minus the more beautiful graphics). We will use simple shapes to reduce complexity.

First, let's set up our scene.

```js
    var x = 50;
    var y = 50;
    var diameter = 25;
    function setup()
    {
        createCanvas(800,600);
    }
    function draw()
    {
        background(0);
        fill(24,200,29);
        circle(x,y,diameter);
    }
```

Here we just created a simple black background and added a greenish circle to it.

We know how to make it move.

```js
    var x = 50;
    var y = 50;
    var diameter = 25;
    function setup()
    {
        createCanvas(800,600);
    }
    function draw()
    {
        background(0);
        fill(24,200,29);
        circle(x,y,diameter);
        x+=10;
    }
```

That moves our circle to the right because we are adding to x.  Remember that x,y, and diameter are variables.  We are just changing (or can change) the values stored in those variables, which makes them useful.  Yes?  Good!

Hopefully, you also found out that if you change x and y and diameter at the same time, some exciting things happen.  The concepts we learned last week will be the starting point for this week.

```js
    var x = 50;
    var y = 50;
    var diameter = 25;
    function setup()
    {
        createCanvas(800,600);
    }
    function draw()
    {
        background(0);
        fill(24,200,29);
        circle(x,y,diameter);
        x+=10;
        y+=3;
        diameter+=8;
    }
```

Fun! Where do we go from here? Let's talk about the conditions.  What are those? If, if/else, and if/else if statements.  We have seen the first two, but maybe not the third one. We will look at those.

<a href="https://umontana.zoom.us/recording/share/mHw0xqCy5nbGnAWXfee7J6l6bjxFyOzw0BAW635APuWwIumekTziMw" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>
