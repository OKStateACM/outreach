# Level 0: HTML lets you write web pages

###### Note: *This level originally appeared [here](http://cs.okstate.edu/~clined/levelUp/level0.html).*

### What is HTML

HTML is the language used to define web pages. To do this HTML uses two things

- page content, which has the words that will be shown on the page.

- markup tags, which describe how the words will be shown


The markup tags tells things like:

- which parts of the page are headers

- which parts are paragraphs

- which parts should be **bold** or *italic*.

***

### HTML Tags

HTML tags start with the character `<` and end with the character `>`. Most tags come in pairs, and form what is called an **element**. For example, a paragraph begins with the tag `<p>`, and ends with the tag `</p>`.

The close tag for elements starts with a slash: `/`.

A few tags, such as `<hr/>` and `<br/>` end themselves, so they don’t need an extra closing tags, and a few, such as `<img>` do not use a close.

Some common tags:

- `<p></p>` - A paragraph tag

- `<hr/>` - Draw a horizontal line

- `<br/>` - Insert a newline (one vertical space)

- `<h1></h1>` - a heading

- `<center></center>` - Horizontally center the content.

- `<strong></strong>` - show in bold face

- `<img src="imageURL">` - show the image given in imageURL. The “URL” says where to find the image on the web.

- `<a href="pageURL">link text</a>` - a link to another web page, or a location on the same page.

***

### HTML Documents

The code for most HTML documents has four things:

1. They start with the tag `<!DOCTYPE html>`

2. Next, they have an `<html>` element which has everything else inside it.

3. A `<head>` element which gives the page title.

4. A `<body>` element which gives the main content of the page.

Lots of other HTML elements can be inside the `<head>` or `<body>` elements. Here is the code for a very simple HTML page:

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Simple HTML page</title>
</head>

<body>
<p>This is a simple HTML page.</p>
</body>

</html>
```

***

### Editing HTML Documents

HTML documents must be edited in a **text editor**. This is an editor that just shows exactly what you typed. Word processors add hidden codes that you can’t see, so you need a special editor to edit HTML.

***

### Terms

- HTML - the language in which web pages are written.

- Text editor - the kind of editor needed to write code like HTML.

- Markup - this describes how to lay out things on the HTML page.

- HTML tag - HTML markup is made of these.

- HTML element - A open and close tag, and everything in-between.

- URL - The location on the web where something is located.

- Slash character `/` - this is used to close HTML tags.

***

### Level 0 Exercise

- Copy the code from the very simple HTML page to your text editor

- Save it to your drive

- Change the title to have your name

- Add some content such as

    - A header with your name on it.

    - A couple of sentences describing something that happened on the way to school..

    - A link to a site that you like.

    - Some copies of the ship or robot image:

        - Robot: http://cs.okstate.edu/~clined/levelUp/robot.png

        - Ship: http://cs.okstate.edu/~clined/levelUp/ship.png

***

### Bonus Level

If you get done with the Level 0 exercise, you can write a list and a table in your HTML document. Lists are more challenging than, say, paragraphs because they use more than one tag type. To make a list

1. Write the tag for the list type (`<ol>` for ordered list, and `<ul>` for unordered list).

2. Write each of the list items, using `<li>item text</li>`.

3. Finally, close the list using </ol> or </ul>.

Example Ordered List:

```html
<ol>
    <li>Making lists</li>
    <li>is fun!</li>
</ol>
```

Tables are even more challenging than lists since you use four different tags to make them. In HTML, tables are defined as a sequence of rows, and the rows are each defined as a set of cells. To write a table

1. Write the table tag `<table>`

2. For each row in the table

    1. write a `<tr>` to begin the table row

    2. For each cell in the row, add a `<td></td>` element, or use `<th></th>` for header (title) rows

    3. Close the table row with `</tr>`

3. Finally, write a close table tag `</table>`

Example Table:

```html
<table>
    <tr>
        <th>Header 1</th>
        <th>Header 2</th>
    </tr>
    <tr>
        <td>Value 1</td>
        <td>Value 2</td>
    </tr>
</table>
```

***
