# Level 2: You can animate things by redrawing the canvas

###### Note: *This level originally appeared [here](http://cs.okstate.edu/~clined/levelUp/level2.html).*

HTML Canvas is great. It allows you to draw just about anything. But to make a game, we have to move things on the screen. How do we do this? The answer is that we redraw the whole canvas many times per second so that it looks like things are moving. This level goes through how to do that. It also presents a bunch of programming concepts needed to make it happen.

***

### Variables

Variables are the way that computer programs keep track of things. JavaScript variables can hold different kinds of data. In this lesson, we will learn about three types of data that can be held in variables:

- numbers

- objects (a set of key-value pairs)

- functions

In later lessons we will learn about some other kinds of variables, including strings, booleans, and arrays.

***

### The gameState object variable

In the level 2 example, the `gameState` variable holds all the information about the object on the screen. We “declare” the variable at the top of the script with the code:

```javascript
var gameState;
```

By declaring the variable at the top of the script, outside of any function, it can be used anywhere. This is called a “global” variable.

gameState is “initialized” in the function `window.onload` with the code

```javascript
gameState = {};
gameState.shipX = 0;
gameState.shipY = 100;
gameState.shipImage = document.getElementById("shipImage");
```

The first line, `gameState = {};`, tells the computer to make a new **object** with nothing inside it. An object is like a box that can hold other variables by name (called “key-value pairs”).

The next two lines define the properties shipX and shipY of gameState. These store the coordinates where we will draw the ship. shipX and shipY will change later, and that’s how we animate the page.

The next line is like something you have seen before. Remember that the code `document.getElementById("shipImage");` gets a reference to the “shipImage” element on the page. The left part of this line, `gameState.shipImage =`, copies the shipImage reference to the gameState object in a variable called `shipImage`.

***

### Functions in JavaScript

One of the things you can do in JavaScript is to make “functions”. Functions are a way to package up some computer code so that it can be run together. The way that we define functions is to define it as a variable. In code it looks like this:

```javascript
var myFunction = function()
{
    // code goes here
}
```

The code above defines a function called `myFunction`.

***

### `window.requestAnimationFrame`

The way that you do animation in the computer is to redraw the canvas over and over, changing something each time. In fact, to make the motion look smooth, you have to redraw 30 or 60 times per second!

In JavaScript, we can make the browser run the animate function over and over using `window.requestAnimationFrame`. In your code, you would put this call in your function to animate like this:

```javascript
var animateGame = function()
{
    // Call animateGame again in about 1/60 of a second
    window.requestAnimationFrame(animateGame);
    ....
```

`window.requestAnimationFrame(animateGame)` tells the compute to call the `animateGame` method again in about 1/60 of a second.

***

### The `animateGame` function

The goal of the `animateGame` function is to do two things:

1. Update everything about the game for 1 “frame” of time (about 1/60 second.)

2. Redraw the game.

In the level2 example, the only thing that changes each time is the x coordinate of the ship position (shipX), so the ship moves horizontally across the screen:

```javascript
// Update the gameState
// change the x location of the ship
gameState.shipX += 1.0;
if (gameState.shipX > 600)
{
    gameState.shipX = -180;
}
```

The first line of this code, `gameState.shipX += 1.0;`, adds 1 to the ship x coordinate at each time step. This causes it to move from left to right across the canvas.

The second part of the function resets the position of the ship to be to the left of the canvas (shipX = -180) if the ship moves too far to the right.

- How would you make the ship move left instead of right?

- How would you make the ship move up or down?

- What if you wanted the ship to move diagonally?

- How could you make the ship bounce off the edge of the canvas?

***

### Drawing the ship

Programs can get complicated, and it’s a good idea to try and organize your code so that things make sense. One way to do this is to use different functions to do different things. In the example, the code to draw the game is put in a function called `drawGame`. This function is called at the end of the `animateGame` function.

The `drawGame` function clears the canvas in a light blue color and draws the ship at its current location. One cool thing we have done here is to look up the width and height of the canvas, so the that function will work no matter how big the canvas is.

```javascript
var drawGame = function()
{
    var w = canvas.width;
    var h = canvas.height;

    // Draw a background rectangle
    drawing.fillStyle = "#BBBBFF";    // light blue fill color
    drawing.fillRect(0,0,w,h);    // fill the canvas with light blue
    drawing.strokeRect(0,0,w,h);  // draw a black border

    // Draw the ship image
    drawing.drawImage(gameState.shipImage, gameState.shipX, gameState.shipY);
}
```

- What would happen if we didn’t clear the background each time?

***

### Putting it All Together

That was quite a bit to take in. If we put it all together, we get the code below.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Moving Ship</title>
</head>

<body>

    <h1>Moving Ship</h1>

    <canvas id="myCanvas" width="600" height="400"></canvas>

    <img id="shipImage" style="display:none;"
    src="http://cs.okstate.edu/~clined/levelUp/ship.png"></img>

    <script>
    //-------------------------------------------------------------------
    // The gameState variable will store all information about the
    // game, such as what objects exist, where they are and the score.
    //-------------------------------------------------------------------

    var canvas;
    var drawing;
    var gameState;

    //-------------------------------------------------------------------
    // The drawGame function redraws the whole canvas for each frame
    // of the game.
    //-------------------------------------------------------------------

    var drawGame = function()
    {
        var w = canvas.width;
        var h = canvas.height;

        // Draw a background rectangle
        drawing.fillStyle = "#BBBBFF";    // light blue fill color
        drawing.fillRect(0,0,w,h);    // fill the canvas with light blue
        drawing.strokeRect(0,0,w,h);  // draw a black border

        // Draw the ship image
        drawing.drawImage(gameState.shipImage, gameState.shipX, gameState.shipY);
    }

    //-------------------------------------------------------------------
    // The animate function gets called for each frame. It updates
    // the gameState variable and then calls drawScreen.
    //-------------------------------------------------------------------

    var animateGame = function()
    {
        // Call animateGame again in about 1/60 of a second
        window.requestAnimationFrame(animateGame);

        // Update the gameState
        // change the x location of the ship
        gameState.shipX += 1.0;
        if (gameState.shipX > 600)
        {
            gameState.shipX = -180;
        }

        // Draw the game
        drawGame();
    }

    //-------------------------------------------------------------------
    // The window.onload function will run when the page first loads
    //-------------------------------------------------------------------

    window.onload = function()
    {
        // Get the canvas and drawing context
        canvas = document.getElementById("myCanvas");
        drawing = canvas.getContext("2d");

        // Initialize the gameState with a variable for the ship
        gameState = {};
        gameState.shipImage = document.getElementById("shipImage");
        gameState.shipX = 0;
        gameState.shipY = 100;

        // Call animate for the first time, starting the game loop
        animateGame();
    }
    </script>

</body>

</html>
```

***

### Level 2 exercise

1. Copy the example code for the moving ship and save it as an HTML page.

2. Play around with the moving ship. Make it go a different speed or direction.

3. Add a copy of the robot, and animate it. To do this, you should do the following steps:

     - Make an `<img>` tag to hold the robot in the HTML part of the file.

     - The URL for the robot is http://cs.okstate.edu/~clined/levelUp/robot.png

     - Add new variables for the robot to the gameState variable in `window.onload`.

     - Add code to the `drawGame` function to draw the robot.

     - Add code to the `animateGame` function to move the robot.

***

### Level Boss

1. Make the robot bounce off the walls so he goes back and forth or up and down.
