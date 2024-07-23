# Exercise: Floats & Positioning

It's time to usher in a new era.  What better to use to learn about floating boxes than floating boxes?  

Before you get started, the instructor will give you a preview of the kind of thing we're expecting you to build on the projector.  If you're in an online section or not able to go to the in-person session, be sure to watch the preview video in myCourses.  You don't have to replicate it exactly, but it should give you an idea of what we're looking for.

## Do the following:
**RULE ONE: Don't edit the HTML file! Only edit the linked CSS file (which starts empty)**
1. Download the starter files ([tetris-start.zip](tetris-start.zip)).

1. Add a thin red line underneath all of the sub-headings.
    - use border-bottom property.

1. Float the diagram of all 19 tetromino orientations to the right.
    - what element is it located in?
    - you'll need to add a width to it. (make it 40% of the available width)
    - the image does not have a width.  Set an appropriate one so that it fills the floated element.
        - how do you make so that only images within figure elements get this new width?
    - add some margin so that the text to its left doesn't come right up against the edge.

1. Make is so that the 2nd heading always appears below the floated image.
    - This involves the clear property.  Feel free to apply it to all h2s (along with your red underline)

1. Try floating all of the tetromino divs to the left.
    - remember they won't float until you give them a width.  Try a percentage, try a pixel width, try a number of rems
    - add a visible border to these divs so that you can see what's going on.
    - don't bother fixing up the layout of the individual divs just yet.  We'll do it better with Flexbox in the next exercise.

1. Position the footer.
    1. First, get it away from the Tetromino gallery (if you still have floats going on up there).  Use another clear property.
    2. As a proof of concept, make it appear 500px higher than it normally would.  (this requires position:relative)
    3. Instead of that, make it appear at the very top of the page.  (this requires position:absolute)  It will overlap the other content
    4. Make it stay in the top right corner of the browser window even as the page scrolls. (this requires position:fixed)
    5. Try sending it to a deeper level so that other things scroll over top of it.  (this will require a negative z-index)

## If you feel so inclined, otherwise move on to the next exercise:
- Get your content off of the edges and get your tetromino images to fit within their boxes.

