# Exercise: Tetris Grid

This exercise is a little more step-by-step than past exercises... We provide you with more code to copy and paste than usual, but you still need to know about CSS Grid and an assortment of topics from Chapters 18 and 19.

We want you to complete this particular exercise and **submit it to the appropriate Assignment item in myCourses when you're done**. 

Start with downloading the starter files located here:  [Tetris Grid Starter Files](tetris-grid-start-files.zip)

## Part One - Normalize your CSS with "Bootstrap Reboot"

1. Look over your starter files, open the *directory* in VS Code (right click the folder or inside of it, and -- if it's a choice -- choose Open with Code... if not, use the open folder command from within VS Code), and preview the tetris-grid.html in your browser (probably by launching it with Live Server). If you haven't done this before... Figure it out now... Install the LiveServer extension (if it isn't already) and then right-click the file and choose "Open with LiveServer".  If Edge comes up, abort!  You can either change your default browser in windows setting or go into the Settings of VS Code and specify Chrome:  Like so: Ctrl-, (control-comma), Type liveserver in the search box and look for "Custom Browser" with a dropdown menu.  Pheww!

2. Recall from the reading (Chapter 19) that there are two ways main ways to achieve a "clean slate" in your HTML so that your design can look the same on all browsers despite the potentially different "user agent style sheets":  
    - CSS reset (which overrides and essentially 'zeros out' all style rules... basically starting you out from square one).
    - Normalize.css (which painstakingly adjusts every modern browsers default styles to make them consistent).  

    However, in the 2nd week, we've already brought up one other style sheet that BUILDS on Normalize, and that's Bootstrap Reboot.  Here's your chance to compare all three:

3. We've already downloaded and added all three to your CSS directory.  They are ready to link to your starter code... Just uncomment each one one-at-a-time and compare what they do to your starting page.  Let's select "Bootstrap Reboot" to keep using it for the rest of the exercise.

4. You should probably apply a little margin to the `<body>` tag.  Maybe 1rem?  Nobody likes words bumping up against the edge of something else.  But don't add your new CSS to the bootstrap-reboot.css... Add them to your *own* CSS file.  We've already set it up for you: css/gridstyles.css. It starts out pretty empty!

## Part Two - Apply a Layout Grid

Here's the plan (imagine these as a sketch): 

```
Mobile:				Wider:

logo				logo		intro
menu				menu		menu
intro				playground 	playground
playground			footer 		footer
footer
```

The playground section will be another grid container of it's own (but we won't add it right away).

1. On Mobile, everything will just stack up in a single column.

1. Start by turning the `<div>` with the id of "wrapper" into a css grid container.  You should know how to do this with a display property.  Don't forget, you should be working in gridstyles.css from here on out.

1. In the source code, the intro section comes first.  (better for screen readers), but when we view it on a mobile device, we want it to appear below the menu.  So, we'll specify the order that we want the 5 grid areas to appear in using the grid-template-areas property (you can copy and paste -- you figure out where to put it):
    ``` 
     grid-template-areas:
        "logo" 
        "menu" 
        "intro" 
        "playground" 
        "footer";
    ```
1. That alone, doesn't do much... It just gives names to areas.  Copy and paste the following CSS to put all of the key elements into the right areas according to our plan:
    ```
    h1.game { grid-area: logo; }
    ul.menu { grid-area: menu; }
    #introduction { grid-area: intro; }
    #tetgrid { grid-area: playground; }
    footer { grid-area: footer; }
    ```		

1. Does it appear in the right order, now?  

1. Add some extra intro text with the 'lorem' emmet shortcut in VS code:  Put your cursor after "Info about this page. " and then type `lorem100` (it works better if you actually type than cutting and pasting) and press return.  Done.		

1. For the wider layout, we will change the grid-template-areas value to specify a layout like this:  (Where would you put this rule so that soon, we can put it in it's own media-query? -- which you'll do in the step after next)
    ```
    grid-template-areas:
        "logo       intro"
        "menu       menu"
        "playground playground"
        "footer     footer";
    ```

1. A preview will show you that the proportions are off at the top.  We need to save room for a logo that is **500pixels wide and 345px high**. Write a grid-template-columns rule and a grid-template-rows rule that gives room for a logo. The other column can be 1fr wide and the other rows can be whatever the browser likes (ie: auto).

1. Finally, surround these new declarations for wider screens with a media query that triggers on Media Type "screen" and Media Feature Query "min-width:850px".  

## Part Three - Use Image Replacement to add the Tetris Logo

In Chapter 19, you also read about "Image Replacement Techniques"... Right now we have an h1 tag that contains the name of our game, but we have a nice Tetris Logo png file that we'd prefer to have replace the word "Tetris" for most users.  We don't want to just use an image with an alt tag here because we like the semantic meaning of an important `<h1>` tag at the top of the page.

1. So the book gives the following example code:

    ```
    <h1 id="logo">Jenware</h1>

    Style rule:
    #logo {
      width: 450px;
      height: 80px;
      background: url(jenware.png) no-repeat;
      text-indent: -9999px;
    }
    ```

1. Use this same technique to match your image's width & height, link to its proper location (!) in the images subfolder (note, your relative link is starting from the css subdirectory so you'll need a different relative path), and set a big negative text-indent to push the word "Tetris" off the screen.

