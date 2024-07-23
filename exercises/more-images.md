# Exercise: Adding More Images 

We've got some specialized images for you to add to your Dig Dug page.  An SVG image and a file to use as a favicon!  

## Do the following:

1. Download this SVG image: [dig-dug.svg](dig-dug.svg). (use the "raw" button to get to the "code" of the image -- which may display as the image itself in your browser -- in which case you can use right-click > save as... to save a copy)

1. View it in your browser quickly to see what it looks like.  Notice how it resizes smoothly at all sizes.

1. Open the file in VS Code.  Turn Word-wrap on.  (It's in the View menu).  Notice the style element near the top with several style rules, all of which have a color in hexadecimal code.  Go ahead and edit this file to figure out which one changes the outer color in the logo.  Change it to something else (maybe "teal"). 
   - Note that hexadecimal colors start with the # symbol.  If you want to use a named color, remove the #.
  
1. Save your edited file.

1. Add it to the page.  
   - You could choose to copy and paste the whole `<svg>` element from the file and paste it where you want it in the HTML file.
   - You could add it through a simple `<img>` element.
   - You could add it as an `<object>` with an `<img>` fallback inside. If you would like to replace the old logo at the top of the page with this new SVG version for browsers that can support it, then this is the best solution.
  
1. Time to make a favicon.  Grab this PNG image: [taizo_hori.png](taizo_hori.png).  Looks perfect to become a favicon, right?

1. Use the website: http://favicomatic.com to create the necessary files and code.
    - This failed for me in recent testing, so if you can't get it to work, yourself, you can download this simple result zip file from a previous attempt: [favicomatic.zip](favicomatic.zip) 
    - If the above site fails to work, you can use this site as an alternative: https://www.favicon-generator.org

1. Add the generated link tags to the head of your page so that the favicon loads.


## If you are so inclined, otherwise, continue to the next exercise.

- Validate.
- Look for at a site like http://thenounproject.com and see if you can find a cool icon to use for your own 235 Home Page.  Maybe something that represents you.  Then, download it as an SVG.
    - Other sites:  http://flaticon.com, http://freepik.com, https://www.iconfinder.com/, etc.
    



