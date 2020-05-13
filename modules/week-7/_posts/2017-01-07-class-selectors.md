---
title: Class Selectors
module: 7
jotted: true
---

# Class Selectors

In the previous section, we added styles by using inline styles, embedded styles, and external style sheets.  

In our styles, we were general to all span tags.  However, what if we wanted to find a specific tag or apply a style to several different tags?  That is where we use classes and ids in our stylesheets.  We will use stylesheets from now on.

Here's an example of an HTML page.

```html
    <html>
        <title>Class Example</title>
        <head>
            <link rel="stylesheet" type="text/css" href="mainstyle.css">
        </head>
        <body>
            <span class="blueColor">New Color</span>
            <br>
            <span>Same Color</span>
            <br>
            <a href="http://www.amazon.com" class="blueColor">Amazon</a>
        </body>
    </html>
```
<br>
```html
    .blueColor{
        color:blue;
        font-family:arial;
        font-size:24px;
    }
```



Notice in this example, the CSS has the name `.blueColor`.  The blueColor class identifier applies the blue color, changes the font type, and the size of the `span` tag and an `a` (anchor) tag.  They both turned blue while the other span tag without the class name did not.

We can get even more specific by doing something like this.

```html
    span.blueColor{
        color:blue;
        font-family:arial;
        font-size:24px;
    }
```

Now, only span tags with the class `blueColor` will change.  No other tags will work.

<a href="https://umontana.zoom.us/recording/play/U4KljRbP4QCe_cQFVZMgV4jWXmL6XS3dKaeMI48gL8i-h5vtV3narFBXN03scANP?continueMode=true" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>

<!-- video -->