1. Now that the logo is there, the introduction text could use a little space around it.  Applying a 2rem margin all the way around the introduction `<section>` will help with that. 

## Part Four - Create a Drop-down menu with Flexbox and standard CSS

So we have a bulleted list that we want to make into a menu.  Let's do it quickly so we can get to the last part before we all get old.

1. Add this code first & test.

```
ul.menu {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
}
```
2. Okay, that's less like a bulleted list.  Let's change the way the link tags work by making them into block elements!

```
.menu a {
    display: block;
    background: gray;
    padding: 10px;
    color: white;
    text-decoration: none;
}
```
3. Make them a little wider:
```
.menu li {
    width: 25%;
}
```
4. Let's get some nice rollover effects:
```
.menu a:hover {
	background: red;
	color: yellow;
}
```
5. They could be a little small on a mobile screen, so let's make the buttons full-width on mobile.

Add flex-wrap: wrap; to the ul.menu rule. 

and

Add the following media query after your other ".menu li" rule:

```
@media screen and (max-width: 550px) {
	.menu li {
		width: 100%;
	}
}
```
6. Two more cool things:

Make a sub-menu:

1. put your cursor between the `</a>` at the end of the Official Tetris site link and before the `</li>` that ends that list item. and hit enter to make some space.

2. In the blank space type the following emmet abbreviation (watch as the preview grows) and then hit enter:  
	`ul.menu>(li>a:link{Link $})*3`  
		(you could also copy/paste and then hit ctrl-space then enter).
	
Immediately after, the cursor will put itself at the first href value so you can type a domain. ie: google.com then hit tab and type another.  Just throw some URLs in there.

3. Copy and paste this to make the new submenu resize and hide/show on rollover.

```
ul.menu ul li {
    width:100%;
}
ul.menu ul {
    display:none;
}
ul.menu li:hover ul {
    display:flex;
}
```
4. Two other nice touches:

add a "submenu" class to the li tag of the Official Site menu item.

Add this css!

```
.menu .submenu li>a:hover {
    background:red;
    color:yellow;
}
.menu .submenu>a:after {
    content: "+";
    padding-left:5px;
}
```
Okay, that's enough of that... It's one of many ways to build menus and style them.  This one has a down-side of pushing content down the page on rollover, but it could probably be improved.

## Part Five - Create an Interactive Tetris Playground Grid.

Okay, last part!

Let's build a new Grid with a 6x6 layout.  

*Note, this is not responsive.  It would take a different approach with the image files and we just haven't had a chance to re-write the execise yet... If you feel so inclined, feel free to submit an alternative version of this assignment with a responsive playground grid.  Bring it to your instructors attention directly and we may award some bonus credit!*

You might want to do this part with Firefox so that you can use its awesome grid inspector tools.  Just copy the Live Server URL to your page out of the Chrome location box and paste it into Firefox's... the same JavaScript will watch for changes to the file and reload when it is modified.  Then, when you use the inspector on an area that's a grid container, there will be a small grid button in the HTML that you can click on to display the grid inspector.

