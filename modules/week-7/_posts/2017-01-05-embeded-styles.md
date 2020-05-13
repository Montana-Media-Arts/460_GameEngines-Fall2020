---
title: Embedded Styles
module: 7
jotted: true
---

# Adding CSS to HTML

## Embedded

The second way in which we can add CSS by using **embedded** styles on the page.  By having embedded styles, we apply a format to only this page.  An example might look like this.

```html
<html>
    <title>Embedded Style Example</title>
    <head>
        <style>
            span{
                background-color:red;

            }
        </style>
    </head>
    <body>
        <span>This is the first sentence.</span>
        <br>
        This is the second sentence.
        <br>
        <span>This is the third sentence</span>
    </body>
</html>
```
In this example, you see the first and the third sentence have a background color of red. While the second sentence does not.  The style at the top of the page within the `<head>` tags applies the background color to all span tags.

What are some of the positives and negatives of using embedded styles?

<a href="https://umontana.zoom.us/recording/share/Udr8dWDE0uYdEhHTtbKKYOuIm0k2iHhsfB7hwa1N7BmwIumekTziMw" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>
<!-- video -->