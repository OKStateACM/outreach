# Drawing commands

* **context.fillRect( left, top, width, height)** - colors in a rectangle with the given shape
	* *left* where the left edge of the rectangle is on the canvas (i.e. the *x* position of the corner)
	* *top* where the top edge of the rectangle is on the canvas (i.e. the *y* position of the corner)
	* *width* the width of the rectangle
	* *height* the height of the rectangle
* **context.strokeRect( left, top, width, height)** - draws an outline of a rectangle with the given shape
	* *left* where the left edge of the rectangle is on the canvas (i.e. the *x* position of the corner)
	* *top* where the top edge of the rectangle is on the canvas (i.e. the *y* position of the corner)
	* *width* the width of the rectangle
	* *height* the height of the rectangle
* **context.fillStyle = "red"** - sets the color for following drawing commands
	* the color can be a color like "red"/"blue"/"green", but that only works for *some* colors, not *every color*
	* for other colors, we need to use "hex codes". We can use [http://www.color-hex.com/color-wheel/](http://www.color-hex.com/color-wheel/) to find these 'hex values' for any color we want
* **context.drawImage( image, x, y )** - draw an image on the canvas
	* *image* - an image that you loaded earlier (ex `var robot=document.getElementById("robotImage")` )
	* *x* - the horizontal position on the canvas to draw the image
	* *y* - the vertical position on the canvas to draw the image
* **var image = document.getElementById( imageId )** - load an image from the page to use later, and store it in a *variable* 
	* *imageId* - the "id" tag of the image on your HTML page
	* ex `var robot=document.getElementById("robotImage")` 
