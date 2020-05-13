---
title: External Style Sheets
module: 7
jotted: true
---

# Adding CSS to HTML

## External Style Sheets

The last way in which we can apply a style is through an **external** style sheet.

How does it look?

**External Style Sheet**

```html
span{
    color:white;
    background-color:red;
}
```

Note that when you save this in a separate page, it has to be called something like `mainstyle.css`.  It always ends with a `.css` extension.

Now, we can assign it to a page like this.

```html
    <html>
        <title>External Style Sheet</title>
        <head>
            <link rel="stylesheet" type="text/css" href="mainstyle.css">
        </head>
    </html>
```

There are a couple of things to note.  The `rel` is the relationship attribute, and the `type` specifies the type of file.  Finally, the `href`, which should look familiar, is the file location. Remember, if it defined like it is above, it has to be in the same folder.  Otherwise, you need to add the correct path.

We use style sheets so that we can apply a style sheet to many pages.  Then, if we want to make a change, we can change it in one file and use it everywhere.

So, when you have all three types of styles on your page, which style is applied?  It always goes in this order.

1. Inline styles first
2. Embedded
3. External
4. Browser

Yes, that's right; the browser has a style sheet.  If you are interested, take a look around, and you can find and change your browser's style sheet. Fun right?

<a href="https://umontana.zoom.us/recording/share/CSAT9qvMOp7X1q8UMw83vh8Ybl3sAQufDaFG7MWm_TewIumekTziMw" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>


<!-- video -->