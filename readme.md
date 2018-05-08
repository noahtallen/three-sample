## Description:

This solution incorporates both parts 1 and 2 from the problem set. I decided to solve the "cloning objects" exercise, as well as incporporate interactivity with the scene.

The starter code for this project is found on Dr. Dailey's site [1], but this code has been heavily modified to support my own unique solution to the problem.

### Part 1 - Cloning
I decided to use both a timer and randomization to clone objects. I created a few helper functions:

1) A loop that clones a bird, sets a timeout, then clones another bird
2) Function to randomize color and position of the clone
3) Function to ensure the randomized position stayed within the bounds of the camera's screen. The two functions that do this were taken from the THREE js discussion boards [2].

To actually solve the cloning, after the initial bird is created, I pushed it into an array called `birds` and set up a `currentBird` variable which is initialized to 0. Then, in the cloning function, I clone `birds[currentBird]`. That way, I always clone the last bird generated. Then, I randomly generate position coordinates which are designed to stay within the bounds of the camera's FOV. I also clone the material of the bird so that I can randomly generate each component of an RGB color to set the color of the newly cloned bird. Then, I push the new bird into the array and add it to the scene.

I modified the render code to animate each bird in the array. I loop through the array, and update the birds rotation position. To make it interesting, the `z` component is incremented by `0.02` every time, but the `y` component is dynamic. Essentially, I created a function which can take the index of the bird in the array, and use that index number to generate a dynamic rotation value depending on the index. I first set this function to `(n) => 0.5 / Math.sqrt(n)`. This allows each bird to rotate differently than the others. The first one rotates quickly, but later ones rotate much more slowly.

### Part 2 - Interactivity
I added interactivity in several ways.

1) Allowed the user to define the rotation function for the `y` component of rotation.
2) Allowed the user to define the timeout between bird creations.
3) Allowed the user to navigate the scene with the camera.