---
title: Dialog Raycast
module: 7
jotted: true
---

# Dialog Raycast

Creating the Character
The first task is to create a character, which will be a frog called Jambi. Now that you are getting used to Unity, this should be quick and straightforward. To make it even easier, the character uses a single looping animation.
The Sprite Atlas to use is JambiSheet in the Art > Sprites > Characters folder:
1. Slice your sprites using the Sprite Atlas format of 4 by 4 Sprites.
2. Import the Sprites into the Scene to create the character. 
Tip: If you select the three sprites in your Project folder and drag them all at once into the Hierarchy, Unity creates the animation of those three frames automatically for you and assigns it to the newly created GameObject. It will play automatically and no other action is needed:
3. Go back to your Jambi sprite atlas in your Project window asset and change the Pixel per Unit setting to something you think will look nice. Change the value, press Apply and check in the scene view if Jambi is the right size for you. 150 was used in this case.
4. Add a Box Collider 2D and scale it to cover the bottom of the Sprite like we did for our main character or our enemy.
5. Create a layer called “NPC” (for Non Player Character) and set your character GameObject to that.
6. Finally, rename the GameObject Jambi and create a Prefab out of that GameObject.
You can now enter Play mode and test your character is properly animated and collides correctly.
If the automatically created animation looks like it’s running too fast, you can always change the sample rate in the Animation window (Menu Window >  Animation > Animation), just like you did for your handmade animation clip. 


Mark step as completed
2.Raycasting
Now you need to add code so that Ruby can talk to your frog character. First, you need to know if Ruby is standing in front of the character.
You could place a trigger in front of the frog character and if Ruby walks on that trigger, then the dialog starts. But this means that Ruby could be turning her back to the frog and would still be able to talk to it.
Instead, you will use a Physics System feature that is really useful in interactive applications: Raycasting. 
Raycasting is the action of casting a ray in the Scene and checking to see if that ray intersects with a Collider. A ray has a starting point, a direction and a length. The term to “cast” a ray is used because the test is made from the starting point all along the ray until its end.
Here you will cast a ray from your main character’s position, in the direction she is looking, from a small distance, for example 1 or 1.5 units. 
To do this, add the following code in your Update function of your RubyController : 
if (Input.GetKeyDown(KeyCode.X))
{
    RaycastHit2D hit = Physics2D.Raycast(rigidbody2d.position + Vector2.up * 0.2f, lookDirection, 1.5f, LayerMask.GetMask("NPC"));
    if (hit.collider != null)
    {
        Debug.Log("Raycast has hit the object " + hit.collider.gameObject);
    }
}
Let’s take a look at that code in detail:
In the first line, you will check to see if the X key is pressed, just like you did in the Projectile Tutorial. 
This will be your “talk” button. If you want this to work across multiple devices instead, you can use input axes (for a reminder, see the character controller movement ).
If that key is pressed, enter the if block and start your Raycast. 
First, you will declare a new variable of type RaycastHit2D. This variable stores the result of a Raycast, which is given to us by Physics2D.Raycast. There are multiple versions of Physics2D.Raycast (for all variants, take a look at the Scripting API), but the version we use here has four arguments:
1.  The starting point in your example is an upward offset from Ruby’s position because you want to test from the centre of Ruby’s Sprite, not from her feet. 
2.  The direction, which is the direction that Ruby is looking.
3.  The maximum distance of your ray should be set to 1.5 so the Raycast doesn’t test intersections that are 1.5 units away from the starting point.
4.  A layer mask which allows us to test only certain layers. Any layers that are not part of the mask will be ignored during the intersection test. Here, you will select the NPC layer, because that one contains your frog. 
Finally, test to see if your Raycast has hit a Collider. If the Raycast didn’t intersect anything, this will be null so do nothing. Otherwise, RaycastHit2D will contain the Collider the Raycast intersected, so you will go inside your final if block to log the object you have just found with the Raycast.
To see this logging in the Console:
Enter play mode
Position Ruby close to and facing the frog
Then press X.


Mark step as completed
3.Dialog UI
To keep it simple, you’ll make your dialog appear in a small box above Jambi, your frog friend. 
You will use a Canvas like you did in the UI tutorial, but this time we’ll make the Canvas appear in world space. This means the Canvas will exist in the world, just above Jambi’s head, instead of always being overlaid on the screen.
To add the Canvas:
Right-click Jambi in the Hierarchy (or select Jambi and then click the Create button on top of the Hierarchy)
Select UI > Canvas. This creates a child Canvas GameObject for Jambi.
Currently your Canvas is overlaid on the screen. With the Canvas selected in the Hierarchy, go to the Inspector and change the Render Mode to World Space: 

