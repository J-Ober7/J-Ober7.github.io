# Welcome to Jakob Ober's Homepage


## Some of my Projects
  
  
  
## Drummage: Dungeon of the Bongo-d

### Trailer
[![](http://img.youtube.com/vi/MaS38SrlOtI/0.jpg)](http://www.youtube.com/watch?v=MaS38SrlOtI "Trailer")

### Post Mortem
Made for the final project of my Game Programming Class, Drummage was my first forray into implementing a rythm game of any kind. My biggest contribution to the game was the combat system that it used to handle the player's interactions with enemies. The combat system made use of a modular action system where the player decided which actions they would take and in which order they would come in. Each action was made up of a series of up to 8 inputs that had to be played in rythm to be executed correctly by the player. The player's inputs had to be paired up as either notes or stored seperately as quarter notes depending on between their inputs and then further paired up to form the 4-8 note chords that made up each action they could take in combat. Once the chord was selected it had to be then checked against whichever chord the player had chosen to try and cast in that slot to see if it matched. Correctly matched chords then produce whichever action they player was trying to complete. 

This need for very precise windows of time to be tracked in order to correctly place the players inputs into the the correct notes was an interesting challenge, as I had to keep track of 3 different times at any given moment: the time between the current and previous frame, the time between the last not and the current one, and the time until the current chord's window for input was closed. There were quite a number of headaches along the way when I was first designing the system to make sure that inputs weren't being dropped or overridden if player inputed to fast or slowly.

If I were to go back and redo this game the biggest thing I would change would have been to try and seperate out all the different tasks that the main rythm loop had. It dealt with far too much of its logic for creating and tracking the player's input patterns inside of the the loop that it used keep track of the current note and chord the clock was on, and that logic for the inputs could have been seperated out into seperate supporting functions instead.

## Breakout 
![Image of Breakout](https://J-Ober7.github.io/media/breakout/BreakoutLevel1.PNG)
### Post Mortem
For my first foray into creating a game from the ground up this one went pretty good. There are a couple of changes I would make if I had 8 more weeks to work on this project. I think the biggest problem I had in the structure of my code was that my util header file was a but of a mess, holding a bunch of different class structures that would have been better off seperated out. Ball, Paddle, Arena, and Brick would have all been better off in their own BreakoutObject.hpp header while PlayerScore was instead put into a header file more focused on controlling the game, like GameController.hpp. I would have also set up a GameManager class to keep track of the score, lives and levels instead of just having them be free floating in the main of breakout.cpp. 

The other big changes I would have made was create a better way of checking wether the ball was colliding with a brick or not and to add a degree of randomness for how the ball bounced off the paddle. The current implementaion of ends up checking every brick in the grid every frame for a collision with the ball when I could almost certainly cut that down to a fraction of the number of comparisons. A potential solution would have been to checked the 4 corners of the ball to see where on the grid of bricks each corner landed and only checked those 4 bricks. The would have limited my number of checks each frame to a maximum of 4, but most likely 1-2, as the size of the ball would limit it from being over more than 4 squares at ones, presuming that it managed to move fast enough that it crossed into 4 squares between frames. The ball not being randomized lead to some repeating patterns in how the ball moved that could be frustrating to play against and randomization should help to break those patterns and lead to a more fun experience.
