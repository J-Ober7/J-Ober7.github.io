# Welcome to Jakob Ober's Homepage


## Some of my Projects



## An SDL Platformer: Learning Game Engines (Group: Fen, Izzy, Jakob)

### Source Code 
file:///C:/Users/cyber/GitHub/Assignment2/platformer-jakob_fen_izzy/Game/Docs/html/index.html

### Post Mortem
For this project, the group learned quite a bit about the different struggles that designers can face when trying to implement different design patterns to build the foundatoin of a game engine. In particular, division of information and determining where and what classes should be getting what information was one of our main problems and it occupied quite a bit of our planning talks. Ultimately, what we decided to do was have a Collision manager determine who was doing the collisions and the have the CollisionComponet hand the generated CollisionEvents back to our primary GameObject, where the CollisionEvents would then be accessible by all the other components attached to the GameObject, which would then handle all the logic regarding handling the different collisions. 

We also spent quite a bit of time learning how to develop tools using python, in specific the TKinter libarary. Outside of one issue of a corrupted python library preventing one of the group members being unable to run the program, the development of our two tools we used for this project, a TileMap editor for loading up TileAtlases and creating and saving tile maps, as well as a sprite previewer, which could be used cut out and view specific sequences of sprites from a sprite sheet, went quite well. The only hick-up we had was an issue with animating the sprite cut out by the sprite editor in the window, due to a quirk of the python Application.

If we had another 8 weeks to work on this project, we would focus on fleshing out our game. Currently our project was mostly focused on getting a basic engine with a component system working. To flesh out our game, we would add more levels, abilities, and enemies, adding more sophisticated elements to our engine as we need. We would also swap in new assets that better adhere to our game's identity. Finally, we would add polish such as having a title screen and game menu.




## Clockwork Story: A Mouse and His Tower

### Trailer
[![](http://img.youtube.com/vi/k-ct4xtg0ko/0.jpg)](http://www.youtube.com/watch?v=k-ct4xtg0ko "Trailer")

### Repository
https://github.com/J-Ober7/Clockwork-Story

### itch.io
https://gregoryloden.itch.io/clockwork-story

### Post Mortem
Clockwork Story was the game my team made as part of my first Global Game Jam. The theme for the game jam had be "rebuild/repair" and after a couple of hours tossing ideas back and forth we eventually settled on the clockwork theme as one that could be fun to work with. The core gameplay was rather simplistic, focuesed on the player shuffling around a series of cogs to lift the bell up the floors of the tower and gain access to the higher floors, with the end goal of bringing the bell to the top of the tower and making it ring. My favorite part of working on this project was probably working the the music that Stephen, our very talented musician, was able to make over the course of the weekend. Using FMod, we were able to split up the sound track into three seperate tracks of differing intensities based off of how far up the tower the bell was. The end result was that the tower had a feeling of coming alive as you were able to bring the bell higher and higher into the tower and more of the clockwork-like instramentals were brought into the BGM.
  
  
  
## Drummage: Dungeon of the Bongo-d

### Trailer
[![](http://img.youtube.com/vi/MaS38SrlOtI/0.jpg)](http://www.youtube.com/watch?v=MaS38SrlOtI "Trailer")

### Repository
https://github.com/J-Ober7/Drummage-Dungeon-of-the-Bongod

### Post Mortem
Made for the final project of my Game Programming Class, Drummage was my first forray into implementing a rythm game of any kind. My biggest contribution to the game was the combat system that it used to handle the player's interactions with enemies. The combat system made use of a modular action system where the player decided which actions they would take and in which order they would come in. Each action was made up of a series of up to 8 inputs that had to be played in rythm to be executed correctly by the player. The player's inputs had to be paired up as either notes or stored seperately as quarter notes depending on between their inputs and then further paired up to form the 4-8 note chords that made up each action they could take in combat. Once the chord was selected it had to be then checked against whichever chord the player had chosen to try and cast in that slot to see if it matched. Correctly matched chords then produce whichever action they player was trying to complete. 

This need for very precise windows of time to be tracked in order to correctly place the players inputs into the the correct notes was an interesting challenge, as I had to keep track of 3 different times at any given moment: the time between the current and previous frame, the time between the last not and the current one, and the time until the current chord's window for input was closed. There were quite a number of headaches along the way when I was first designing the system to make sure that inputs weren't being dropped or overridden if player inputed to fast or slowly.

If I were to go back and redo this game the biggest thing I would change would have been to try and seperate out all the different tasks that the main rythm loop had. It dealt with far too much of its logic for creating and tracking the player's input patterns inside of the the loop that it used keep track of the current note and chord the clock was on, and that logic for the inputs could have been seperated out into seperate supporting functions instead.

## Breakout 
![Image of Breakout](https://J-Ober7.github.io/media/breakout/BreakoutLevel1.PNG)
### Post Mortem
For my first foray into creating a game from the ground up using SDL, this one went pretty good. There are a couple of changes I would make if I had 8 more weeks to work on this project. I think the biggest problem I had in the structure of my code was that my util header file was a but of a mess, holding a bunch of different class structures that would have been better off seperated out. Ball, Paddle, Arena, and Brick would have all been better off in their own BreakoutObject.hpp header while PlayerScore was instead put into a header file more focused on controlling the game, like GameController.hpp. I would have also set up a GameManager class to keep track of the score, lives and levels instead of just having them be free floating in the main of breakout.cpp. 

The other big changes I would have made was create a better way of checking wether the ball was colliding with a brick or not and to add a degree of randomness for how the ball bounced off the paddle. The current implementaion of ends up checking every brick in the grid every frame for a collision with the ball when I could almost certainly cut that down to a fraction of the number of comparisons. A potential solution would have been to checked the 4 corners of the ball to see where on the grid of bricks each corner landed and only checked those 4 bricks. The would have limited my number of checks each frame to a maximum of 4, but most likely 1-2, as the size of the ball would limit it from being over more than 4 squares at ones, presuming that it managed to move fast enough that it crossed into 4 squares between frames. The ball not being randomized lead to some repeating patterns in how the ball moved that could be frustrating to play against and randomization should help to break those patterns and lead to a more fun experience.
