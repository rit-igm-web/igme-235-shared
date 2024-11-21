# Project 2 - Web Service Application

## I. Overview

For this project you are creating a JavaScript driven Web application that utilizes a Web service.
- Your goal is to create an application that is easy to use, functional, and aesthetically pleasing.
- Ideally the experience will run in all modern browsers, but at a bare minimum it must run in recent versions of Chrome.
- The objective of this project is for you to demonstrate your mastery of HTML5/CSS/JS programming in a [web browser DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction) context. 
- You will be evaluated on:
    - how well you met the requirements of the assignment.
    - the quality of the experience you create.
    - the soundness of your programming.
    
- Resources:
    - Our entire Web apps series: [Web Apps 0 - About this Web App Tutorial Series](../tutorial/web-apps-0.md)
   - This HW pulls together most of what you need to know into a working example -> [GIF Finder HW](../tutorial/HW-gif-finder-lab.md) 
   - Here are some working web service examples for you to look at - you can use any of these APIs in your project: [web-service-app-starters.md](../tutorial/web-service-app-starters.md)
   - https://developer.mozilla.org/en-US/docs/Web/JavaScript

## II. Requirements

### A. Functional
1. You have three options for selecting a Web API for this project.
- Continue to use the GIPHY API and deliver a GREATLY improved version of GIF Finder.
- Use one of a specified set of APIs and create a similar experience to GIF Finder that meets the requirments.
- Select another API of your choice that you can provide a proof-of-concept for by the Proposal due-date.

#### GIPHY Option
- You may choose to use GIPHY for this project, however you must do the following things.
  - Completely re-vamp the user interface.  There should be no elements from the original interface (images, layout, buttons, phrasing, etc) still in use in your new implementation.  
  - Add much more functionality.  At a minimum:
    - Sign up for your own GIPHY API key.
    - Implement a "Searching..." spinner or other progress graphic.
    - Add a way to "Get More" results with "next/previous" functionality.
    - At least 2 other new features. for example:
      - Keep a list of recent searches.
      - Find popular/trending GIFs.
      - Allow the user to "favorite" images and then retrieve them later.
      - Give the user a "Copy" link that copies the URL of the GIF to their clipboard.
    
