---
title: Logical Operators
module: 11
jotted: false
---

# Logical Operators

As we discussed last week, there are three logical operators - AND, OR, and NOT.  They are symbolized with **&&**, **||**, and **!**

Let's look at the first operator AND

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

        if(x <= 200)
        {
            x+=10;
        } 
        else if(x > 200 && x <=300)
        {
            x+=2;
            console.log("second else if for x");
        }
        else if(x > 300)
        {
           x = 50;
        }
        
        if(y <= 200)
        {
            y+=3;
        }
          
        else if(y > 200 && y <= 300)
        {
            y+=1; 
            console.log("second else if for y");
        }
        else if(y > 300)
        {
            y = 50;
        }
        if(diameter <= 200)
        {
            diameter+=8;
        }
          
        else if(diameter > 200 && diameter <= 300)
        {
            diameter +=2;
            console.log("second else if for diameter");
        }
        else if(diameter > 300)
        {
            diameter = 25;
        }
        
    }
```

It wasn't doing what we wanted in the last section. It was only going into the first if statement and the final else if, but never the second. To make the code find the second else if, we need to make the changes above.  

For each second else if the variable must be higher than some number and if the same variable is less than some other number.  If the variables are greater than 200 and less than or equal to 300, then the variable will change at a different rate, and the console.log will print out.

Now, the variables change like before, but the changes slow down until it resets. Feel free to change the numbers.

## OR

What do you think would happen if we changed it to an OR instead of an AND?  Let's find out.

Try this code out.

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

        if(x <= 200)
        {
            x+=10;
        } 
        else if(x > 200 || x <=300)
        {
            x+=2;
            console.log("second else if for x");
        }
        else if(x > 300)
        {
           x = 50;
        }
        
        if(y <= 200)
        {
            y+=3;
        }
          
        else if(y > 200 || y <= 300)
        {
            y+=1; 
            console.log("second else if for y");
        }
        else if(y > 300)
        {
            y = 50;
        }
        if(diameter <= 200)
        {
            diameter+=8;
        }
          
        else if(diameter > 200 || diameter <= 300)
        {
            diameter +=2;
            console.log("second else if for diameter");
        }
        else if(diameter > 300)
        {
            diameter = 25;
        }
        
    }
```

Why did it grow forever? Now that we inserted an OR, the x variable, for example, will change if it's higher than 200 or less than or equal to 300.  After meeting this condition, then variables grow forever.  These changes happen for the other two variables, y, and diameter too.

What needs to change so that all three if and else if's evaluate to true at some point?

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

        if(x <= 250)
        {
            x+=10;
        } 
        else if(x == 250 || x <= 300)
        {
            x+=2;
            console.log("second else if for x");
        }
        else if(x > 300)
        {
           x = 50;
        }

      
        if(y <= 200)
        {
            y+=3;
        }

        else if(y == 250 || y <= 300)
        {
            y+=1; 
            console.log("second else if for y");
        }
        else if(y > 300)
        {
            y = 50;
        }
        if(diameter <= 200)
        {
            diameter+=8;
        }
          
        else if(diameter == 200 || diameter <= 300)
        {
            diameter +=2;
            console.log("second else if for diameter");
        }
        else if(diameter > 300)
        {
            diameter = 25;
        }
        
    }
```

## NOT

So, what about NOT?  How does this fit in this scenario?

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

        if(x <= 250)
        {
            x+=10;
        }
        else if(x == 250 || x <= 300)
        {
            x+=2;
            console.log("second else if for x");
        }
        else if(x != 300)
        {
           x = 50;
        }

      
        if(y <= 200)
        {
            y+=3;
        }

        else if(y == 250 || y <= 300)
        {
            y+=1; 
            console.log("second else if for y");
        }
        else if(y != 300)
        {
            y = 50;
        }
        if(diameter <= 200)
        {
            diameter+=8;
        }
          
        else if(diameter == 200 || diameter <= 300)
        {
            diameter +=2;
            console.log("second else if for diameter");
        }
        else if(diameter != 300)
        {
            diameter = 25;
        }
        
    }
```

All we changed in this scenario is the last else if and as long x,y, or diameter isn't equal to their respective number, then the variable resets.

<a href="https://umontana.zoom.us/recording/share/d1LmQTffFVdIfpgDzTI2CHrypVo_17nwj9RI5ZJoeE2wIumekTziMw" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>