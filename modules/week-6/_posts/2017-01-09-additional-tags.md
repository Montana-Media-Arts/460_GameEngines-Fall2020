---
title: Addional Tags
module: 6
jotted: true
---

# Additional Tags

Two tags that are inside the `<html>` tag, but do not show up on the page are the title tag and the head tag.  The first is the `<title>` tag, and the second is the `<head>` tag.  They both exist above body tag, and they serve two very distinct purposes.

1. title - the text that goes between the title tags show up in the tab or the title bar of the browser.
2. head - the head tag contains items like included files.  We will examine these as time goes on.  

Here's an example of the head and the title tags.

```html
<html>
    <title>My first page</title>
    <head>
        <!-- this is a comment -->
        <!-- we will put stuff in here later -->
    </head>
    <body>
        This is a some random text
    </body>
</htmL>

```

<!-- video -->

There are several other tags that we use for display purposes.

1. ol - Use this tag to create an ordered list.  
2. ul - Use this tag to create an unordered list
3. li - this tag must be used with the ol and ul to make the list items appear

It looks like the following:

```html
<html>
    <title>My first page</title>
    <body>
        <ol>
            <li>Apples</li>
            <li>Oranges</li>
            <li>Grapes</li>
        </ol>

        <ul>
            <li>Dogs</li>
            <li>Cats</li>
            <li>Hedgehogs</li>
        </ul>
    </body>
</html>

```

Try these tags in the section below to ensure that you see the ordered and the unordered list.

<!-- video -->

What else can we do?  If I want to display images, there is a unique tag for that.  It's the `<img>` tag.  Using this tag, we can view images. Let's look at an example, and then I will explain it to you.

```html
<html>
    <title>My first page</title>
    <body>
        <img src="myPicture.jpg" />
    </body>
</htmL>

```

What did I do? Yikes!  What I did was add what is called an `attribute` to the `<img>` tag.  This attribute is where we store the location of the image.  It can be on your computer or reference an image online.  Pretty cool, huh?  There are more attributes if we want to change the size of the image as well.  They are `height` and `width`.

Try this example out and see if it works:

```html
<html>
    <title>My first page</title>
    <body>
        <img src="myPicture.jpg" height='200' width='200'/>
    </body>
</htmL>

```

<!-- video -->
<a href="https://umontana.zoom.us/recording/play/TsfeO9wf0ahSSHsmeFyn5o-UbW_GSWPUr8FFBS3xbDImG61BokWEys-ZxJ3hZ-rq?continueMode=true" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>

<a href='http://www.silverleaf-consulting.com/CodeEditor/' target="_new">Click here for an Interactive HTML editor</a>

Let's move on and learn about hyperlinks.

