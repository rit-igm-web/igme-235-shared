# 9 - WebStorage API

## I. Overview
The HTML5 WebStorage API allows us to store **key:value** data in the user's browser, and that information can be retrieved at a later date by your JavaScript (when the user returns to your page).

## Contents
<!--- Local Navigation --->
I. [WebStorage Reference](#section1)

II. [An Example](#section2)

III. [Storing Objects with WebStorage](#section3)

IV. [Nota Bene](#section4)

<hr><hr>

## I. <a id="section1">WebStorage Reference
There are some WebStorage examples on the Internet that we can point you to:

- https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API
- https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API
- https://html.spec.whatwg.org/multipage/webstorage.html
- https://mdn.github.io/dom-examples/web-storage/


## II. <a id="section2">An Example

- Try out this example, whenever you `onchange` the values of the textbox or the &lt;select>, their values are written to `localStorage`. 
- If you close the window and reopen it, your changes will be preserved.  
- After you have referred to the links above, it should be pretty easy to figure out what's going on in the code.
- One thing worth mentioning is the `prefix` variable (see below):
    - Because Web Storage uses the same set of keys for *each domain*, this means that on shared domains like `people.rit.edu` that all of the students are **sharing the same set of keys**, so that if someone uses `highscores`as a key, another student's `highscores` key could wipe out and replace their data. 
    - One solution is to prefix your key names with something unique, like your RIT web account id. 
    - Therefore `highScores` would become `abc1234-highScores` for one student, and `xyz9876-highScores` for someone else, and the keys would never conflict.

### webstorage-1.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8" />
	<title>Web Storage Example</title>
</head>
<body>

<div>
What is your name -> <input type='text' id='nameField'>
</div>

<div>
What is your favorite color -> 
<select id="colorSelect">
	<option value="red">Red</option>
	<option value="green">Green</option>
	<option value="blue">Blue</option>
	<option value="magenta">Magenta</option>
	<option value="cyan">Cyan</option>
	<option value="white">White</option>
	<option value="gray">Gray</option>
</select>
</div>

</body>
<script>

/* This stuff happens "onload" */
// declare some constants
const nameField = document.querySelector("#nameField");
const colorSelect = document.querySelector("#colorSelect");
const prefix = "abc1234-"; // change 'abc1234' to your banjo id
const nameKey = prefix + "name"
const colorKey = prefix + "color";

// grab the stored data, will return `null` if the user has never been to this page
const storedName = localStorage.getItem(nameKey);
const storedColor = localStorage.getItem(colorKey);

// if we find a previously set name value, display it
if (storedName){
	nameField.value = storedName;
}else{
	nameField.value = "Turbo"; // a default value if `nameField` is not found
}

// if we find a previously set color value, display it
if (storedColor){
	colorSelect.querySelector(`option[value='${storedColor}']`).selected = true;
}

/* This stuff happens later when the user does something */
// when the user changes their favorites, update localStorage
nameField.onchange = e=>{ localStorage.setItem(nameKey, e.target.value); };
colorSelect.onchange = e=>{ localStorage.setItem(colorKey, e.target.value); };


</script>
</html>
```

### A. And here is what it looks like:

![Web Page](_images/web-storage-1.jpg)

### B. You can also see your selections reflected in the web inspector:

![Web Page](_images/web-storage-3.jpg)


<hr>

### ** *Try This!* **
- Modify *webstorage-1.html* by adding a "What is your Quest?" dropdown with values like "I seek the Holy Grail" and "To end injustice!".
- Store/restore the chosen value in localStorage.

<hr>

## III. <a id="section3">Storing Objects with Web Storage
- A major limitation of Web storage is that it doesn't allow us to store arrays and other objects directly - but there's an easy workaround:
    - you can easily convert built-in JavaScript objects (Object, Array, Date, etc) to and from a string representation, and then save them to `localStorage`.
    - this is known as *serialization* - https://en.wikipedia.org/wiki/Serialization

### A. Save an array to localStorage with `JSON.stringify()`

```javascript
let listID = "abc1234-action-list";
let items = ["Direct Movie","Deliver Baby","Cure Cancer","Walk on Mars"];
items = JSON.stringify(items); 			// now it's a String
localStorage.setItem(listID, items);
```

### B. Retrieve an array from localStorage with `JSON.parse()`

```javascript
let listID = "abc1234-action-list";
let items = localStorage.getItem(listID); 	// returns a String
items = JSON.parse(items);  			// now it's an Array again
```

## IV. <a id="section4">Nota Bene
- The process by which the browser works out how much space to allocate to web data storage and what to delete when that limit is reached is not simple, and differs between browsers - read about it here: https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API/Browser_storage_limits_and_eviction_criteria
- Because localStorage is a *synchronous* (blocking) API, understand that DOM updates will "hang" whenever localStorage is being updated by your code. What this means is that you should be careful about when you update your localStorage values.
    - In a game for example, **DO NOT** update your `highScore`  localStorage value inside of your game loop  - 60 times a second - to do so would seriously harm the game's performance.
    - Instead, do the localStorage update only occasionally, when a level or the entire game are completed, for example.
- You can read more about the blocking issue here: https://nolanlawson.com/2015/09/29/indexeddb-websql-localstorage-what-blocks-the-dom/


**Something to consider:**
One big issue with the applications we have written this semester is that reloading the page will wipe out all of the user's work (for example the poem they created in *Magnetic Poetry*, or their pixel art creation in *Pixel Artist*). Think about the various HW assignments that we have worked on for this Web Apps unit - how they could be improved by utilizing web storage?

<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|    **[JavaScript Arrays (chapter 8)](web-apps-8.md)** |  **[About this Web App Tutorial Series](web-apps-0.md)** |  **[Web Services (chapter 10)](web-apps-10.md)**
