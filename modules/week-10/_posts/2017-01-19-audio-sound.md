---
title: Audio
module: 10
jotted: true
---

# Audio Clips, Audio Source and Audio Listener

The Unity sound system is comprised of: 

1. Audio Clips 
    - Audio Clips are Assets, like textures or scripts. You can import Audio Clips from an audio file, such as mp3, ogg and wav files, and they live in your Project folder. You can find the Audio Clips for this tutorial Project in the Audio folder.
2. Audio Listener
    - Audio Listener is a component that defines where the “listener” is in the Scene. This is useful when you use spatialized sound, which is the kind of sound that plays more on the left/right speakers (or even back/front on some installations) to give the illusion of it being around the player. 
    - By default, this is placed on the Camera because players expect to hear things from the Camera’s position, so a sound on the right of the screen should play on the right speaker. 
    - If you click on your Camera in the Hierarchy, you can see it’s got an Audio Listener component on it.
3. Audio Source
    - Audio Source is a component which allows you to play an Audio Clip at the position of the GameObject on which the component is. Its position relative to the Audio Listener will make the Audio System mix the sound so it appears to be spatialized properly (if we use spatialized sound).
    - Even if you don’t use spatialized sound, for background music for example, you can still use an Audio Source on a GameObject because it plays a sound.


### Background music

Start by making some background music that can play all the time:

1. Create an empty GameObject, name it BackgroundMusic and add an Audio Source component to it.
2. Drag and drop the audio clip called 2D MUSIC LOOP in the Audio folder in the Project into the AudioClip property slot.
3. Make sure you check the Loop option, so your music continues playing from the beginning when it reaches the end.
4. And check the Spatial Blend slider, which can go from 2D (left side) to 3D (right side). 
    - This defines whether the sound is spatialized or not. If the slider is all the way on 2D, the sound is not spatialized and it will play at the same level no matter where our Audio Listener is. 
    - It's a bit like listening to music in a music player, with the stereo that is set in the music. If the slider is all the way to 3D, the sound will play more or less in the right/left speaker depending on where the Audio Source is in relation to the Audio listener. 
    - Since your music needs to be heard the same everywhere, make sure the slider is all the way to 2D. You can ignore the other properties for now. 
    Tip: If you’re curious, click the book icon with a question mark on the top right corner of the component to open the Unity Manual. 

5. Now enter Play mode and you should hear the music start as soon as the game starts. You can always play with the volume slider if the volume is too loud. 

**Note:** Remember that any change you make as the game runs will be “undone” when exiting Play mode, so make sure you note the values you want to use and adjust the settings outside of Play mode.

6. If during development you need to mute all sound for any reason, click the Mute Audio button in the top right corner of the Game View. If you can’t hear any sound when there should be sound, it’s worth seeing whether this button is enabled.

### One Shot Sound

Assigning an Audio Clip is good for when you have sounds that are always playing. But sometimes you need to play a sound a single time when something happens, for example when a character gets a health collectible.

One option would be to create a new Audio Source, assign the health collectible Audio Clip and uncheck the Play On Awake option so it doesn’t play when the game starts. 

Then in script you could make the Audio Clip play when the event happens. But that would require creating a GameObject and Audio Source for every little sound in the game.

Instead, you will use an AudioSource function called PlayOneShot. Unlike Play, which plays the audio clip currently assigned to the Audio Source, PlayOneShot takes the audio clip as its first parameter and plays that audio clip once, with all the settings of the Audio Source, at the position of the Audio Source.
So you can add an Audio Source to our Ruby GameObject, and use that Audio Source to play all sounds related to the gameplay actions that Ruby does, like grabbing a health pack, throwing a cog or being hit.

**Note:** if you added the Audio Source to Ruby in the Scene and not in Prefab mode, apply the override in the Inspector!

### After adding an Audio Source to Ruby:

1. Open your RubyController script and add a private AudioSource variable called audioSource to store the Audio Source and retrieve it in the Start function with GetComponent.
2. Then let's write a function called PlaySound that takes an AudioClip as a parameter and just call PlayOneShot on our AudioSource:
AudioSource audioSource;

```csharp
void Start()
{
    rigidbody2d = GetComponent<Rigidbody2D>();
    animator = GetComponent<Animator>();
    currentHealth = maxHealth;

    audioSource= GetComponent<AudioSource>();
}

public void PlaySound(AudioClip clip)
{
    audioSource.PlayOneShot(clip);
}
```

3. Now, open the HealthCollectible script and add a public member of type AudioClip called collectedClip. And then call the PlaySound function on the RubyController:

```csharp
public class HealthCollectible : MonoBehaviour
{
    public AudioClip collectedClip;
    
    void OnTriggerEnter2D(Collider2D other)
    {
        RubyController controller = other.GetComponent<RubyController>();

        if (controller != null)
        {
if (controller.health < controller.maxHealth)
            {
            	controller.ChangeHealth(1);
            	Destroy(gameObject);
            
            	controller.PlaySound(collectedClip);
}
        }

    }
}
```

Why are you using an Audio Source on Ruby and not on the collectible? Well, because an Audio Source is a component. When Ruby grabs the collectible, it gets destroyed. This would also destroy the Audio Source and stop the sound from being played.

By playing the sound through an Audio Source on Ruby, the sound can be played even when the collectible gets destroyed.

4. Now check your Health Collectible Prefab in your Project window. A new slot called Collected Clip is now available on the Health Collectible component as you made that variable public. Drag and drop the Collectable audio clip you can find in the Audio folder into that slot.
5. You can now enter Play mode and get Ruby to grab a health pack to hear the sound - don’t forget you need Ruby to get damaged by the robot first to lose some health!

