---
title: Setup and Draw
module: 9
jotted: true
---

# Setup and Draw

These are the two main functions in p5.js.  They are the most critical functions and built into this library.

## function setup()

The setup function is the first function called and called only once.  createCanvas is another built-in function that sets up the main window that allows us to draw.

It looks like this.

```js
    createCanvas(300,500);
```

There are some essential things to notice. Hopefully, the look isn't too mysterious. **createCanvas** is the name of the function.  We know it's a function because of the **()** and the first **parameter**, **300** is the width, while the second parameter, **500**, is the height and then, don't forget the **;** semicolon.

**Note** Remember a parameter is something that passed into a function - some value.  The semicolon is needed to end the statement.

To make the canvas appear, add the createCanvas to the setup function.  It looks like this.

```js
    function setup()
    {
        createCanvas(300,500);
    }
```

Why do we put the createCanvas function in the setup? We only want to create the canvas one time.

Give this a try and see what it looks like.

Did you get a canvas to appear in your web browser? Good!

## function draw()

What about the draw function?  What makes it so unique?  We know that setup is called only once when the script while the draw function called continuously.

What have we seen so far? We have done this.

```js
function draw()
{
    background(220);
}
```

Calling the background function repeatedly, then the user sees the grey background.  How can we tell, though? Remember when talked about writing information to the screen?  We can write to the console.log to prove that the draw is called multiple times.  Let's try it.

```js
function draw()
{
    background(220);
    console.log("hi");
}
```

Open your Developer Options and see what it says in the console?

What did you see?

<a href="https://umontana.zoom.us/recording/share/e-mXzteNjuEYz2qzMIVSFjwrqsK4ROlBOnYvfhWc7XCwIumekTziMw" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>

Now, let's do something fun on the screen.