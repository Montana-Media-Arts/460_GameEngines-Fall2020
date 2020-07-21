---
title: User Interface - HUD
module: 7
jotted: true
---

# User Interface - HUD

UI Canvas
In this tutorial you will add UI to your Project to show the current health of your main character.

The UI in Unity renders UI-specific components like images, sliders, and buttons using a GameObject called a Canvas component. A Canvas defines how each UI element should be rendered on screen, and takes care of rendering all UI components that are children of it.
To create a UI:
1.  The first step to create a UI is to create a Canvas. You make a Canvas just like any other GameObject, by right-clicking in an empty space in your Hierarchy, or using the Create button at top the Hierarchy and selecting UI > Canvas.
When you do this, you’ll notice another GameObject is also added to your Scene, called EventSystem. This is a GameObject with a special component that handles events and interaction with the UI, such as a mouse click. You won’t use it here, but you need to leave it in the Scene or the Canvas will log warnings.
2.  Select the newly created Canvas GameObject and check the Inspector: 



Mark step as completed
2.Rect Transform
The first difference is that the GameObject has a Rect Transform component instead of the Transform that you’ve seen on other GameObjects. 
A Rect Transform is still a Transform, so you can use it as a Transform in your scripts, but it has additional UI data that you will look at later on. For now, just think of it as a special kind of Transform.
The Canvas defines how the UI is displayed in the game. The Canvas can be in any of these modes:
Screen Space - Overlay: This default mode makes Unity draw your UI on top of your game all of the time. Most applications use this mode because they want the UI to always be on top to give all information.
Screen Space - Camera: This draws the UI on a plane aligned with our camera. The plan is sized so that it always fills the screen, so you can move the camera around and the plane will move with the camera to appear the same as the Overlay. However, because the plane ’s drawn in the world and not on top of the screen, objects in the world can be drawn on top of your UI.
World Space: This draws a plane anywhere in the world. For example, you could use this plane as a screen in a computer in your game, or a wall or on top of your character. This is more useful in 3D games because the UI gets smaller with distance, for example.
In this case, you will keep the default Screen Space - Overlay because you want to display Ruby’s Health all the time so that it’s not hidden by objects in your world, no matter where the camera is facing.
You can ignore the other parameters for the game. For more information, see the documentation on Canvas. 
Tip: you can click the small book icon with a question mark on the component to open the documentation.


Mark step as completed
3.The Canvas Scaler
The Canvas has the Canvas Scaler component, which defines how the UI scales with different screen sizes. Some players might run your game at a resolution of 800 x 600, and others at 1920 x 1080. Or for mobile applications, maybe the app can be used in either landscape and portrait mode. All of these options need different screen sizes and ratios. 
You can set the Canvas Scaler modes to either:
1.  Constant Size (either Pixel or Physical): This makes the UI stay the same size, no matter what size or shape the screen is. This keeps the UI readable on any screens, but smaller screens might have a lot of space covered by the UI, and elements can’t overlap if the screen is too small.

2.  Scale With Screen Size: This makes the UI scale depending on the screen size you set as the Reference Resolution. 
For example, if you set the Reference Resolution to 800 x 600, and your screen is 1600 pixels wide, the UI will scale to be twice as big. That way, the UI always covers the same portion of the screen, no matter what size the screen is. 
The drawback is that this can lead to the UI being either too small to read (if your base size is big and someone plays the game on a smaller screen), or the UI appears blurry or pixelated if you make it for smaller screens and someone plays on a big screen where it’s zoomed out a lot:

For your purpose, leave it to Constant Pixel Size, because your UI is minimal and it’s easier to learn with it.
3.  Finally, the last component on a Canvas is the Graphic Raycaster. You won’t use it in this tutorial, but this allows things that are part of the canvas, like buttons, to detect when they are clicked. 


Mark step as completed
4.Adding an Image to the UI
Now that you’ve got your Canvas set up, you can add your Health meter to the UI. It will be formed of two parts: 
Part 1:  The background image, which is the portrait of Ruby portrait
Part 2:  A slot for the Health meter. The blue meter drawn on top will dynamically change based on the current health of your character. 
To add an image:
1.   Right-click on the Canvas, or click Create in the Hierarchy when the canvas is selected, and choose UI > Image . This creates an Image GameObject as a child of the Canvas, because it needs to be rendered on that canvas. 
If you open the Game window, you’ll notice a white square in the middle of the screen. You haven’t assigned a Sprite to our image yet, so it renders as a white square right now: 

