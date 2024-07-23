# Exercise: CSS Frameworks

In this exercise we explore the use of Frameworks in web development. Frameworks are utilized by a large proportion of the web development community, since they offer a quicker development option, as well as provide a similar design language.

Start by downloading the starter file located here: [Frameworks Starter Files](css_frameworks_demo.zip).

## Part One - Look over the Default Styles

1. Look over your starter files, **open the directory in VS Code** (right click the folder or inside of it, and -- if it's a choice -- choose Open with Code... if not, use the open folder command from within VS Code), and preview the “default-start.html”. We will be using the Live Server extension for the exercise, so at this point, launch the Live Server and observe how the default-start.html appears in your web browser.

2. Go back to VS Code and look at the code. Notice we have a style.css file in our **css** folder. There are some basic CSS directives applied to our **default-start.html** file, nothing too fancy.

3. The body of the **default-start.html** file is pretty basic. To simplify our development for the exercise, we are not using images, but rely on a third party site called **[placeholder.com](https://placeholder.com/)**, this is a handy utility site that just provides placeholder images to whatever size you want. The remainder of the content is relatively basic, we also have an HTML Table in the Main, as well as a basic form (we know we’ve not covered tables or forms, but they are a standard part of web development that you'll encounter at some point). 

## Part Two - Bootstrap

1. Open a new browser window or tab, and go to https://getbootstrap.com/, click the “**Read the docs**” button on the page. We will be doing the **Quick Start**, and using a *CDN (Content Delivery Network)* and not downloading the framework locally. 

2. Back in VS Code, make a copy of the **default-start.html** file and rename to **bootstrap.html**, and open this file. 

3. In the **HEAD** section of the **bootstrap.html** file paste the CSS code from the Bootstrap Quick Start into your file (Be sure it goes BEFORE the link to style.css):

Copy it from the web page or from right here:

   ```
   <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-F3w7mX95PdgyTmZZMECAngseQB83DfGTowi0iMjiWaeVhAn4FJkqJByhZMI3AhiU" crossorigin="anonymous">
   ```

4. Next, below the styles.css link, paste the given links to Javascript libraries.  The bootstrap site suggests you add this code at the bottom of your web page right before the closing </body> tag.  However, with a situation like this, you can still put them in the head section.

Copy from the web page or from right here:
   
```
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.3/dist/umd/popper.min.js" integrity="sha384-W8fXfP3gkOKtndU4JGtKDvXbO53Wy8SZCQHczT5FMiiqmQfUpWbYdTil/SxwZgAN" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/js/bootstrap.min.js" integrity="sha384-skAcpIdS7UcVUC05LJ9Dxay8AXcDYfBJqt1CJ85S/CFujBsIzCIv+l9liuYLaMQ/" crossorigin="anonymous"></script>
   ```
   
5. Now preview the **bootstrap.html** file in your browser as well (it would be best to open in a new window or tab). Notice the differences between base styles and the bootstrap-applied styles.  It's not a lot, but there are font differences and line-height changes, etc.

6. These base CSS changes are fine, but let's talk about some of the more interesting aspects of having a framework. Let's look at a NavBar and a Carousel.

7. In VS Code, duplicate the **bootstrap.html** and name the new file **bootstrap-navbar.html**, and in the new file empty out the body content.

8. Let's first start with the NavBar, go to https://getbootstrap.com/docs/5.1/components/navbar/ and we will copy the first example code into our newly emptied body (here it is it, also):

```
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            Dropdown
          </a>
          <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" href="#">Action</a></li>
            <li><a class="dropdown-item" href="#">Another action</a></li>
            <li><hr class="dropdown-divider"></li>
            <li><a class="dropdown-item" href="#">Something else here</a></li>
          </ul>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled">Disabled</a>
        </li>
      </ul>
      <form class="d-flex">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>
```

9. Now save and reload this page and see the results. Resize the browser window, notice what happens to the navigation? Go back into VS Code and look closely at the code, do you see the large number of CSS classes that each element has? All those classes are what makes the navbar function, there are also a number of data and aria attributes used as well. Feel free to experiment with the navbar, add some links, or even try to add another pulldown.

10. Lastly, let's look at a Slideshow Carousel. In VS Code, let's duplicate the current **bootstrap-navbar.html** and rename the new file to **bootstrap-carousel.html**. In the new file, clear out the body tag.

11. Now we will utilize the #slideshow rules found in our **style.css**.

12. Go take a look at this url: https://getbootstrap.com/docs/5.1/components/carousel/. You can refer to this page for more information about the Carousel, but we'll be putting in some of our own code for this next example. The HTML below is based off the first sample, but we've replaced the images with 5 slides from placeholder.com.

Copy and paste this into your body:

```
    <div id="container">
      <div id="slideshow">
        <div id="carouselExampleSlidesOnly" class="carousel slide" data-bs-ride="carousel">
          <div class="carousel-inner">
            <div class="carousel-item active">
              <img src="https://via.placeholder.com/500x300/0000FF/808080?text=Slide1" class="d-block w-100" alt="...">
            </div>
            <div class="carousel-item">
              <img src="https://via.placeholder.com/500x300/00AAFF/808080?text=Slide2" class="d-block w-100" alt="...">
            </div>
            <div class="carousel-item">
               <img src="https://via.placeholder.com/500x300/00FFAA/000000?text=Slide3" class="d-block w-100" alt="...">
             </div>
             <div class="carousel-item">
               <img src="https://via.placeholder.com/500x300/AADD00/000000?text=Slide4" class="d-block w-100" alt="...">
             </div>
             <div class="carousel-item">
               <img src="https://via.placeholder.com/500x300/22FADA/000000?text=Slide5" class="d-block w-100" alt="...">
             </div>
           </div>
         </div>
       </div>
     </div>
 ```

13. Save and preview this file, observe the glory of a fully functional carousel slideshow!  You'll need to wait about 5 seconds to see it change.

14. Now, can you alter this slideshow and change into a slideshow with controls? The code is on the Bootstrap page, see if you can make that work.
    - Hint: Note the relationship in the code between the ```id``` of the carousel and the ```data-bs-target``` values of the next and previous buttons.



## Part Three - Materialize

1. Open a new browser window or tab, and go to https://materializecss.com/, click the “**Get Started**” button on the page. We will also be using the CDN version of Materialize. 

2. Back in VS Code, make a copy of the **default-start.html** file and rename to **materialize.html**, and open this file. 

3. In the **HEAD** section of the **materialize.html** file paste the links to the CSS and Javascript code from the CDN section into your file *(Be sure the link to the CSS goes BEFORE your style.css, and link to the JavaScript AFTER)*:
   
```
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/css/materialize.min.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/js/materialize.min.js"></script>
```
   
4. Now go to your web browser and load the **materialize.html** file in a new window or tab. Compare the Materialize version to the Bootstrap version to the version without a framework.

5. Notice how just by including the frameworks, the differences can be quite dramatic. What do you notice?

6. Just like the Bootstrap framework, there are similar components available. Let's take a look at the Navbar. Make a copy of the **materialize.html** and rename the new file to **materialize-navbar.html**, open this file and clear out the body content.

7. Open a web browser tab or window to https://materializecss.com/navbar.html, this is the documentation page for the Materialize Navbar, let's start with the basic Navbar. Copy this code into your **materialize-navbar.html** body.

   ```
   <nav>
   <div class="nav-wrapper">
     <a href="#" class="brand-logo">Logo</a>
     <ul id="nav-mobile" class="right hide-on-med-and-down">
   	<li><a href="sass.html">Sass</a></li>
   	<li><a href="badges.html">Components</a></li>
   	<li><a href="collapsible.html">JavaScript</a></li>
     </ul>
   </div>
   </nav>
   ```

8. Notice what makes this nav work, there doesn't appear to be much, now go load this page in your browser. Now you have a responsive navbar. We're skipping the dropdown feature, because Materialize requires us to do a little more JavaScript in order to make a dropdown function, but if you're feeling up to it, give it a try. Otherwise, go ahead and try a few of the other navbars from the Materialize page.

9. Now let's take a look at the Materialize Carousel. Go to your web browser and open a window or tab to https://materializecss.com/carousel.html. This is the reference page for the Materialize Carousel.

10. in VS Code, make a copy of your **materialize.html** file and rename it to **materialize-carousel.html** and once again, clear out the body. Then add the following code into the body. 

    ```
    <div class="carousel">
            <a class="carousel-item" href="#"><img src="https://via.placeholder.com/500x300/0000FF/808080?text=Slide1"></a>
            <a class="carousel-item" href="#"><img src="https://via.placeholder.com/500x300/00AAFF/808080?text=Slide2"></a>
            <a class="carousel-item" href="#"><img src="https://via.placeholder.com/500x300/00FFAA/000000?text=Slide3"></a>
            <a class="carousel-item" href="#"><img src="https://via.placeholder.com/500x300/AADD00/000000?text=Slide4"></a>
            <a class="carousel-item" href="#"><img src="https://via.placeholder.com/500x300/22FADA/000000?text=Slide5"></a>
        </div>
    ```

    You can see this is just a simple div tag with some href images, what's important here is notice the class names assigned to all the elements.

11. Now after the div, we will place a script tag to put some JavaScript on the page that initializes our slideshow. 

    ```
    <script>
    	var elems = document.querySelectorAll('.carousel');
    	var instances = M.Carousel.init(elems);                
    </script>
    ```

    We won't dwell on what this code means, but it essentially initializes our carousel, without this, nothing happens.

12. Now go back to the web browser and load this page, you should see a fancy looking carousel. Not bad with only a little bit of code! Feel free to try out the other types of carousels, such as the slider carousel.

    

## Part Four - Font Awesome

1. For our last part of the lab, we'll take a look at Font Awesome. Font Awesome isn't an extensive style library like the others, but it does provide an important function, which is to provide easy to use iconography for your web site.

2. In VS Code, open the **navbar-start.html** file. To keep things simple, we have an embedded CSS style that formats our header, nav and main elements on our simple page. 

3. Open this page in the browser. Observe how it's just a simple page with a header, some text and 2 buttons. It's rather plain, so we'll add some imagery to make our links and options look much better.

4. Back in VS Code, copy the **navbar-start.html** file to **fontawesome.html**.

5. In a web browser window or tab, go to https://fontawesome.com/. We will refer back to this site for finding icons. They don't provide an easy-to-get-to CDN link, so we'll use another resource to get a CDN, open a new tab or window and go to https://cdnjs.com/libraries/font-awesome.

6. From cdnjs, use the pull-down to select the most recent non-beta version (currently 5.15.4) and copy the first css link (make sure to use the "copy link tag" button so that you get the full HTML) and paste it into the HEAD section of your fontawesome.html file, once again, be sure this is before the link to your style.css link.

This is the URL that you'll be using (but you need to include it in a full link tag)
```
   https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css
   ```
   
7. Let's enhance one of our links in the nav bar. First, go back to the window you opened to https://fontawesome.com, and in the search box in the header, type in "instagram" and click the search button. In the search results, click the first matching result.

8. From the result, you will see that various styles the icon has, now click the "Start Using This Icon". A dialog appears with a snippet of code for this icon, copy the code:

   ```
   <i class="fab fa-instagram"></i>
   ```

9. Go back to VS Code and your fontawesome.html file. Locate the link for Instagram, and add this code (and a space) in front of the "Instagram" text for the link, it should now look like the following:

   ```
   <a href="#"><i class="fab fa-instagram"></i> Instagram</a>
   ```

10. Save and load the page in a web browser. Notice how the link looks now?

11. Let's add another icon to our **Help** button, go back to the fontawesome site, and now search for "**help**", a large number of results comes back for this simple search term, but we'll pick the solid "question-circle". Once again, click on the icon and get the code from the "Start Using This Icon" button. 

12. Back in VS Code, find our help button and add the code to the front of our text:

    ```
    <button><i class="fas fa-question-circle"></i> Help</button>
    ```

13. Now reload the page and you should see the button now show the icon before the text.

14. Now it's time for you to complete the rest. Go forth and search for icons to use for the rest of the links in the navbar and the last email button. Feel free to add any additional buttons or icons to your file.

## Wrap Up

That's it for now. We recommend taking some time and exploring the documentation for these CSS frameworks to see what else they offer. Hopefully you can see how just a little bit of code within the framework yields impressive results. 

Be sure you upload your work to Banjo, zip up your work and submit the zip file and link to the assignment folder (Since there is no index.html it should load up a list of the files in your directory -- wherever you put it).

We should be able to click to 3 different bootstrap files, 3 materialize files, and a fontawesome file.










