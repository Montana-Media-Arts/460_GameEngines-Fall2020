---
title: How to Extend
module: 5
jotted: true
---


# Extend Your Game

Now, what will you do to make your game more interesting?  Will you add more quests? Will they be dependent on other quests?  Will you add more NPCs?  What about customization?  

Take some time and add more quests, NPCs, and stories along with plants and more.

For Wednesday, be prepared to show your RPG game and what you added to it. Describe the storyline, the motivation and what makes your game a game?  What are the goals?  Is there an over-arching theme?  

Talk about how you are going to test and have others test your game.  

What do we need to change to add a quest to another quest? Here is an example.

```csharp

    if(GameObject.FindGameObjectWithTag("firstquest") != null)
    {
        Destroy(GameObject.FindGameObjectWithTag("firstquest"));
        GameObject Archer = GameObject.FindGameObjectWithTag("archer");
        ConversationScript myScript = Archer.GetComponent<ConversationScript>();
        Destroy(myScript);
    }

```