But if you look in the Scene view, the white square is nowhere to be seen. That’s because the Scene and Game views handle UI position and size slightly differently. 
Until now, everything has been in “units”, so moving a GameObject 10 along one axis moves it of 10 units in the world, the Rect Transform of our UI element here is in pixels. 
So if your screen is 800 pixels wide, and your image is at position 400, it will be in the middle of the screen on the UI, but at 400 units in your Scene view, so way too far (and too big) for us to see. 


Mark step as completed
5.Editing the UI in the Editor:
1.  To edit the UI in the Editor, select the Canvas in the Hierarchy and you can either: 
Double-click on it, or
Press the F key with your mouse hovering over the Scene view.
2.  You should now see the white square and a rectangle with four blue dots that are the bounds of your Canvas. And in the bottom left corner you can see your very tiny game world.

3.  Let’s change that white rectangle to the image we want by dragging the Sprite in Art  > Sprites > UI called UIHealthFrame into the Source Image setting of our Health GameObject, the child of our Canvas. 
 The image is all squished, because it keeps the size of the rectangle. 
4.  To change the Rect Transform to the size of the image, click the Set Native Size button in the Image Inspector. Now your image should be way too big for your screen :

That’s because your image is 1336 pixels wide and your screen is smaller than that. But you’ll rescale it to a proper size.


Mark step as completed
6.Resizing your image
1.  Select your image, and make sure that the Rect tool is selected in the toolbar (shortcut key: T). 
2.  Now drag the corners or sides to resize our image. If you do hold the Shift key while you drag the corners, you will keep the right ratio while resizing, and your image will scale uniformly. 
3. You can also click and drag your image around, and it will “snap” to the Canvas corner. Let’s place it in the top left corner: 
You can always open your Game view to check how things look in your game. Placing the image is just the first part. 
Right now, if you resize the screen size (for example, by resizing the Game view), the placement of the element will change:


Mark step as completed
7.What are Anchors?
Your image is anchored to the center of the screen, but what are anchors? Look in your Scene view with your image selected:

The cross in the center of the screen is the anchor of your image. That’s the point from which the position of the object is calculated (this is shown by the green arrow, from the anchor to the pivot of your image, which is the small blue circle). 
So when the screen is resized, that position will stay the same, and the image won’t move with the screen border.
To handle this, you need to anchor the image to the corner. So if that corner moves because the screen is resized, your image will remain within the same distance and move with it. 
To anchor the image to the corner: 
1. You could move the anchor directly with the Rect Transform, but the RectTransform allows us to anchor to a corner directly.
 2.  Click on the square at the top left corner of your Rect Transform and select the top left option. 

You can see in the Scene view that the anchor has moved to the corner. 
Also note that the Pos X and Pos Y of the Rect Transform have changed: they are now computed from the corner and not the center of the canvas anymore!
Make sure your image is in the corner, and now when you resize the screen, the UI stays in the corner!
You can also rename the GameObject from image to Health, so we know it’s the health UI. Use the text box containing “Image” at the top of the Inspector and change it to Health.


Mark step as completed
8.Adding the Portrait
So now you need to add the portrait of Ruby and the blue bar to complete our Health UI.
To add the portrait:
1.  Find the portrait in Art > Sprites > UI - it’s called CharacterPortrait.
2.  Create a new image as a child of the Health Image, assign that portrait to it, click Set Native Size and resize it (while holding shift to keep the same ratio and do not squish it!). Play about with resizing it and moving it to place it in the blue circle of our Health bar background until you’re happy with the result.

You don’t really need to change the anchors here, as it is anchored to the center of its parent, which in this case is our Health GameObject. So when your Health GameObject is moved by a screen resizing, its center will also move, and your portrait will move accordingly.
But if you resize your Health bar object horizontally, it will change the center position and so move the position of the portrait, and the portrait won’t be resized:
That’s because anchor doesn’t just define the position, it also defines the size. If you press the anchor button in the Rect Transform component, and choose the expanding blue arrows at the bottom right, you will see that the 4 arrows that were the anchors move to the 4 corners of the parent image. 
Now your image size is not absolute but relative to the distance between those anchor points. So if your image size is 25% between the left and right anchors, if those are moved closer (by a resize for example) then the image will resize to stay within that ratio: 
 3.  To resize the Health bar properly,change your Rect Transform to stretch and move the anchor. You can do this by clicking and dragging them so they are around the portrait. 


