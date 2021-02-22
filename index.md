## Welcome to Jober's Homepage



### Breakout 
![Image of Breakout](https://imgur.com/a/hVvENGy)
#### Post Mortem
For my first foray into creating a game from the ground up this one went pretty good. There are a couple of changes I would make if I had 8 more weeks to work on this project. I think the biggest problem I had in the structure of my code was that my util header file was a but of a mess, holding a bunch of different class structures that would have been better off seperated out. Ball, Paddle, Arena, and Brick would have all been better off in their own BreakoutObject.hpp header while PlayerScore was instead put into a header file more focused on controlling the game, like GameController.hpp. I would have also set up a GameManager class to keep track of the score, lives and levels instead of just having them be free floating in the main of breakout.cpp. 

The other big changes I would have made was create a better way of checking wether the ball was colliding with a brick or not and to add a degree of randomness for how the ball bounced off the paddle. The current implementaion of ends up checking every brick in the grid every frame for a collision with the ball when I could almost certainly cut that down to a fraction of the number of comparisons. A potential solution would have been to checked the 4 corners of the ball to see where on the grid of bricks each corner landed and only checked those 4 bricks. The would have limited my number of checks each frame to a maximum of 4, but most likely 1-2, as the size of the ball would limit it from being over more than 4 squares at ones, presuming that it managed to move fast enough that it crossed into 4 squares between frames. The ball not being randomized lead to some repeating patterns in how the ball moved that could be frustrating to play against and randomization should help to break those patterns and lead to a more fun experience.
