# 2.1 Design Frame

Systems Diagram

<figure><img src="../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

This systems diagram shows the different aspects of my game. These aspects have come from my [success criteria](../analysis/1.5-success-criteria.md), and therefore it demonstrates what I want to achieve in my game. They have been broken down into smaller, sub-sections which are more manageable and combine together to finish the overall tasks at hand. These sub-sections are what I can go about aiming to achieve in my cycles, as they are smaller tasks and they will eventually lead to the finished project of my game. The dividing of these tasks is done with [computational methods](../analysis/1.4b-computational-methods.md) in mind, namely [decomposition](../analysis/1.4b-computational-methods.md#thinking-procedurally-and-decomposition).

## Usability Features

Usability is an important aspect to my game as I want it to be accessible to all. There are 5 key points of usability to create the best user experience that I will be focusing on when developing my project. These are:

### Effective

Users can achieve the goal with completeness and accuracy. To do this, I will make it easy for the players to realise that they need to reach a goal in order to complete a level. I will make this goal clear to see so there is no confusion over where the players need to go.&#x20;

#### Aims

* Create a goal to reach to determine the end of a game
* Create a clear goal for multiplayer&#x20;
* Create a clear goal for puzzles and minigames
* Create fair gameplay for all users

### Efficiency

The speed and accuracy to which a user can complete the goal. To do this, I will create a menu system which is easy to navigate through in order for to find what you are looking for. The information which is more important can be found with less clicks. The mock in [1.4a](../analysis/1.4a-features-of-the-proposed-solution.md#user-interface) shows that on the opening screen there will be 3 tabs for the players to click.

#### Aims

* Create a menu system that is quick and easy to navigate through
* Create a controls system that isn't too complicated but allows the player to do multiple actions

### Engaging

The solution is engaging for the user to use. To do this, I will create an engaging world and multiplayer to keep the players engaged and allow them to have fun while playing the game. Using pixel style art will also make the game nicer to look at, so will draw more people in, keeping them engaged.

#### Aims

* Create a multiplayer mode to play
* Create puzzles and minigames to play
* Incorporate a style of game art the suits the game

### Error Tolerant

The solution should have as few errors as possible and if one does occur, it should be able to correct itself. To do this, I will write my code to manage as many different game scenarios as possible so that it will not crash when someone is playing it.

#### Aims

* The game doesn't crash
* The game does not contain any bugs that damage the user experience

### Easy To Learn

The solution should be easy to use and not be over complicated. To do this, I will create simple controls for the game. I will make sure that no more controls are added than are needed in order to keep them as simple as possible for the players.

#### Aims

* The game should not be too hard for all players to complete
* Create ways of helping the user to beat certain levels

## Pseudocode for the Game

### Pseudocode for a level

This shows the basic layout of code for a scene. It shows where each task will be executed.

```

 define scene
        load all sprites and music
    
        start music
        add background
        create players
        create platforms
        create puzzle elements
        create obstacles
        add key bindings
    
        add object interaction
        add new objects
        update all animations
        check if player at exit
        go new scene
end scene
```
