---
title: Hyperlinks
module: 6
jotted: true
---

# Hyperlinks


Hyperlinks have been around since the beginning of HTML4 and continue today. They are the bedrock of web pages as they take us places.  They have a similar structure to image tags, and they look like this.

```html
<a href="mypage.html">Link to somewhere</a>
```

The `<a>` tag is called the anchor tag.  It tells us that there will be a link there.  The `href` is the attribute that indicates where you are going to go.  So in the previous instance, if we clicked on the *Link to somewhere*, it would take us to the *mypage.html* page.

So, how does the whole page look?

```html
<html>
    <title>My first page</title>
    <body>
        <a href="secondpage.html">Go to my other page</a>
    </body>
</html>

```

Whereas on the second page, you might have something that looks like this.

```html
<html>
    <title>My second page</title>
    <body>
        <a href="firstpage.html">Go to my first page</a>
    </body>
</html>

```

Keep in mind that you have to have two pages named *secondpage.html* and *firstpage.html* respectively.


<!-- video -->
<a href="https://umontana.zoom.us/recording/play/V-pYuGcb458imbF1fVAOoy6bhatQIPhrk8whAhPjWTIeTnPPIHfQf64FfTwA4yOe?continueMode=true" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>

<a href='http://www.silverleaf-consulting.com/CodeEditor/' target="_new">Click here for an Interactive HTML editor</a>

<!-- video -->