You can ignore the Event Camera setting because it is only useful for UI interactions like button presses, and you only want to display text on your Canvas.
Right now our Canvas is way too big. The Canvas size is in pixels, and in the Rect Transform of the Inspector we can see that the Width and Height are in the hundreds (the value will be different for you as it is based on the size of your Gameview when you switch the Canvas mode to World Space):

You could change those values to give your Canvas a proper size in your Scene (for example, a width of 3 units and a height of 2 units), but that would make it harder for you to build your UI. 
All UI elements (such as image and text) work in pixels, so a Canvas size of width 3 and height 2 would create a box of 3 by 2 pixels.
Instead, you will scale your Canvas, so the size in the Scene is reduced, but its width and height are kept to proper pixel values.
Set your Rect Transform:
Pos X and Pos Y to 0
Width to 300 and Height to 200
Then set the Scale to 0.01 in X, Y and Z:



Mark step as completed
4.Changing your Scene
Now that your Canvas is the right size in your Scene, let’s move it to be above the frog character. 
Now let’s add an image:

1.  In the Hierarchy, select the Canvas GameObject.

2.  Right-click the GameObject and select UI > Image from the contextual menu.

3.  In the Project window, go to Assets/Art/Sprites/UI.

4.  Select the UIDialogBox Sprite and drag it into the Source Image field. 
Don’t forget to expand the image to fill the Canvas by selecting the bottom right handle while keeping Alt pressed in the Rect Transform:
You may notice that your Canvas image appears behind some elements in your Scene. That’s because your Canvas exists in the Scene, so it’s like any other GameObject and can be rendered behind those GameObjects. 
To make sure nothing renders on top of your Canvas, select the Canvas in the Hierarchy and, in the Inspector, set Order in Layer to a high value (for example, 10):



Mark step as completed
5.Adding text to your Canvas
To add the text to our Canvas:
1. Right-click on that Image GameObject in the Hierarchy and choose UI >  Text - TextMeshPro. This will display the following dialog box:

2.  Click on Import TMP Essentials. When the import is done (the Import TMP Essential button will become greyed out), you can close that window. Your text is now created.
3.  Just like you did for the image earlier, click on the expand anchor handle while pressing Alt to spread the text to the full size of the image
4.  Then use the small white handle to move the yellow box (the text bounds), to give the text box a margin:
5.  Now, in the Inspector, you can write your text and change the text style. Play with all the parameters and enter the text you want Jambi to say!



Mark step as completed
6.Displaying Dialog
Finally, you need to display the dialog when Ruby talks to Jambi. 
For this, let’s hide the Canvas by disabling it:
1.  Select the Canvas in the Hierarchy and, in the Inspector, uncheck the checkbox at the top of the Inspector.
2.  Then create a new C# script called NonPlayerCharacter and add it on Jambi.
3.  In that script, create two public variables: 
One of type float called displayTime, initialised to 4, which will store how long in seconds our dialog box is displayed. 
One of type GameObject called dialogBox that will store the Canvas GameObject, so you can enable/disable it in the script.
4.  Then a private variable:
One of type float called timerDisplay that will store how long to display our dialog.
public float displayTime = 4.0f;
public GameObject dialogBox;
float timerDisplay;
 5.  In the Start function, we need to make sure that the dialogBox is disabled, and initialise timerDisplay to -1: 
void Start()
{
    dialogBox.SetActive(false);
    timerDisplay = -1.0f;
}
6. In the Update function, check whether the dialog is currently displayed by testing if timerDisplay is superior or equal to 0. 
If it is greater than zero, then the dialog is currently being displayed. In this case, you will decrease Time.deltaTime to count down and then check if your timerDisplay has reached 0. This means it’s time to hide your dialog box again, so you will need to disable the dialog box:
void Update()
{
    if (timerDisplay >= 0)
    {
        timerDisplay -= Time.deltaTime;
        if (timerDisplay < 0)
        {
            dialogBox.SetActive(false);
        }
    }
}
7.  Finally, you need to write a public function called DisplayDialog that your RubyController will call when Ruby interacts with the NPC frog. This function will show the dialog box and initialize the timeDisplay to the displayTime setup:
public void DisplayDialog()
{
    timerDisplay = displayTime;
    dialogBox.SetActive(true);
}
8.  You can now open your RubyController script again, and replace the Debug.Log you wrote earlier for your Raycast with this code: 
if (hit.collider != null)
{
    NonPlayerCharacter character = hit.collider.GetComponent<NonPlayerCharacter>();
    if (character != null)
    {
        character.DisplayDialog();
    }  
}
 