### Exercise

As an exercise, you can try to add a sound when Ruby throws a cog and/or when she gets hit by an enemy. You will need to: 

Add a public AudioClip member to your RubyController script to store the throwing sound or hit sound Audio Clip, just like we did in the HealthCollectible just above.

Call PlayOneShot on the Audio Source at the right place in the code in RubyController script.

### Spatialization

Until now, you’ve used 2D sound. This plays at the same volume no matter where you are placed compared to the source. That made sense because the sounds were "gameplay" sounds that weren’t part of the world (also called extradiegetic/non-diegetic sound).

But in lots of interactive creations, you want sound to exist in your world, so now you’ll add the sound of the robots walking.

1. Open the Enemy robot Prefab and add an Audio Source to it:
2. Set the clip to the Audio Clip in the Audio folder called Robot Walking_Broken.
3. Check the Loop setting.
4. Finally, move the Spatial Blend slider all the way to the right to 3D to make it a spatialized sound.

In the Scene view, you’ll see a blue circle around the speaker icon.

This is the minimum distance of the spatial blend setting of our Audio Source. If the Audio Listener is inside that circle, it will hear sound at maximum volume. Then the sound will slowly attenuate until it reaches the maximum distance, where it will be silent. 


### What is the Maximum Distance?

1. You will need to zoom out of the Scene view a lot to see it: 
    - It will look too big and you will need to make it smaller. As long as the Audio Listener is inside that circle, it will hear the walking sound but that distance is way bigger than your entire world right now.
    - You could drag the small dot on the side of the circle, but it’s easier to set it in the Inspector. 
2. At the bottom of the Audio Source Inspector, open the 3D Sound Settings section to find the Min Distance and Max Distance settings:
3. Currently, our Max Distance is set to 500 units, which is pretty large. Let’s change that to 10 units. The max distance circle should now be at a much more practical size.
    - Outside of that circle, the sound won’t be heard. So in that setup, if the listener is closer than 1 unit from the source, it will play the sound at maximum volume, if it’s at 5 units, it will play it at half volume and further than 10 units from the source will mute the sound as the volume will be 0.
4. Now save the Prefab and go back to the Scene. 

Right now, if you press Play and try it, your attenuations will not work and you won’t hear the sound. That is because the Sound System is made for 3D. So that circle is actually a sphere.

You can switch the Scene View to 3D to show that sphere. 

As the above capture shows, the camera sits slightly above your whole game. So even if the robot is in the center of the screen, and the Camera is directly above, the Audio Listener on the Camera is still at the max distance from the Audio Source, and the attenuation is maximum!

### Fixing attenuation

1. To fix attenuation, you will need to place the Audio Listener at the same depth as the rest of your GameObjects, so z = 0. 
    - You can’t change the Camera, because if the Camera is on the same z then it will break the rendering. 
    - Instead, you are going to create a child GameObject to the Camera. Make sure that z coordinates with the Audio Listener. That way, it will move with the Camera, always in the center of the screen, but attenuation will be computed correctly based on the 2D distance.
2. Select the Main Camera and create a new Empty GameObject as a child. Name it Listener, add an Audio Listener to it and set its coordinates in its Transform to x = 0, y = 0 and z = 10. 
    - Remember the position set here is relative to the parent, thus placing the child GameObject 10 units in the front of the Camera. 
    - Since the Camera is 10 units back from the plane, that will place the child GameObject exactly at z = 0 in the world.
3. On the Camera, right-click on the Audio Listener and choose Remove Component.
4. Now your setup is ready, and if you enter Play mode, the robot walking sound will be spatialized (playing left or right) and attenuated when the robot gets farther from the center of the screen as expected.

### Check Your Scripts

Your RubyController script should now look like this:

```csharp
public class RubyController : MonoBehaviour
{
    public float speed = 3.0f;
    
    public int maxHealth = 5;
    
    public GameObject projectilePrefab;
    
    public AudioClip throwSound;
    public AudioClip hitSound;
    
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
    
    AudioSource audioSource;
    
    // Start is called before the first frame update
    void Start()
    {
        rigidbody2d = GetComponent<Rigidbody2D>();
        animator = GetComponent<Animator>();
        
        currentHealth = maxHealth;

        audioSource = GetComponent<AudioSource>();
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
            
            PlaySound(hitSound);
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
        
        PlaySound(throwSound);
    } 
    
    public void PlaySound(AudioClip clip)
    {
        audioSource.PlayOneShot(clip);
    }
}
```

Your HealthCollectible script should now look like this:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class HealthCollectible : MonoBehaviour
{
    public AudioClip collectedClip;
    
    void OnTriggerEnter2D(Collider2D other)
    {
        RubyController controller = other.GetComponent<RubyController>();

        if (controller != null)
        {
            if (controller.health < controller.maxHealth)
            {
                controller.ChangeHealth(1);
                Destroy(gameObject);
            
                controller.PlaySound(collectedClip);
            }
        }

    }
}
```

### Summary

With this section you completed the last big part of an interactive application: integrating sounds.

You've seen how to handle 2D sound, sounds that play at the same volume no matter where the character is in your Scene. You have also learned that 3D sound is played at different volumes and in different speakers based on where the sound is compared to your Camera.

The next section will be your last one! Now you have every bit of a game done, it’s time to take a look at how to create the application you’ll distribute to your users, so they don’t have to install Unity to play your game.


Mark step as completed