---
title: If statements
module: 8
jotted: true
---

# If statements

Let's start with a form that is similar to what we had before. However, this time, we have two functions. **gasp**.

It looks like this.

```html
<html>
    <title>If statements</title>
    <head>
        <script>
            function printQuestion()
            {
                document.getElementById("theQuestion").innerHTML = "What is 3+5?"; 
            }
            function checkAnswer()
            {
                var answer = document.getElementById("txtAnswer").value;
                document.getElementById("finalResult").innerHTML = "Your answer is " + answer;
            }
        </script>
    </head>
    <body onload="printQuestion();">
        <div id="theQuestion"></div>
        <table>
            <tr>
                <td>Your answer</td>
                <td><input type="text" id="txtAnswer"></td>
            </tr>
            <tr>
                <td colspan="2"><button id="btnSubmit" onClick="checkAnswer();">Submit</button></td>
            </tr>
        </table>
        <div id="finalResult"></div>
    </body>
 </html>
```

Okay, so first, the onLoad calls the **printQuestion** function. Then the button click calls **checkAnswer** function, and the user's answer is printed out. Did it work for you? Good!

So, how do we know if it is correct? That is where **if** statements come in. Again, you have seen these before in other languages, but maybe not quite like this. Hopefully, you can visualize them, though. Let's change the code a bit, so it looks like this now.

```html
<html>
    <title>If statements</title>
    <head>
        <script>
        function printQuestion()
        {
            document.getElementById("theQuestion").innerHTML = "What is 3+5?";
        
        }
        function checkAnswer()
        {
            var answer = document.getElementById("txtAnswer").value;
            if(answer == 8)
            {
                document.getElementById("finalResult").innerHTML = "Good job!";
            }
            else
            {
                document.getElementById("finalResult").innerHTML = "Not quite!";
            }
        
        }
        </script>
    </head>
    <body onload="printQuestion();">
        <div id="theQuestion"></div>
        <table>
            <tr>
                <td>Your answer</td>
                <td><input type="text" id="txtAnswer"></td>
            </tr>
            <tr>
                <td colspan="2"><button id="btnSubmit" onClick="checkAnswer();">Submit</button></td>
            </tr>
        </table>
        <div id="finalResult"></div>
    </body>
 </html>
```

Run this and try entering **8**. Did you get the **Good job!** message? What about if you enter something that is not 8?

You have written an if statement in JavaScript! Good job!

Let's expand on this a bit now. At the moment, it's boring because it has one question. How do we make it more dynamic?

Let's create random numbers.

How do we do that?

```js
 Math.floor(Math.random() * 10);
```

Before you start breathing heavy, consider this. Math.floor means if there are any numbers after the decimal point (e.g., 3.453, round down. So, this should 3 and 3.646 will also be 3.) The Math.random() is just a function that returns a number between 0 inclusive and 1 exclusive. That means include zero in the results, and all decimal numbers up to 1, but not 1.  Another thing to notice is that it's being multiplied by 10. In programming, the `*` is the multiplication sign. So, the number returned by Math.random (something between 0 and .9999999999) is first multiplied by ten before calling Math.floor. After all that, you will get a number between 0 and 9. So, if you change the 10, you will get a number between 0, and whatever that number entered minus 1. Make sense?

So, how do we apply this?

```html
<html>
    <title>If statements</title>
    <head>
        <script>
        var actualAnswer;
        function printQuestion()
        {
            var number1 = Math.floor(Math.random() * 10);
            var number2 = Math.floor(Math.random() * 10);
            actualAnswer = number1 + number2;
            document.getElementById("theQuestion").innerHTML = "What is " + number1 + "+" + number2 + "?";
        
        }
        function checkAnswer()
        {
            var answer = document.getElementById("txtAnswer").value;
            if(answer == 8)
            {
                document.getElementById("finalResult").innerHTML = "Good job!";
            }
            else
            {
                document.getElementById("finalResult").innerHTML = "Not quite!";
            }      
        }
        </script>
    </head>
    <body onload="printQuestion();">
        <div id="theQuestion"></div>
            <table>
                <tr>
                    <td>Your answer</td>
                    <td><input type="text" id="txtAnswer"></td>
                </tr>
                <tr>
                    <td colspan="2"><button id="btnSubmit" onClick="checkAnswer();">Submit</button></td>
                </tr>
            </table>
        <div id="finalResult"></div>
    </body>
 </html>
```

I did two things right away.

1. I create three variables above the printQuestion function. I created **number**, **number2**, and **actualAnswer** variables. I put the number1 and number2 variables in the printQuestion method because I don't need to use them in any other function. However, we use actualAnswer in both the printQuestion and the checkAnswer functions. If we declared actualAnswer in the printQuestion function, the checkAnswer function wouldn't be able to use it.

Put this into your web page. Do you see a different question when you run it? What if you answer it? Did you get the **Good job!** with the correct answer? Why or why not?

What do we need to change?

The code should look like this.

```html
<html>
    <title>If statements</title>
    <head>
    <script>
        var actualAnswer;
        function printQuestion()
        {
            var number1 = Math.floor(Math.random() * 10);
            var number2 = Math.floor(Math.random() * 10);
            actualAnswer = number1 + number2;
            document.getElementById("theQuestion").innerHTML = "What is " + number1 + "+" + number2 + "?";
            
        }
        function checkAnswer()
        {
            var answer = document.getElementById("txtAnswer").value;
            if(answer == actualAnswer)
            {
                document.getElementById("finalResult").innerHTML = "Good job!";
            }
            else
            {
                document.getElementById("finalResult").innerHTML = "Not quite!";
            }
        
        }
    </script>
    </head>
    <body onload="printQuestion();">
        <div id="theQuestion"></div>
             <table>
                <tr>
                    <td>Your answer</td>
                    <td><input type="text" id="txtAnswer"></td>
                </tr>
                <tr>
                    <td colspan="2"><button id="btnSubmit" onClick="checkAnswer();">Submit</button></td>
                </tr>
            </table>
        <div id="finalResult"></div>
    </body>
 </html>
```

<a href="https://umontana.zoom.us/recording/share/IEKX1NAVifV853DyeRcp9Rt5Wiq4LIdP-VBNJBtxkvWwIumekTziMw" target="_new" style="font-family:Ariel; font-size:32px;">Click here for this section's Video</a>

Next, let's look at how we can do this more than once by using a for loop.