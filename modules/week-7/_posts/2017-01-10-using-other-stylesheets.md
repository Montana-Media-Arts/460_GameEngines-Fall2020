---
title: Using other Styles
module: 7
jotted: true
---

# Using other StyleSheets

## CDN

There are some popular stylesheets out there. One of the most popular is Bootstrap.  To use it, we have a couple of options. We have two options.

1. Use a CDN
2. Download a local copy and reference the local copy.

```html
<html>
    <title>Class Example</title>
    <head>
          <meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
    </head>
    <body>
        <button type="button" class="btn">Basic</button>
        <button type="button" class="btn btn-default">Default</button>
        <button type="button" class="btn btn-primary">Primary</button>
        <button type="button" class="btn btn-success">Success</button>
        <button type="button" class="btn btn-info">Info</button>
        <button type="button" class="btn btn-warning">Warning</button>
        <button type="button" class="btn btn-danger">Danger</button>
        <button type="button" class="btn btn-link">Link</button>
    </body>
</html>
```

Take a look at the `href` attribute in the `link` tag at the top inside the `head` tag. It points to what is called a CDN.  CDN stands for **Content Delivery Network** There are some benefits to using these.  Your CSS is always up to date whenever the author updates it.  However, you must be online to apply this style. So, if you need an offline application, you may want to use a local copy.

## Local Copy

In the case of Bootstrap, you first go to:

https://getbootstrap.com/

Then, click on **Download**.

Under **Compiled CSS and JS**, click **Download**.

You are going to download a zip file.

Save that in a directory near your file.  Then, make sure you unzip your file into a folder.

Then, you will reference your new file like this.

You will also need to download JQuery from:

https://jquery.com/

Then, click on `Download jQuery`.

Then, right-click `Download the compressed, production jQuery 3.x.x` and save the file in your `js` folder with Bootstrap.


```html
<html>
    <title>Class Example</title>
    <head>
          <meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet" href="./styles/bootstrap-4.3.1/css/bootstrap.min.css">
<script src="./styles/bootstrap-4.3.1/js/jquery-3.4.1.min.js"></script>
<script src="./styles/bootstrap-4.3.1/js/bootstrap.min.js"></script>
    </head>
    <body>
        <button type="button" class="btn">Basic</button>
        <button type="button" class="btn btn-default">Default</button>
        <button type="button" class="btn btn-primary">Primary</button>
        <button type="button" class="btn btn-success">Success</button>
        <button type="button" class="btn btn-info">Info</button>
        <button type="button" class="btn btn-warning">Warning</button>
        <button type="button" class="btn btn-danger">Danger</button>
        <button type="button" class="btn btn-link">Link</button>
    </body>
</html>
```

Did you see the same thing as before?  Unfortunately, it's not as simple as using a CDN. However, if you need an offline solution, this will work.  Downloading and saving libraries work for other styles (and JavaScript) that you may want to use in the future too.

<a href="https://umontana.zoom.us/recording/play/wndK0otYtUncEhNDvQQT93q1A_69jVXNmjzq5kQB_7uy2u3qtl24ZX5V70dg9iEq?continueMode=true" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>

<!-- video -->