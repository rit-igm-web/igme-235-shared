# Exercise: Formatting Text

Let's modify our text a bit. 

## Do the following:

1. Apply a main font (I suggest **Arial**) and a common font (I suggest **sans-serif**) to your whole page.  What element should you apply it to?  Leave it the default size.
    - Hint:  Use the **font-family** property and two comma-separated values.

1. Add a Web Font to your page from *Google Fonts*.  Apply it to your **headings**.
    - Helpful steps:
        1. Go to http://fonts.google.com
        1. Pick something interesting (click on "+ Select this style" next to the version you want to use)
        1. In the "Selected Family" overlay that appears, click the embed tab.
        1. Copy and Paste the standard link into your `<head>`
        1. Copy the provided **font-family** declaration into your heading style rule(s)

1. Try adding a universal selector to your style rules and adding a "1px solid gray" **border** to everything.  See what it looks like, but don't leave it there.
    - Hint, the universal selector is a single character.

## If you are so inclined, otherwise, move on.
- Try proving that you can make a functional **descendant** selector where a paragraph (or other element) that's located in your `<footer>` (for example) has a different style applied to it than a paragraph that appears elsewhere on your page.
