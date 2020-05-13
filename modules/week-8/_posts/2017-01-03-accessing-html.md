---
title: Accessing HTML Tags
module: 8
jotted: true
---

# Accessing HTML Tags

One of the most useful things that JavaScript can do is access HTML tags and change their content. Look at the example below.

```js
 document.getElementById("myTag").innerHTML = "New Text";
```
If you were to have an HTML page like the following, the JavaScript above would change the tag that has the id "myTag".

```html
 <html>
    <body>
        <span id="myTag">This is my favorite text</span>
    </body>
 </html>
```

So, where does it go?

Remember where we put the style tags? Yes? Those went in the head. JavaScript can also go in the head.

The tricky part, though, is that you read HTML from top to bottom. So, if you put the JavaScript from above in the head as is, it won't find the span tag because it doesn't exist yet! Oh no!

So, we have to do something like this.

```html
 <html>
    <body>
        <span id="myTag">This is my favorite text</span>
    </body>

    <script>
        document.getElementById("myTag").innerHTML = "New Text";
    </script>
 </html>
```

After creating the span tag, the JavaScript code updates the text so that it says "New Text". Try it and see if you get that too.

What if we make a mistake, though? Remember earlier when I said if you forget a semi-colon, things could go wrong. What if we don't get the capitalization correct or what if spell something wrong?

Try that. Put this into your web page.

```html
 <html>
    <body>
        <span id="myTag">This is my favorite text</span>
    </body>

    <script>
        dcument.getElementById("myTag").innerHTML = "New Text";
    </script>
 </html>
```

Open your web page. What do you see? Does it help you determine what went wrong? There is a fix for this. It's in the browser settings. To access those in Chrome, follow these steps.

1. Click on the three vertical dots in the upper right-hand corner.
2. Navigate to **More Tools**->**Developer Tools**
3. Click on the console tab. The area shows you the error and where it is in your code. Nice!


We can also use another command to write to the console. It's called console.log.

Try this now.

```html
 <html>
    <body>
        <span id="myTag">This is my favorite text</span>
    </body>

    <script>
        console.log("I am in the console!");
    </script>
 </html>
```

Open your web page. It won't show anything on the page. However, if you go to the console in the Developer Tools again, you will see the message from the console.log. Console.log is an excellent way to find out what is happening in your JavaScript code.

Next, let's talk about variables in JavaScript.

<!-- video -->
<a href="https://umontana.zoom.us/recording/share/nLX4YN7iloCtutSQ-s9sNWpHoEogIDNuBiMzFjWX5r6wIumekTziMw" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>