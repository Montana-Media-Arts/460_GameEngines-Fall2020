---
title: HTML Forms
module: 6
jotted: true
---

# HTML Forms

What are HTML forms?  Well, if you have ever purchased anything online or filled out an application online or signed up for an email, your social media account or more, you have filled out a form.  Forms are just a way for us to gather data from the end-user.  Keep in mind there are some principles to which we should adhere.

First, we want to adhere to standards. Use the component for their intended use.  Use checkboxes for multiple selections and radio buttons for various choices, but only one correct one.

Aso, use dropdown lists, use those to control the input gathered.  We are going to first focus on creating forms and what tags are required. Then, we will add a look and feel to them and add a little functionality to them.

Here is an example of a simple form.

```html
<html>
    <title>My first page</title>
    <body>
        
        <form action="nextPage.html" type="Post">
            First Name: <input type="text" id="fName"><br>
            Last Name: <input type="text" id="lName"><br>
            <button id="mySubmit" type="submit">Submit</button>
        </form>
    </body>
</html>

```
<a href="https://umontana.zoom.us/recording/play/GO_MDg10XBmdQxTaqsUElvCDWN2v8OQpW_ez7U5a_8z_Nhvs8i7KcWIjTYWz9gxz?continueMode=true" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>

<a href='http://www.silverleaf-consulting.com/CodeEditor/' target="_new">Click here for an Interactive HTML editor</a>

Look what we did here!  We created a basic yet pretty bland form!  So, challenge yourself to add more fields. Did it work?  Great!