#### Specified API Option (NOW MORE OPTIONS!)
- You may get familiar with and use one of the APIs from this list:
  - Because APIs change from time to time this is not a guarantee that these APIs will be smooth sailing, but they have been shown to work.
    - Dog API*: https://dog.ceo/dog-api/
    - Jikan Unofficial MyAnimeList API*: https://jikan.docs.apiary.io/
    - The Amiibo API*: http://www.amiiboapi.com
        - *Starters for the above 3 APIs can be found in the [web-service-app-starters.md](https://github.com/tonethar/IGME-235-Shared/blob/master/tutorial/web-service-app-starters.md)
    - REST Countries: https://restcountries.com/  
    **Recent additions to the list:**
    - Pokémon TCG API: https://docs.pokemontcg.io/
    - Pokemon API: https://pokeapi.co/docs/v2
    - Rick and Morty API (REST version): https://rickandmortyapi.com/documentation
    - Scryfall Magic: The Gathering Search: https://scryfall.com/docs/api
    - Open Trivia DB API: https://opentdb.com/api_config.php
    - Mixcloud (This is a little more complicated): https://www.mixcloud.com/developers/
    
  - You can make pretty much any experience you like as long as it captures a user request, gets data from the API, and then presents it back in a way that is useful or fun, easy to understand, and fairly well organized. 
        
#### Choose Your Own API Option
- This choice is for the more adventurous students who want to try to go beyond the well-trodden paths and look for an alternative API that appeals to them.
- But if you wish to make this choice, you must be able to prove that you can access the API by the due date of the PROPOSAL.
- You must also be able to keep your project to a reasonable scope that is roughly equivalent to the other assignments.
- There are API lists that you can peruse, however there are a couple of guidelines.
  - Look for an API that supports *CORS* (Cross-origin resource sharing) - if the API says **NO** in the **CORS** column then it will **NOT work** well for this project
    - **DO NOT** use any API that requires *OAuth* authentication
    - if an API requires an API Key, be sure that there is a "free tier", and that the API does not have a short trial period
    - Here are a couple of lists to check out:
      - https://github.com/toddmotto/public-apis <- Includes CORS column.
      - https://github.com/abhishekbanthia/Public-APIs <- Less info about each API.
    - **Important note:** Most of the "sports score" APIs have strict rate limits and/or short trial periods. In the past, most students attempting to use these APIs on their projects ended up having to change their project idea to something else at the last minute. Use such APIs at your own risk.

### A. Functional - continued.
2. You will save the last term searched by the user in the browser local storage - this was covered here: [Web Apps 9 - WebStorage API](https://github.com/tonethar/IGME-235-Shared/blob/master/tutorial/web-apps-9.md):
    - we are going to test this capability by typing in a search term, doing a search, and then closing the browser window. When we re-open the window, the user's last search term should still be in the field.
    - ideally this will also be true of the other controls, but we won't require it.
    - if there isn't a 'search term' to save in your project, then save something else and be sure to document what is saved from visit to visit.

3. Required controls - there will be a MINIMUM of 3 controls that a user can use to filter and display the results. Search buttons or similar don't count towards the 3 controls. For example, GIF Finder has these controls:
    - a search button (which doesn't count)
    - a search term field (&lt;input>) that the user types into
    - a pulldown (&lt;select>) that the user can use to limit the number of results

  -  **So you will need at least one additional kind of control. What kind of control to use depends on what parameters the web service will allow you to search it on. Here are some ideas:**
  
     - a **rating** pulldown - if we had this on the GIPHY HW then a user would be able to choose between viewing "G" and "PG" videos for example
     - a **sort by** pulldown to allow the user to view the results sorted A->Z, Z->A, by date, etc 
     - a **date** chooser to filter the results by date - jQuery has a Datepicker Widget that would help with this -> https://jqueryui.com/datepicker/
     - **next** and **previous** buttons - another really nice option is to allow the user to "page" through large numbers of results. In the GIPHY HW did you notice that we always get the same 100 "cat" GIFs back when we search?
       - This is because there are ***thousands*** of cat GIFs on GIPHY, and if we don't otherwise specify we will always get them returned from the web service starting at index 0, which means we always get the first 100 (index 0-99) back.
       - We can instead write code that requests a higher starting index.
       - In the GIPHY API this can be done by tracking and adding an `offset` value to the query string that is sent over to the API.

4. Finally, there will be no JavaScript errors or exceptions thrown by the app.

### B. Design & Interaction
- Pleasing graphic design:
  - with a custom interface coded in HTML/CSS, by you
  - this interface does not closely resemble the GIPHY homework's UI
- Widgets are well labeled and follow interface conventions, for example:
  - radio buttons are for mutually exclusive options, checkboxes are for when you want to let the user choose *multiple* options - https://www.nngroup.com/articles/checkboxes-vs-radio-buttons/
  
- Users should be able to figure out how to use the app with minimal instruction:
  - be sure to provide instruction and tooltips if necessary
- User errors must be handled gracefully:
  - for example, if the user forgets to type in a search term before clicking the Search button, the app should tell the user something like "Please enter a search term first"
- Users must know what *state* the app is in at all times:
  - for example, when they click the search button, there should some indication that a search is happening:
    - text that says "Searching for 'Tacos' near you" and so on
    - a "spinner" or other "indeterminate progress" animation - [Google search "indeterminate progress"](https://www.google.com/search?q=indeterminate+progress&client=safari&rls=en&source=lnms&tbm=isch&sa=X&ved=0ahUKEwj-sNCal4neAhVr34MKHWKqA98Q_AUIDigB&biw=1036&bih=583)
    - An HTML 5 Progress element is also available: https://css-tricks.com/html5-progress-element/
- While the app doesn't need to be fully responsive, it should look good on a range of displays. For example, don't design it just to work on your huge 24" screen at home (as we'll be grading it on a laptop with a much smaller screen). The main controls of the application must fit in a 1080px wide x 800px height window.
- You are encouraged to use CSS Flexbox and/or Grid for this project.  However, you MAY use a CSS framework such as Bootstrap, Skeleton, or Materialize CSS as an alternative.

### C. HTML/CSS & Media
- Valid HTML5 - https://validator.nu/
- Valid CSS - https://jigsaw.w3.org/css-validator/
- Most CSS is in an external style sheet.
- Use HTML5 semantic and structural elements where practical.
- Images are properly optimized for Web delivery.

### D. Code Conventions
- All code is an external JavaScript file - inline event handlers are not allowed
- `let` and `const` must be used to declare variables (no `var`!)
- `querySelector()` and `querySelectorAll()` must be used for DOM traversal (DO NOT use the older methods)
- D.R.Y. - Don't Repeat Yourself. Repeated blocks of nearly identical code must be factored out and placed in a separate function.
- Variable and function names must begin with a lowercase letter.
- Well-commented code. Each and every function gets a comment indicating what it does.
- Delete or comment out any `console.log()` calls.

## III. Milestones
- Project proposal with mockup - see myCourses for due date/time. 
- Prototype - You should have a working version of your project for others to provide feedback on.  At a bare minimum, you should demonstrate functionality of your API call with results displayed on screen.  see myCourses for due date/time. 
- Final project deliverable - see myCourses for due date/time. 

## IV. Documentation
- As with Project 1, include a Documentation page (put the link in the comments field of the dropbox, as well as an easy to find link in the project site itself) where you document your process, cite any sources, tell me where to find anything special you want me to see, and also explain how you met the requirements. Finally, give yourself a grade for the project that you feel fairly represents what its worth.


## V. Grading
- The grading rubric for this project is visible in myCourses.  You should look it over carefully.  Find it by going to the "Assignments" section and clicking through to the "Project 2 Final Submission" dropbox.

Furthermore, Complete the Project 2 Assessment Survey. 

Reminder - 'A' -level work means doing college-level work that goes beyond what we did in class. (You should be able to see this reflected in the online Rubric). Meeting only the base requirements will most likely only earn you a B.

## VI. Submission
- ZIP and post the completed project and documentation page to to the mycourses dropbox
- Post the project to Banjo and link it from your 235 home page

<hr><hr>

**[Table of Contents <- About this Web App Tutorial Series](../notes/web-apps-0.md)**
