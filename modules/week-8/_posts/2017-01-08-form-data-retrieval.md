---
title: Form Data Retrieval
module: 8
jotted: true
---

# Form Data Retrieval

Keep in mind that although it's handy to print information to the page, it is beneficial to get information from a form. I imagine most of you have filled out web forms before. They are super fun, I know. However, most web forms use JavaScript in one way or another. So, we are going that.

Let's create a form like this.

```html
<html>
    <title>Forms</title>
    <head>
        
    </head>
    <body>
        <table>
            <tr>
                <td>Name</td>
                <td><input type="text" id="txtName"></td>
            </tr>
            <tr>
                <td>Phone Number</td>
                <td><input type="text" id="txtPhone"></td>
            </tr>
            <tr>
                <td colspan="2"><button id="btnSubmit" onClick="getData();">Submit</button></td>
            </tr>
        </table>
    </body>
 </html>
```

If you put this into your web page, you will see a basic form. It won't be fancy (there is no styling, as you know). So, how do we make it function?

Let's change the form now to look like this.

```html
<html>
    <title>Forms</title>
    <head>
        <script>
            function getData()
            {
                var name = document.getElementById("txtName").value;
                var phone = document.getElementById("txtPhone").value;

                window.alert("name: " + name + " phone: " + phone);
            }
        </script>
    </head>
    <body>
        <table>
            <tr>
                <td>Name</td>
                <td><input type="text" id="txtName"></td>
            </tr>
            <tr>
                <td>Phone Number</td>
                <td><input type="text" id="txtPhone"></td>
            </tr>
            <tr>
                <td colspan="2"><button id="btnSubmit" onClick="getData();">Submit</button></td>
            </tr>
        </table>
    </body>
 </html>
```

There are a couple of things to notice here.

1. Within the button tag, there is an **onClick** event called now. It calls the function **getData**. We know it's a function because of the **()** after the name.
2. If we go to the script tags within the head tag, you will find the getData function. It retrieves the data from the text boxes by calling the **value** property.
3. Variables store the values, and then we use the window.alert to determine if we are getting the actual values.

Why did I do that? Percolate on that for a second.

I did it because then we know we are getting the correct data before we write more code. We don't want to keep going only to find out that none of it is working. If we have a whole lot of code to wade through, it can get harrowing. If you don't like window.alert, you can always use console.log. It is just as useful.

So, now that it is working, let's print out the values on the page. It looks like this.

```html
<html>
    <title>Forms</title>
    <head>
        <script>
            function getData()
            {
                var name = document.getElementById("txtName").value;
                var phone = document.getElementById("txtPhone").value;

                document.getElementById("finalResult").innerHTML = "name: " + name + " phone: " + phone;
            }
        </script>
    </head>
    <body>
        <table>
            <tr>
                <td>Name</td>
                <td><input type="text" id="txtName"></td>
            </tr>
            <tr>
                <td>Phone Number</td>
                <td><input type="text" id="txtPhone"></td>
            </tr>
            <tr>
                <td colspan="2"><button id="btnSubmit" onClick="getData();">Submit</button></td>
            </tr>
        </table>
        <div id="finalResult"></div>
    </body>
 </html>
```

All I did was add a **div** tag and then accessed its Id in JavaScript and put the name and phone number in that tag. 

<a href="https://umontana.zoom.us/recording/share/Xc--4OkFbX5SudNXip4n9s4s_w58inGUq9PW6k2AOHqwIumekTziMw" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>

Where do we go from here? Let's create a small addition game so that we can learn about **if** statements in JavaScript.