1. Anyway:  Just add this code to get a 6x6 grid.
    ```
    #tetgrid {
        display: grid;
        grid-template-columns: repeat(6, 100px);
        grid-template-rows: repeat(6, 100px);
    }
    ```
    Easy, right?  See what the tetromino pieces do?

    Interestingly, the default size of each square in the tetromino SVGs happens to be 100 pixels.

    Notice how they all pile up, one to each grid cell and over-lap each other?  That's because the "overflow" of all of these divs is set to visible.  

1. Test this rule real quick:
    ```
    div.tet {
        overflow: hidden
    }
    ```
    Not as fun, right?  Why does one block look empty?

1. Set that back... either delete the rule or set the overflow: visible;

1. Let's move our tetrominos around.  Let's take the "O" block and put it in the top left corner.  Try this code:
    ```
    #o {
        grid-column: 1/3;
        grid-row: 1/span 2;
    }
    ```
    These are two different ways of specifying to make something go across two columns or rows... The first one specifies a starting line and and ending line (recall that grid tracks are not numbered.  The lines BETWEEN them are).  The second specifies a starting line and a number of rows to span across.

    Notice that the other tetrominos are filling in around the O-block now.

1. Let's put the "I" block next to the "O" block.
    ```
    #i {
        grid-column: 3/-1;
        grid-row: span 1;
    }
    ```
    What does that -1 mean?  Recall that grid lines are numbered from both the start (going further positive) and the end (going further negative)

    Also, since when do tetris blocks fill in from the top?  Since now. Deal with it.   :-)

    Okay, I want to rotate a block.

1. Let's try our first CSS Transform on the red "Z" block:
    ```
    #z img {
        transform: rotate(90deg);
    }
    ```
    It's rotating, but not quite around the right spot... It's rotating around it's own center point.

    I'd prefer to rotate around the top left corner & then shift the whole image about 200 pixels to the right.

1. First, this style rule will change what part of the image is anchored during rotation:

    `transform-origin: 0 0;`

    Change the transform rule to this:  `transform:  translateX(205px) rotate(90deg);`

    The order is important... Compare it to:  `transform:  rotate(90deg) translateX(205px);`

    Okay, Grid is great for situations where you want things to overlap!  Now we want the red Z to overlap the corner of the yellow "O" block.

1. Use grid-column and grid-row like we did for the "o" and "i" blocks to put the "z" block into position:
    ```
    #z {
        grid-column: 2/span 2;
        grid-row: 2/span 3;
    }
    ```
    Okay, your challenge is to put all of the other blocks in position on the grid so that none of them are overlapping each other... The cells can overlap, but the tetromino images can not (except for the black edges).

    ***Before you go off doing that***, there's one more thing that we want you to do.  We want you to see how CSS transitions work.  They let you 'tween' between two states of some property of your HTML element... Could be many things from color, to width, to transform!

    Let's put a transition on the tetris blocks so we can make them rotate under our cursor!

1. Start by telling all images on the page that if their rotation ever changes, that it should change over a 1 second duration:
    ```
    img {
        transition-property: transform;
        transition-duration: 2s;
    }
    ```
    Alone that won't do anything.

    but couple it with this hover rule:
    ```
    img:hover {
        transform: rotate(-90deg);
    }
    ```
    And boy, howdy, do we have an interesting playground, amirite?
    
    *Note, this won't work perfectly for all blocks.  This is another challenge for you to work out a way to make all blocks rotate.  Bring this to the instructors attention if you do it, but this one isn't worth extra credit)*

1. Let's add one more interesting interface element:
    Back to your rollover navigation menu:

    Add:     `transform:scale(1.1);`   to the .menu's "a:hover" state.

    Add:    `transition: transform 0.1s ease-in;`  to the .menu's regular "a" element.

    Try it... Pops out a bit, huh?  But the color change is sudden.  How about adding 
    " `, background-color 0.5s linear;` to that same transition declaration.

    Interesting, right?  Well, that's enough for now.  

1. Submit your finished version of this (with no overlapping tetrominos) to the assignment folder.
