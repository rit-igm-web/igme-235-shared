# Exercise: Flexbox

In this exercise, you will again use the starting tetris.html file that you used for the [last exercise](floatposition.md).  However, you will **rename your old css file to something else and instead, start a new css file at the same name as the old one**.

## Do the following:

1. We want this version of the page to respond more to the overall width of the viewport and present a nice experience at multiple widths.  Start by setting a max-width for the figure.  Set the max-width property to never be wider than 650px.
    - After you set the max-width, you'll notice that the image is still quite large.
        - You could try setting overflow: hidden or overflow: scroll as a test. However, it's better to have the image simply fill the available space in the figure container.
        - try applying a width:100% to the img element within the figure element.  Use a contextual selector.
        - Note: You could apply both of these properties directly to the image element if you wanted... Which in some cases would be what you need if you had no surrounding element.
        
2. Try centering the figure.
    - Don't use text-align.
    - Set the left and right margins of the figure to 'auto'.
    
3. Set the header, main, and footer to be 90% of the viewport width, and center them (in the same way as the figure)
    - use a grouped selector
    
4. Okay, everything looks pretty good, but we really have to 
get this gallery of tetrominos under control.  First, what is the parent container for all of the `<div>`s that contain the tetrominos?
    - select that element (use its id if you want) and put a declaration on it to make it a flexbox container.
    
5. They should have all lined up horizontally.  Which we want, but not going wider than the screen.  Instead we want the flexbox items to wrap to new lines.
    - Instead of using both flex-direction and flex-wrap, let's just add a flex-flow property and tell it you want the items to be in a "row" that will "wrap".

6. They now just go down the page because they are all expanding by default to start out at whatever width they want.  Let's decide three things:
    1. Do we want the items to be able to grow wider than what they start out at? (1 for yes, 0 for no)
    2. Do we want the items to become narrower than their starting width? (1 for yes, 0 for no)
    3. How wide do we want them to be, initially? (a measurement with pixel units)
    
7. Select all of the items with the same rule (hint: they are all divs that share a single class) and apply a flex property to it.  For the value put the 3 answers to the above questions in sequence with spaces between.  For example, yes, no, 450 pixels would be declared:  flex: 1 0 450px;
    - While you're at it, throw a border on it so that you can see what's going on.  border: 1px solid black;

8. How did it look?  Here's a thing:  The SVG images appear to push the divs wider than your initial size, so let's get those to be a portion of the containers width...
    Set them to be 60% of their container width.
    - target them with a descendant selector (so you don't change the size of the other image)
    
9. Really make things look better:
    - Sometimes your data isn't in the right container types... Like the spans for the block names.  They'd be better as divs, but since we aren't allowed to change the HTML, add a display property to the spans and make them blocks.  (display:block;)
    - Give them a little margin on the top and bottom.
    - Make them a little larger and bolder.
    - Let's center everything within the tetromino divs using text-align.
    - The alias lists look terrible centered.  Let's make them look like we designed it by left-aligning the text in the alias divs and giving them a margin of about 1em.
    
## If you feel so inclined:
- Notice that two of the tetrominos have an extra class applied.  This would allow you to set the width of the image for the I-Block to be an additional 20% wider and the width of the O-Block to be another 20% narrower than the other blocks.  That will keep the images in their proper relative size.
   
   
## When you finish:
- Make sure you save this version of your exercise.  
    - Upload this flexbox version to banjo (exact URL is up to you).  Make note of the URL, you'll need it in a moment.
    - Make a Zip containing this whole exercise with the css linked to the tetris.html file (and the image files, etc) and include your previous css file (that you renamed) in the same directory (it shouldn't be linked to tetris.html, however).  
    - Submit your Assignment on myCourses... Include both the Zip that you just created as a file upload and make a clickable link to your banjo version in the comment field.
    - *If your instructor requests it* (see your section-specific channel on Slack), submit a link to your finished lab exercise to your section's Slack channel.


    
    
    
    

    
