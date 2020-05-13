---
title: JavaScript Basics
module: 8
jotted: true
---

# JavaScript Basics

What is JavaScript? JavaScript is the client-side programming language that allows us to provide actual functionality to our HTML sites.

How is JavaScript recognized in an HTML page? We need to use `script` tags now. They look like this.

```html
 <script> </script>
```

Inside the script tags are where we put our JavaScript code. These script tags can go anywhere in your HTML. Often you find them in the head tag, but they can also be at the bottom of the body tag. All major browsers read and interpret JavaScript without having to install anything extra. Nice huh?

What can we do right away?

We can **display** text in all different ways.

1. Writing into an alert box, using window.alert().
2. Writing into the HTML output using document.write().
3. Writing into an HTML element, using innerHTML.
4. Writing into the browser console, using console.log().


Well, let's create a quick web page that looks like this.

```html
 <html>
    <title>First JavaScript Page!</title>
    <head>
        <script>
            window.alert("HI");
        </script>
    </head>
    <body>
        This HTML page has JavaScript on it. Did you see the popup?
    </body>
 </html>
```

Open your webpage. Did it provide a popup? Fun huh!? And yes, annoying. Keep in mind there is a new **syntax** of which we should be aware.

The **window** means access to a new window object. The **.** is saying I want to access a method called **alert** that will display an alert window type. The **()** is what tells you that it is a method and that it can receive a **parameter**. In this case, the parameter is **Hi**, and it has to be surrounded by double-quotes for it to work correctly. Finally, all JavaScript lines must end with a semi-colon **;**. The semi-colon tells the computer where the line of code ends. Whew, that was a lot! Don't worry; you will see this is again and again. I just wanted to point this out.

What else can we do?

This time change your webpage so that it looks like this.

```html
 <html>
    <title>First JavaScript Page!</title>
    <head>
        <script>
            document.write("Hi there");
        </script>
    </head>
    <body>
        This HTML page has JavaScript on it. What do you see?
    </body>
 </html>
```
What was different this time? Do you still see the text in the body? Why?

Go onto the next section to learn about accessing HTML and making changes there.

<!-- video -->
<a href="https://umontana.zoom.us/recording/share/6dFr-xnF8-sGaodEKtbhSmUFedPM-UYgzA0BUOw5WeewIumekTziMw" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>