Mark step as completed
9.Masking the Health Bar
Now you need to add the blue Health bar and a way to reduce the Health bar when your character gets hurt. 
You could simply scale the bar to 1 when Ruby is in full health, and then reduce the bar progressively to 0 when her health is empty. But this squishes the bar: 
Instead, you will use masking. Masking is a technique in the UI system where you can use an image as a “mask” for another image. Think of it as your first image acting like a stencil. Every part of your 2nd image that overlaps your 1st image is visible, and the other part is hidden. 


Mark step as completed
10.How to create a Health Bar Mask
To create a Health Bar mask:
1.  First create an Image GameObject child of your Health GameObject and call it Mask
2.  Resize it and move its anchors to fit the empty place in your UI where the Health bar goes: 
3.   One last step is to move the pivot, which is the blue empty circle on the left side. Why? Because when you resize it using code later, the resize will be made from the pivot. 
Note: If you were to leave your pivot in the middle, and reduce the size by 20% for example, it will resize by 10% on each side. By putting the pivot on the left side, you ensure that the 20% resize is only done on the right side. 
You don’t need to assign a Sprite to it, because you want to use that as a stencil - the default white rectangle works perfectly for your needs.
4.  Create a new image child of that Mask and assign it the sprite UIHealthBar in the folder Art > Sprites> UI. Then, instead of clicking Set Native Size as we did before, open the anchor menu by clicking on that icon in the Rect Transform of your image: 

 

5.  Now, while you keep the Alt key pressed, click the bottom right icon in the popup that appeared:

This will both set the anchor and the size of your new image to fill its parent, so your Health bar is  automatically set to the right size. Once that is done, reopen that popup and, this time, select the top left icon like earlier without pressing Alt to only set the anchor of your Health bar in the top left corner without resizing it.
6.  Now click on the Mask again, choose Add Component and search for Mask. Add it, and uncheck Show Mask Graphic to hide the white square.
7.  Resize the Mask, but be careful that it’s the Mask that you select in the Hierarchy and not the Health bar! 
This hides the bar. Because the rectangle is a stencil, when you reduce it, all parts of the Health bar that do not overlap the smaller mask are hidden. And that’s also why you set the anchor of your Health bar to the corner and not to scale with your mask. If the bar rescales with the mask, it defeats the purpose.


Mark step as completed
11.Scripting the Health Bar
Now that your visual part of our Health bar is done, let’s look at the script to handle changing it.
1.  Let’s create a new Script called UIHealthBar that contains: 
public class UIHealthBar : MonoBehaviour
{
    public Image mask;
    float originalSize;

    void Start()
    {
        originalSize = mask.rectTransform.rect.width;
    }

    public void SetValue(float value)
    {				      
        mask.rectTransform.SetSizeWithCurrentAnchors(RectTransform.Axis.Horizontal, originalSize * value);
    }
}
2.  There’s nothing new here, apart from getting the size on screen with rect.width and setting the size and anchor from code with SetSizeWithCurrentAnchors. 
3.  Your  code will call SetValue when the Health changes to a value between 0 and 1 (1 full health, 0.5 half health and so on), and this will change the size of our mask, which in turn will hide the right part of your Health bar.
4.  Now if you go back to the Unity Editor to get your script compiled, you will get an error telling you “The type or namespace name 'Image' could not be found”.That’s because Image is not part of the main UnityEngine code “namespace”, which groups all similar stuff together. Instead, it’s in a sub category called UnityEngine.UI. 
We could fix this by typing UnityEngine.UI.Image instead, but GameObject is part of the UnityEngine namespace and, until now, we didn’t have to write UnityEngine.GameObject, so why is that?
Well, at the top of your script, remember the lines with the keywords “using” which were mentioned in the first tutorial that you ignored at the time? They allow you to “import” all things inside a namespace into a script. 
The line using UnityEngine; will remove the need to type UnityEngine before all classes inside UnityEngine, like GameObject. So if you add the line using UnityEngine.UI; just below the using.UnityEngine; line, your code will compile because now Image can be used directly inside that script.
The final thing you need to do to change our Health bar is to tell the script that the health has changed. You need to call SetValue from our RubyController script’s ChangeHealth function, to give the new health amount. 
You could, as you’ve done until now, expose a public variable of type UIHealthBar in our RubyController script and assign it manually in the Inspector. But you’d need to do that in every Scene you create. 


