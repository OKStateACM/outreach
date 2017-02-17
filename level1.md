# Level 1: You can animate things by redrawing the canvas

###### Note: *This level originally appeared [here](http://cs.okstate.edu/~clined/levelUp/level1.html).*

### HTML Canvas

The HTML Canvas element is a special element that allows you to draw on it. You do this by writing drawing commands in the **JavaScript** language. Some of the commands can draw rectangles, circles, text, or images.

JavaScript commands are written on your HTML page inside a `<script>` element, so really, what we are doing is writing a JavaScript program to draw a picture.

Let’s look at an example of making a page with a canvas element and drawing a few things on it.

```html
<!DOCTYPE html>
<html>
<title>Page With Canvas</title>
<body>

<h1>This page shows a canvas element</h1>
<canvas id="myCanvas" width="600" height="400"></canvas>

<img id="shipImage" style="display:none;"
    src="http://cs.okstate.edu/~clined/levelUp/ship.png"></img>

<img id="robotImage" style="display:none;"
    src="http://cs.okstate.edu/~clined/levelUp/robot.png"></img>

<script>
// This part is the JavaScript code that will draw on the canvas
// Lines that start with // are called comments. They are ignored
// by the computer, but are there to help you understand what
// is going on.

// The window.onload function will run when the page first loads
window.onload = function()
{
    // First, Get a reference to the canvas, looking it up by name
    var canvas = document.getElementById("myCanvas");

    // Next, get a 2d "graphics context" for the canvas.
    var drawing = canvas.getContext("2d");

    // Draw a background rectangle
    drawing.fillStyle = "#BBBBFF";    // light blue fill color
    drawing.fillRect(0,0,600,400);    // fill the canvas with light blue
    drawing.strokeRect(0,0,600,400);  // draw a black border

    // Finally, we can draw the circle
    drawing.fillStyle = "#00FF00";        // green fill color
    drawing.beginPath();                  // start the shape of the path
    drawing.arc(300,200,80,0,2*Math.PI);  // the drawing path is a circle
    drawing.fill();                       // fill the path with red
    drawing.stroke();                     // draw a black border

    // Get the ship image and draw it
    var shipImage = document.getElementById("shipImage");
    drawing.drawImage(shipImage, 0, 100);

    // Get the robot image and draw it
    var robotImage = document.getElementById("robotImage");
    drawing.drawImage(robotImage, 450, 100);
}
</script>

</body>
</html>
```

***

### The HTML part

The page code above is quite a lot to take in at once, so let’s break it down piece by piece.

The first part defines an HTML page. It defines the page layout, in other words, what things will be on the page and where they will go. This is pretty much what you have seen before, except that we have added a new type of element called a “canvas”.

Besides the canvas, there are two images that are not displayed. These will be used later to draw on the canvas.

```html
<!DOCTYPE html>
<html>
<title>Page With Canvas</title>
<body>

<h1>This page shows a canvas element</h1>
<canvas id="myCanvas" width="600" height="400"></canvas>

<img id="shipImage" style="display:none;"
    src="http://cs.okstate.edu/~clined/levelUp/ship.png"></img>

<img id="robotImage" style="display:none;"
    src="http://cs.okstate.edu/~clined/levelUp/robot.png"></img>
```

### The JavaScript part

After the HTML part of the page, the JavaScript code is given in a `<script>` element. Everything in-between `<script>` and `</script>` is written in JavaScript instead of HTML. This means that the rules about what kinds of things you can put in the script element (syntax) are different from the rules you use when you write the rest of the HTML document. So really, you are writing in two different languages!

HTML is a layout language, but JavaScript is a real programming language. Think of the commands in JavaScript as being executed one at a time from top to bottom, unless something in the code changes that order.

***

### window.onload

At the beginning of the script, there are a bunch of lines that start with `//`. These lines are called “comments”. The computer ignores them, but they are written to help you understand what the code is doing. After that is the line:

```javascript
window.onload = function()
```
This line tells the system that the code inside the curly braces `{}` should run when the page has loaded. Think of this as the starting point for our JavaScript program.

By putting our code in the onload function, we can make sure that it runs after the page has loaded all of the images that it will use.

***

### The Graphics Context

The goal of our JavaScript program is to create a drawing on the canvas. In order to do this, the program needs a “graphics context” for the canvas.

You can think of the canvas as a piece of paper. A graphics context is sort of like deciding which piece of paper you want to draw on. When the code draws to the graphics context of the canvas, the drawing will show up on it. To get this context, first, we get a reference to the canvas itself, and then get its graphics context in the following lines:

```javascript
// First, Get a reference to the canvas, looking it up by name
var canvas = document.getElementById("myCanvas");

// Next, get a 2D "graphics context" for the canvas.
var drawing = canvas.getContext("2d");
```

***

### Clearing the canvas by drawing a rectangle

After getting the graphics context, the code can actually draw something. The first thing that it does is to fill (color in) a rectangle covering the whole canvas. Then, it draws a border around the whole canvas using the strokeRect command.

```javascript
// Draw a background rectangle
drawing.fillStyle = "#BBBBFF";    // light blue fill color
drawing.fillRect(0, 0, 600, 400);    // fill the canvas with light blue
drawing.strokeRect(0,0,600,400);  // draw a black border
```

***

### Hex Colors

You may have noticed that it said the color for the rectangle was light blue. But how do we get light blue out of “#BBBBFF”?

In JavaScript you can create colors using **hexadecimal** notation (or just hex for short). Hexadecimal is a numbering system that has 16 digits rather than the 10 that you are used to. The digits are given as 0123456789ABCDEF. In this scheme, A means 10, and F means 15.

