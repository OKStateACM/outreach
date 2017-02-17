# Putting it all together

We've talked about some big concepts so far. Lets put them all together to
build our own 

* Basic instructions
* Variables
* `if` Statements

## The Basics

A computer is a machine. It is a tool that we can use to do amazing things. But
at its core, a computer is a simple machine. We give a computer **code** and it
works by doing **exactly** what the code says to do. 

**Code** is just a *list of instructions* that tell the computer what to do.
And all a computer *can* do is that list of instructions, nothing else.

## Our situation

There are many different types of programming code, different 'languages',
frameworks, and different types of computers. For instance, your phone is a
computer, but it isn't the same as the desktop's in the lab. 

For our stuff, we will be using **JavaScript** which is a programming language.
(a language is just a way to tell the computer what to do - in other words,
each language has different *instructions*, and different *syntax*)

We've learned about HTML and the basic structure of web pages in level 0, as
well as some basic JavaScript in level 1.

```html
<script>
	// you put JavaScript in between script tags
</script>
```

## Drawing stuff on the canvas

We learned a few instructions to tell the computer to draw things on the canvas
in level 1. We've made a short "cheatsheet" for you so you don't have to
memorize everything. Reference that, and the code we made in level 1 to draw
some things on the screen!

```javascript
// *magic*
var canvas = document.getElementById("myCanvas")
drawing = canvas.getContext("2d")

// now you write something!

drawing.fillStyle = "blue"
drawing.fillRect(0, 0, 10, 10) //these rectangles will be blue
drawing.fillRect(20, 20, 10, 10)
drawing.fillRect(20, 0, 10, 10)
drawing.fillStyle = "red"
drawing.fillRect(10, 30, 20, 20) //this rectangle will be red.
```


### The console

In Chrome, open the "Developer Tools" because we're developers!

`Menu -> More tools -> Developer tools`

and go to the "Console" tab at the top. Here we can tell the computer to do
things, without saving/reloading the page. Try drawing some shapes on the
canvas for a bit and get the hang of it. Notice that the computer always does
*exactly* what you tell it to do, even if that's not what you *wanted* it to
do.

## Variables

After playing around with several instructions, we can't really do much. We
need the computer to keep track of things, like the ship's position or speed.
**variables** allow us to do that. We can think of them as boxes that we can
put things into.

```javascript
var myName // this *instruction* tells the computer to reserve a new box, and name it "myName"
myName = "Alex" // this *instruction* tells the computer to put the word "Alex" into the box labeled "myName"
```

To make sure we understand how these are working, lets look at an example.
We're going to make a new variable, and do a series of *instructions*. At the
end, there will be a *value* inside the variable. Try to figure out what that
value is, we can use the *console*

```javascript
var A_Box = 20
A_Box = (1+3)*2
console.log(A_Box)  // this command will show the *value* in A_Box in the
console
```

```javascript
var number = 20
number = 10
number = number + 5
// what is in the box labeled "number" now??
```

Anywhere in our code that we would type a number, a "string of text", or any
other value, we can instead put a variable. For instance, with our drawing
commands:

```javascript
drawing.fillRect(20, 20, 10, 10)
// or, with a variable
var x = 20
var y = 20
drawing.fillRect(x, y, 10, 10)
```

## Logic and `if` statements

We can use variables now, but unfortunately, we are still stuck with a fixed execution. Our code always does the same thing. Not very interesting. We are going to need to add *logic* to our code.

An `if` statement takes up more than a single line of code, unlike everything else we've seen! Here's the structure of an `if` statement and what it looks like:

```javascript
if ( **some condition that may or may not be true** ) {
	// and here we have more code, inbetween the *{* and *}*
	// like, drawing a rectangle!
	drawing.fillRect(0, 0, 100, 100)
}
```
Here's an example:

```javascript
if ( 1+3 == 4 ){
	console.log("yes");
}
```

Our "condition" was checking whether or not "1+3" was equal to "4", which is
true. So the computer does the code inside the `{}`. Note that we use `==` to
*check* if two things are equal, while we use `=` to *set* things equal with
variables (ex `myvar = 42`). The computer is **very** picky, and it can't tell
the difference.

```javascript
if ( 1+3 == 5 ){
	console.log("This is impossible")
}
```

Walking through this example above: The computer calculates 1+3 (which is 4),
then it check if that number (4) is the same as 5. This is *not* true. In other
words, it is **false**, so it **skips over the entire `{ }` section** unlike
before.