Mark step as completed
12.Referencing
Let’s look into a new way of referencing something, by using a static member. Until now, when you created a member in a script (like our public float speed in our Enemy script), there is a copy of it for each instance for every object that uses it. If you have ten enemies, you can set ten different speeds, because each enemy has its own speed variable.
Static members are shared by all objects of that type. So, if in your enemy script you make the speed a static member (by adding the keyword static in front of it), then changing it on one enemy will change it on all enemies at once. This is because it accesses the same space in memory instead of each having their own space. It also allows us to access that variable using the class name instead of a reference (so Enemy.speed instead of myEnemy.speed, where myEnemy is a variable containing a reference to your enemy).
You’ve already used a static member: Remember Time.deltaTime ? Yes, it’s a static member of the Time class, so you don’t need to do:
Time myTime = gameObject.GetComponent<Time>();
myTime.deltaTime;

Because deltaTime is static, you can just type Time.deltaTime.
Of course, static members can also be functions and you have been using one of those too: Debug.Log. Again, you don’t need to get a reference to a Debug object, you just call the function directly on a class name.
In this case, you want to be able to access our UIHealthBar script from any other script without needing a reference. This is the modification to our UIHealthBar script: 
public class UIHealthBar : MonoBehaviour
{
    public static UIHealthBar instance { get; private set; }
    
    public Image mask;
    float originalSize;

    void Awake()
    {
        instance = this;
    }

    void Start()
    {
        originalSize = mask.rectTransform.rect.width;
    }

    public void SetValue(float value)
    {				      
        mask.rectTransform.SetSizeWithCurrentAnchors(RectTransform.Axis.Horizontal, originalSize * value);
    }
}


 Let’s look at the changes:

The static UIHealthBar instance property is static and public, so you can write UIHealthBar.instance in any script and it will call that get property. The set property is private because we don’t want people to be able to change it from outside that script.
Then in your Awake function (remember this is called as soon as the object is created, which is our case is when the game starts), you store in the static instance this, which is a special C# keyword that means “the object that currently runs that function”.
Now when the game starts, your Health bar script get its Awake function call and stores itself in the static member called “instance”. So, if in any other script you call UIHealthBar.instance, then the value it will return to that script is the Health bar in our Scene.
You now have a reference to the Health bar script in your Scene without having to assign it in the Inspector manually. Why didn’t you do that for everything else so far? Well as you’ve seen before, static members are shared across all instances of that scripts, so it is the same value in all the GameObjects with that script attached to them. 
If you have two Health bars in your Scene, the second one will store itself in the static member too, replacing the first one. So UIHealthBar.instance would always return the second one, never the first one. This is why that particular setup is called a Singleton, because only one object of that type can exist. This is exactly what you want here: to have only one Health bar. 


Mark step as completed
13.Updating the Health Bar
Now let’s update the Health bar dynamically during gameplay. Just open your RubyController script, and in the ChangeHealth function, replace the Debug.Log line with:

UIHealthBar.instance.SetValue(currentHealth / (float)maxHealth);
You give the ratio of our currentHealth over our maxHealth to our UIHealthBar SetValue function. The (float) before maxHealth makes C# think maxHealth is a floating point value. 
Both currentHealth and maxHealth are integers, and dividing two integers is treated as a whole division by C#, so 2/4 won’t give 0.5 but 0. Forcing one of the numbers to be a float makes this become 2/4.0, which gives us a float result equal to 0.5.
You can now add the UIHealthBar script to your Health bar GameObject, drag your mask into the Mask properties in the Inspector and enter Play mode. If you make Ruby get damaged by the enemy or damage zone, her Health bar will update accordingly.


Mark step as completed
14.Check Your Scripts
Your RubyController script should now look like this:
﻿public class RubyController : MonoBehaviour
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
Your UIHealthBar script should now look like this:
﻿using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class UIHealthBar : MonoBehaviour
{
    public static UIHealthBar instance { get; private set; }
    
    public Image mask;
    float originalSize;
    
    void Awake()
    {
        instance = this;
    }

    void Start()
    {
        originalSize = mask.rectTransform.rect.width;
    }

    public void SetValue(float value)
    {				      
        mask.rectTransform.SetSizeWithCurrentAnchors(RectTransform.Axis.Horizontal, originalSize * value);
    }
}


Mark step as completed
15.Summary
In this tutorial you have seen how Unity renders a UI, and how you can use the Rect tool in the Editor to place and size an element so that it works well with multiple scales.
You also learned how to use static members in scripts and Singletons, to make your UIHealthBar script accessible from anywhere.
In the next tutorial you will enhance your UI a bit more to add a character you can talk to, and introduce an important concept for video game making: Raycasting.


Mark step as completed

Mark all steps as completed


