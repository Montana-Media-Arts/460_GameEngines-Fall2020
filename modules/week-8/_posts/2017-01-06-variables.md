---
title: Variables
module: 8
jotted: true
---

# Variables

So, you have been working with variables in all the other languages we have worked with so far. Hopefully, these won't feel scary or foreign to you now.

What do they look like in JavaScript?

```js
 var favoriteNumber = 13;
 var favoriteColor = "blue";
 var myAge;
 myAge = 79;
 var red,green,blue;
 red = "#FF0000";
 green = "#00FF00";
 blue = "#0000FF";
```

As you stated above, there are several different ways in which you can declare and assign values to your variables. They are all valid, and it just depends on when you want to give them a value or if they will be assigned later.

To use them in your HTML page, you can do something like this.

```html
 <html>
    <title>Variables</title>
    <head>
    <script>
        var favoriteColor = "blue";
    </script>
    </head>
    <body>
        <span id="myTag">This is my favorite text</span>
    </body>

    <script>
        document.getElementById("myTag").innerHTML = "Favorite Color " + favoriteColor;
    </script>
 </html>
```

There are three things to notice here.

1. I can put the variable in the script tag inside the head tag because it is not trying to access the tag **myTag**.
2. When I print out the variable **favoriteColor**, it has to match the capitalization precisely as it is declared, or it will not work.
3. To make it show up in the tag, you have to use the **+** and then put the variable name without the double-quotes **"**. The double-quotes are required if you want to print out exactly what is inside the double-quotes. In this case, we want to print out the value stored in the variable.

<!-- video -->
<a href="https://umontana.zoom.us/recording/share/2ftwL1SiCufc5jsjSce0TTbHI9cdKw8TrsD-WWTBkhewIumekTziMw" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>