To make a color, you start with a *#* sign, and then use two hex digits to indicate how much red, green, and blue you want in the color. 00 means that you don’t want any of that color, 88 means that you want about half of that color, and FF means that you want as much as possible.

With the hex system you can literally specify millions of different colors. Here are some example colors given in hex format:

```html
<p style="color:#000000">black</p>
<p style="color:#FF0000">red</p>
<p style="color:#00FF00">green</p>
<p style="color:#0000FF">blue</p>
<p style="color:#FFFF00">yellow</p>
<p style="color:#888888">gray</p>
<p style="color:#FF8800">orange</p>
```

What hex values would you use to make a purple color?

***

### Pixel coordinates

In order to draw a rectangle, we have to tell the computer where it should be on the canvas. We use **pixel coordinates** to do this. For the canvas, coordinates are two numbers that tell the computer where a point is located. The coordinates (0,0) are the top left corner of the canvas, and (600,400) is the bottom right of the canvas.

The point (0,0) is sometimes called the **origin**. The first coordinate is often called the “x” coordinate, and the second coordinate is called the “y” coordinate.

To make a rectangle, we have to give the computer two coordinates, which ends up being four numbers. Since the canvas is defined to be 600 pixels wide and 400 pixels high on our page, the line of code below fills the entire canvas with the current fill color:

```javascript
drawing.fillRect(0,0, 600,400);
```

***

### Drawing a circle

The next thing that the program does is to fill in and outline a circle. This is a little complicated, and we have to do a bunch of steps to make it happen.

The first thing we do is set the fill color to green “#00FF00”. Then, we begin a path and draw an “arc” that goes all the way around a circle. Finally, we fill the circle path and stroke the path to outline it in black.

```javascript
// Finally, we can draw the circle
drawing.fillStyle = "#00FF00";        // green fill color
drawing.beginPath();                  // start the shape of the path
drawing.arc(300,200,80,0,2*Math.PI);  // the drawing path is a circle
drawing.fill();                       // fill the path with red
drawing.stroke();                     // draw a black border
```

***

### Drawing images

The final thing that the program does is to draw a couple of images. The way we get the images is to first include them as image tags on the page that are set to have a `“display:none”` style. We also give the images an `id` property so that the JavaScript code can find them later. This happens in the HTML part of the page:

```html
<img id="shipImage" style="display:none;"
    src="http://cs.okstate.edu/~clined/levelUp/ship.png">
```

In the JavaScript code, it then gets a reference to the images and draws them at different locations on the canvas. The two numbers that are given are the pixel coordinates of the top left corner of the images.

```javascript
// Get the ship image and draw it
var shipImage = document.getElementById("shipImage");
drawing.drawImage(shipImage, 0, 100);

// Get the robot image and draw it
var robotImage = document.getElementById("robotImage");
drawing.drawImage(robotImage, 450, 100);
```

***

### Errors and Debugging

Programming languages like HTML and JavaScript are not very smart. Tiny errors throw them off. If things are misspelled, or even mis-capitalized, they don’t understand what you mean.

For example, this line of code draws the robot image on the canvas:

```javascript
drawing.drawImage(robotImage, 450, 100);
```

But this line of code is an error and breaks the program:

```javascript
drawing.drawImage(robotImage 450, 100);
```

One helpful thing that some browsers include is called the “web console”. It shows errors that happen in your JavaScript code. Each browser handles the web console a bit differently. Here is how to open it on some of the major browsers:

- Google Chrome

    - Three dots menu on top right -> More tools -> Developer tools

- Firefox

    - Three bars menu on top right -> Developer -> Web console

- Internet Explorer

    - Gear menu -> F12 Developer Tools -> script tab

- Safari

    - (Mac) Develop menu -> show error console

***

### Terms

- Canvas Element - An HTML element where you can draw things.

- `<script>` tag - Where you place your JavaScript code.

- JavaScript - A programming language that can be used to make your web page interactive.

- `style=display:none` - Tells the page not to display an image or other element.

- `window.onload = function()` - The starting point for the JavaScript program.

- `document.getElementById()` - gets a reference to an HTML element using the id.

- Graphics context - tells what canvas we will draw to.

- Hex colors - using hexadecimal notation to define a color. For example #0000FF is blue.

- Pixel coordinates - Two numbers that tell the computer where to draw things. For example (0,0) is the top left of the canvas.

- Bug - An error in the program.

- Syntax error - Code that does not follow the rules of the language.

- Web console - A display in the browser that will show syntax errors.

***

### Level 1 Exercise

1. Copy the page at the top of the assignment. Save the page, and then open it in a web browser. Also, open the web console.

2. Change the page to add your own content, such as your name at the top.

3. Change the canvas size and make your own drawing. The drawing could be of something like a face using lots of circles and rectangles to do the drawing. Each time you make a change, you should save the file and press refresh on the browser to reload the page.

4. You may want to use a piece of paper or the whiteboard to help you plan out the drawing. Think of the drawing space as having a grid on it with coordinates, where (0,0) is the top left corner of the drawing. Then, if your canvas is w pixels wide and h pixels high, (w,h) will be the lower right corner.

***

### Bonus Level

1. Make a second page with a canvas, and draw a grid of images on a canvas. To do this, you will have to figure out the coordinates of each image. Remember that a coordinate has two values, one for the horizontal position (x), and one for the vertical position (y). Remember that the URLs for the robot and ship image are:

    - Robot: http://cs.okstate.edu/~clined/levelUp/robot.png

    - Ship: http://cs.okstate.edu/~clined/levelUp/ship.png
