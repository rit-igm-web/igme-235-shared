# Project 3 - Web-based Game or Experience

## I. Overview
*Using PixiJS and/or the Browser DOM, create an Interactive Game or Rich Media "experience"*:

- For this project you are creating a JavaScript-driven game or experience.
- You will be proposing an idea and describing it on a nicely formatted "proposal/about" web page which will include the "game treatment" elements described below: 
- If you would like to see examples of previous projects, take a look back at the [Past Project exploration Exercise from Week 1](https://github.com/dccircuit/IGME-235-Spring-2023/blob/master/exercises/projects.md).

You will use **ONE** (or both) of these technology stacks:
- **JavaScript & PixiJS** (which wraps WebGL): 
    -  [About this PixiJS Tutorial Series](https://github.com/tonethar/IGME-235-Shared/blob/master/tutorial/pixi-js-0.md) has links to the **Circle Blast!** exercise and other demos that can get you started **OR**
- **JavaScript & the Browser DOM** - these exercises will give you an idea of what is possible, and also represent some nice "starter" code:
    - [DOM Adventure!](https://github.com/tonethar/IGME-235-Shared/blob/master/tutorial/HW-adventure.md) is a tile-based game that uses arrow keys for movement, and simple sound.
    - [DOM Chibi Matching](https://github.com/tonethar/IGME-235-Shared/blob/master/tutorial/HW-chibi-matching.md) is a card matching game that uses CSS animations.
    - [DOM Life](https://github.com/tonethar/IGME-235-Shared/blob/master/tutorial/HW-life.md) is a tile-based game that explores simple [cellular automata](https://en.wikipedia.org/wiki/Cellular_automaton).
    - [Magentic Poetry](https://github.com/tonethar/IGME-235-Shared/blob/master/tutorial/HW-magnetic-poetry.md) uses CSS transforms and absolute positioning, and mousemove events.

- **IMPORTANT: YOU MAY NOT USE THE CANVAS 2D DRAWING API FOR THIS PROJECT - DOING SO WILL RESULT IN A GRADE OF ZERO**

- **IMPORTANT: THIS PROJECT NEEDS TO BE _YOUR WORK_:**
    - If you are using *Circle Blast!* or another game we gave you as a template, be sure to "change it up" and go well beyond what we gave you in the start code. Think about changing the game genre, control system, and how the opponents behave. We are only going to give you credit for the code you wrote, so if 90% of your submission is the same as one of our in-class exercises, you are going to get very little credit for the coding and functional sections of the rubric.
    - You must change the fonts, graphics, spritesheets, and sounds from what we gave you in the starting exercises. If you simply reuse what we gave you, points will be deducted in the design and interaction section of the rubric.
    - One reason for the above is that we want you to have a potential portfolio piece that you can show employers, and if your project just looks like the in-class exercises that everyone else is showing them, then you will likely not get the position.


## II. Goal
- Your goal is to use one of the tech stacks above to create an interactive media experience or game that is easy to use, functional, and aesthetically pleasing.

- Ideally the experience will run in all modern browsers, but at a bare minimum it must run in recent versions of Chrome.

- You will be evaluated on:
    - your creativity
    - the quality of the experience you create
    - the soundness of your programming in your chosen tech stack
        - don't miss the requirement to include an ES6 `class` somewhere in your project
    - how far you went beyond what we did in class, as described below

## III. Requirements

### A. Functional
- You will use one of the above tech stacks above as your underlying graphics engine
- Your game or app should do something useful, and be easy to use
- The functionality goes beyond what we have done in similar in-class examples
- There will be no JavaScript errors or exceptions thrown by the app

### B. Design & Interaction
- Pleasing graphic design
- Widgets are well labeled
- User should be able to figure out how to use the app with minimal instruction (and be sure to provide instruction and tooltips if necessary!), and user errors are handled gracefully
- While it doesn't need to be responsive, it should look good on a range of displays; don't design it just to work on your huge screen at home. If a 1024 x 768 display can't show the whole layout, it's a problem

### C. Media
- Images are properly optimized for web delivery - e.g. cropped and scaled to appropriate dimensions, and saved as a JPEG or PNG
- Sound is used to enhance the experience
- you have changed the fonts, graphics, spritesheets, and sounds from what was provided in the in-class examples

### D. HTML/CSS
- Reasonably Valid HTML5 - https://html5.validator.nu/
- Reasonably Valid CSS - https://jigsaw.w3.org/css-validator/
- Most CSS is in an external style sheet
- Use HTML5 semantic and structural elements where practical

### E. Code Conventions
- Utilize at least one ES6 `class` of your own creation
- `let` and `const` (no `var`!)
- `querySelector()` and `querySelectorAll()` for DOM traversal (DO NOT use the older methods)
- D.R.Y. - Don't Repeat Yourself. Repeated blocks of nearly identical code should be factored out and placed in a separate function.
- Separation of Concerns. Similar to how the *Circle Blast!* HW was structured, have a separate .js file for your classes, utility functions, and main code. If you have more than 3 CSS rules, then put them in an external stylesheet
- Variable and function names must begin with a lowercase letter
- Well-commented code. Each and every function gets a comment indicating what it does
- Delete or comment out your `console.log()` calls

## IV. Milestones
- Proposal: Post a simple "proposal/about" web page in your banjo account (under project3/about.html would be a good place) that provides the information described in the next section about what you plan to create for your game. - see myCourses dropbox for submission info & the due date
- Checkpoint: Create a working draft of the project. Post it to you Crit Group channel in our Slack workspace - see myCourses dropbox for the due date
- Final project deliverable is due final exam week - see MyCourses dropbox for the due date and submission instructions. Be sure to post the project to the web, and put the link in the comments field of the myCourses dropbox. 
    - Part of the final deliverable includes a demonstration of your game.  
        1. You should create a short video demo by recording your computer screen while using a tool such as OBS.  http://obsproject.com
 Submit this video by uploading it to YouTube as an unlisted video.  Ideally, you should explain your project with a voice-over, however if you do not wish to do that, you can upload your description as a separate file to the dropbox.
        1. If you have technical issues that prevent you from doing this, you may schedule a Zoom chat with your course instructor to demonstrate your finished project (which they may then record to be able to refer to during grading).

## V. Proposal
We would like you to write a brief game treatment for your Project 3 Proposal:

Here are some elements/sections to include:

You may format this in any way that you want, but break each bulleted item below into a separate paragraph at least.  Feel free to label the paragraphs with headings.

- Give your game/experience a name. It can be changed later. Put it at the top of your page.
- Add a High Concept: A 1-3 sentence description that pitches and summarizes your game.  Examples in link below.
- Genre: Identify the genre(s) the experience belongs to. There are sample lists of genres provided in the link below.
- Platform: Desktop web, mobile web, both, other?
- Story: Is it purely abstract or is there a deeper premise/theme/narrative/motivation?
- Aesthetics: How would you describe the desired graphic style... You might not make it there, but what are you aiming for?
- Gameplay: Discuss what choices the player will be able to make and what kind of control they have to make those choices.  How will the player learn how to play?  
- Mockups: Provide at least 2 mockup screens of the game.  They can be hand-drawn sketches captured on a phone camera, Photoshop mockups, etc.  Use <img> tags and reduce the size of the image so that aren't downloaded at ridiculously high resolutions.  (no more than twice the desired pixel dimensions ont he page).
- Other: Anything else that you like to say, like discuss external libraries you'd like to use, etc.
- About the developer: Give your name/major/minor/year and your skill set/interests.  

Here is a template document of sorts, once used in another class. It contains some extra examples and tips for what we're looking for. You should only really pay attention to the part above the first thick red line:  http://igm.rit.edu/~acjvks/courses/2017-fall/590-ios-game/html/project-1-proposal.html The rest of it was for another assignment specific to that course.

## VI. Documentation
- When you're ready to hand in your document (and actually throughout the development process), add your documentation to the same web page that you created just above for your proposal. Include your process for this project, cite any sources, tell me where to find anything special you want me to see, and also explain how you met the requirements.

## VII. Video Demonstration
During final exam week, you will present your project in a brief (5 to 10 minutes) video demo. Plan to show us:
- What you made. (What is it?  What's the purpose?)
- How it works. (Demonstrate it!  Don't walk through the code.)
- What's cool, and what you think is "above and beyond". (Important!)
- How you overcame any serious challenges.
- Resources utilized (for libraries, tutorials, etc.), if you used any (outside of in-class demos and homeworks, that is).

**There is an alternative if you have technical issues with making your own video as described above in the Milestones section.**

## VIII. Grading

### Your project grade will be split into two parts.
- 1/2 of your overall score will be assessed based on what we can see in the video demo that you provide (the video ITSELF if not worth that much).
- 1/2 of your overall score will be assessed separately based on your required file submission.

### The grading rubrics for each part of this assignment are attached to the
- Project 3 - Final Code Submission
- Project 3 - Video Demo Link 

assignments in myCourses.  

Please review them before you get deep into your project development.
