---
title: Build and Distribute
module: 10
jotted: true
---

# Player Settings

The application you create from the Editor to distribute to users is called the Player. Before creating the Player, let’s have a quick look into the Player Settings. 

1. To find the Player Settings, open the menu Edit > Project Settings and open the Player category.

This page enables you to change and tweak a lot of settings for the game you will distribute. 

At the top of that page, you can set your:

* Company Name, which is used to create the folders where the files created by the games will be stored, or in other system related things.
* Product Name, which is the game or application name. This will be used to name the executable/bundle (depending on the platform) and create a place under your company name to save all things related to that game in particular.
* Default Icon, which is the application’s icon, for example the app icon on mobile and the executable icon on desktop.
* Default Cursor, which you can set to have a cursor that is different than the system arrow.

The downward arrow at the top of the next section here tells us that all the settings in this section are for PC, Mac & Linux Standalone platforms. If you have installed support for other platforms when installing Unity, you will see multiple button in that toolbar.

Each section can be clicked on to expand it and show its settings.  Only a couple will be highlighted here, but you can find an explanation of all settings in the documentation on Player settings for Standalone platforms.

2. Ignore the "Icon" section because it specifies additional icons to the Default Icon for different resolutions, and instead start by opening the Resolution and Presentation section by clicking on it.

The first part, Resolution, allows us to define the default mode that the game starts in. The Run In Background setting determines whether your game continues to run if the window/application doesn't have focus. 

For example, when that option is disabled and the person playing the game opens a web browser and browses the web while playing, the game will pause until they return to the game and the game becomes the focus application again.

3. In the Standalone Player Options section, make sure that Display Resolution Dialog is set to Enabled. This allows us to show a window when the user launches the game so that they can select the resolution.

As for the other options, the default settings generally work with most games, but refer to the manual for more explanation.

4. Finally, in the Splash Images section, you can change the image shown at the top of the above dialog (Application Config Dialog Banner) or the logo shown when the game starts (Logos).  


### Building the Game

Now that you have set up our Player settings, it’s time to build your game. This takes all the Assets, like scripts, images and sound, and packages them in an optimized format for distribution.

1. To build your application in Unity, open the Build window by selecting File > Build Settings.
2. The Scenes in Build section at the top lists all the Scenes that will be included in your game. You can have Scenes in your Project that you only use to test features or to debug, so Unity needs to know which ones to include in the final product. 
3. If your main Scene is still open, just click Add Open Scenes to add it to the list. Or you can also drag and drop your Scenes from your Project Window to that part of the Build Settings window.
4. The Platform section in the bottom left allows you to choose which platforms you want your game to run on. By default, the Editor only supports the platform that it is installed on. To install more platforms, open the Unity Hub, click Installs, click the three dots next to the relevant Unity version, click Add Component and select the platforms. 
5. Finally, in the bottom right are settings related to the current selected Platform. These settings are mostly for debugging or special builds, so you can ignore most of them for now. 
