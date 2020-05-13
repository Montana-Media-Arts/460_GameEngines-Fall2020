---
title: Draw Simple Shapes
module: 9
jotted: true
---

# Draw Simple Shapes

Drawing simple shapes is the first thing that p5.js allows us to do quickly.  One example looks like this.

## circle

To draw a circle, it might look like this.

```js
function setup() {
  createCanvas(400,400);
}

function draw() {
  background(220);
  circle(30,40,50);
}
```

How does this work?

1. circle is the name of the function
2. 30 is the x location on the page
3. 40 is the y location on the page
4. 50 is the diameter of the circle

One thing in which to mindful, the x and y origin is in the upper left-hand corner.  Any guesses why? It's because we don't like negative numbers. It's easier to move to the right positively and down positively.  Then, as we subtract, we move left and up, respectively.

## square

```js
function setup() {
  createCanvas(400,400);
}

function draw() {
  background(220);
  square(30,40,50);
}
```

This time square is the name of the function.  30 is still the x, 40 is the y location, and the 50 represents the width and height since they are the same.

Give it a try!

## ellipse()

```js
function setup() {
  createCanvas(400,400);
}

function draw() {
  background(220);
  ellipse(30,40,50,60);
}
```

Notice the difference with the ellipse as it allows us to create a different width and height. If the height and width were the same, it would be a circle.

## rect()

```js
function setup() {
  createCanvas(400,400);
}

function draw() {
  background(220);
  rect(30,40,50,60);
}
```

Same for the rect function.  If the last two parameters are the same, we will get a square, but if they are different, we will get a rectangle.

## triangle()

```js
function setup() {
  createCanvas(400,400);
}

function draw() {
  background(220);
  triangle(30, 75, 58, 20, 86, 75);
}
```
The first two parameters represent the first point, which is the bottom point; in this case, then the second two parameters are the second point, which is the top point, and then the last two parameters represent the third point or the bottom right point in this triangle.  

There are several other simple shapes, such as point, line, and quad.

<a href="https://umontana.zoom.us/recording/share/IUTwNHyCPUBLZ5qcv7O5Yl7On_u8oQiao-DbQb4vlmewIumekTziMw" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>