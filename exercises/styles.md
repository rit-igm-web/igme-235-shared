# Exercise: Starting Styles

We're really moving on to the Presentation layer and learning how to properly add styles to our pages.  

## Do the following:

1. Get your Dig Dug page loaded up.

1. We briefly added an inline rule to your body tag during the previous exercise.  Remove that inline rule and add it to your embedded style sheet instead.
    - Hint: Use an element selector for the `<body>` tag.

1. Confirm that it works.

1. Set a style for the `<h2>` tags (a new embedded rule) & test.
    - Make them another color, but not underlined like the `<h1>`.
    - If you don't have any `<h2>` tags, you should add them to the sections within rather than making all of them be `<h1>`s.
    
1. Were you previously tempted to use `<blockquote>` to indent things from the left?  That's a bad practice because the things you are trying to indent are semantically not quotes (except for one of them).  Instead, try using the **p** element selector and applying the declaration: `margin-left: 100px;`
    - You can also apply that to your `<h2>` elements if you prefer that they moved over with the rest of the text... Or maybe something in-between?  You decide.

1. Select an image or two that you'd like to have floating against the right side of your screen.  Then add the same `class` to all of them.  Something like **side** or **over** would be a good class name.

1. Add one more style rule that would apply to all of the images and cause them to float to the right.
    - I'll go ahead and give it to you.  `img.side {float:right; margin: 0 12px;}` is what you'd use if you used the class name **side**.

## If you are so inclined, otherwise, move on:
- The book doesn't cover it for real until the end of Chapter 13, but I think you should be able to move your embedded styles into an external style sheet very easily now.  Just copy and paste them into a new empty text file with a .css extension and then add a `<link>` element into your head section that points at the file.  Here's an example of what that would look like:
    - `<link rel="stylesheet" href="styles/mycssfile.css">` assuming you put your .css file into a subfolder called **styles** -- not that you have to, but it's a common practice.