9.  All you are doing here is checking if we have a hit, then trying to find a NonPlayerCharacter script on the object the Raycast hit, and if that script exists on that object, you will display the dialog.
10.  Don’t forget to assign the Canvas child of Jambi in the “Dialog Box” setting in the NonPlayerCharacter script in the Inspector. 
11.  Now try again to get Ruby to interact with Jambi by pressing X when she’s facing Jambi. This time, the dialog box will appear and then disappear after four seconds (or however long you set the displayTime value to in the Inspector).


Mark step as completed
7.Check Your Scripts
Your RubyController script should now look like this:
public class RubyController : MonoBehaviour
{
    public float speed = 3.0f;
    
    public int maxHealth = 5;
    
    public GameObject projectilePrefab;
    
    public int health { get { return currentHealth; }}
    int currentHealth;
    
    public float timeInvincible = 2.0f;
    bool isInvincible;
    float invincibleTimer;
    
    Rigidbody2D rigidbody2d;
    float horizontal;
    float vertical;
    
    Animator animator;
    Vector2 lookDirection = new Vector2(1,0);
    
    // Start is called before the first frame update
    void Start()
    {
        rigidbody2d = GetComponent<Rigidbody2D>();
        animator = GetComponent<Animator>();
        
        currentHealth = maxHealth;
    }

    // Update is called once per frame
    void Update()
    {
        horizontal = Input.GetAxis("Horizontal");
        vertical = Input.GetAxis("Vertical");
        
        Vector2 move = new Vector2(horizontal, vertical);
        
        if(!Mathf.Approximately(move.x, 0.0f) || !Mathf.Approximately(move.y, 0.0f))
        {
            lookDirection.Set(move.x, move.y);
            lookDirection.Normalize();
        }
        
        animator.SetFloat("Look X", lookDirection.x);
        animator.SetFloat("Look Y", lookDirection.y);
        animator.SetFloat("Speed", move.magnitude);
        
        if (isInvincible)
        {
            invincibleTimer -= Time.deltaTime;
            if (invincibleTimer < 0)
                isInvincible = false;
        }
        
        if(Input.GetKeyDown(KeyCode.C))
        {
            Launch();
        }
        
        if (Input.GetKeyDown(KeyCode.X))
        {
            RaycastHit2D hit = Physics2D.Raycast(rigidbody2d.position + Vector2.up * 0.2f, lookDirection, 1.5f, LayerMask.GetMask("NPC"));
            if (hit.collider != null)
            {
                NonPlayerCharacter character = hit.collider.GetComponent<NonPlayerCharacter>();
                if (character != null)
                {
                    character.DisplayDialog();
                }
            }
        }
    }
    
    void FixedUpdate()
    {
        Vector2 position = rigidbody2d.position;
        position.x = position.x + speed * horizontal * Time.deltaTime;
        position.y = position.y + speed * vertical * Time.deltaTime;

        rigidbody2d.MovePosition(position);
    }

    public void ChangeHealth(int amount)
    {
        if (amount < 0)
        {
            if (isInvincible)
                return;
            
            isInvincible = true;
            invincibleTimer = timeInvincible;
        }
        
        currentHealth = Mathf.Clamp(currentHealth + amount, 0, maxHealth);
        
        UIHealthBar.instance.SetValue(currentHealth / (float)maxHealth);
    }
    
    void Launch()
    {
        GameObject projectileObject = Instantiate(projectilePrefab, rigidbody2d.position + Vector2.up * 0.5f, Quaternion.identity);

        Projectile projectile = projectileObject.GetComponent<Projectile>();
        projectile.Launch(lookDirection, 300);

        animator.SetTrigger("Launch");
    }
}
Your NonPlayerCharacter script should now look like this:
﻿using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class NonPlayerCharacter : MonoBehaviour
{
    public float displayTime = 4.0f;
    public GameObject dialogBox;
    float timerDisplay;
    
    void Start()
    {
        dialogBox.SetActive(false);
        timerDisplay = -1.0f;
    }
    
    void Update()
    {
        if (timerDisplay >= 0)
        {
            timerDisplay -= Time.deltaTime;
            if (timerDisplay < 0)
            {
                dialogBox.SetActive(false);
            }
        }
    }
    
    public void DisplayDialog()
    {
        timerDisplay = displayTime;
        dialogBox.SetActive(true);
    }
}


Mark step as completed
8.Summary
In this tutorial you’ve seen how Raycasting is extremely useful in interactive applications because it allows you to detect things like Colliders in a given direction.
As well as checking what is in front of a character, Raycasting has a lot of other uses, depending on the type of game you want to make. 
For example, to check whether there is anything between the main character’s position and an enemy position, you could set up a Raycast between those two points and, if it returns a hit, then something is between them, so the enemy can’t see the main character.
In the next tutorial you will add another crucial part to your interactive game: audio and sound.


Mark st