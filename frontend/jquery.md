#JQuery
##Concepts
###Getting started...
HTML file:`<script type="text/javascript" src="script.js"></script>`

Script file: `$(document).ready(function() { });`

###The this keyword
The `this` keyword refers to the jQuery object you're currently doing something with, i.e. the element that called the current event handler.

##Methods
######FANCY STYLES
- `.fadeOut(1000);`
- `.fadeTo('fast', 1);`
- `.mouseenter(function() {`
- `.mouseleave(function() {`
- `.hide()`
- `.slideToggle('slow');` To slide down


######HTML
- `.append("Some HTML code")` Inserts the specified element as the last child of the target element
-  `.prepend("Some HTML code")` Inserts the specified element as the first child of the target element
-  `.after("Some HTML code")`
-  `.before("Some HTML code")`
- `.remove()`
- `.html("New content");` Will modify the content of the element

######CSS
- `.addClass('className');` 
- `.removeClass('className');` 
- `.toggleClass('className');` Toggles the CSS class (add or remove)
- `.height("100px");`
- `.width("100px");`
- `.css("background-color","#008800");` General CSS
- `.hover(function(){},function(){});` First function is for hover and the second one for not hover

######FORMS
- `$('input[name=checkListItem]').val();` Get the value of the input field 

######EVENTS
- `.click(function() { ` It will not work for items added after the DOM was loaded
- `$(document).on('event', 'selector', function() {` It wil work for items added after the DOM was loaded
- ` $(document).keydown( function() { `

######EFFECTS AND ANIMATIONS
- `.effect('[bounce | explode | slide]');`
- `.animate({ top: '+=100px'}, 1000);`
- `.accordion({collapsible: true, active: false});` For dropdown menus
-  `.draggable();` Makes an HTML element dragable, awesome...
-  `.selectable()` Enhances the selected element (e.g of an `ul` or `ol`) by highlighting it.
-  `sortable()` Makes the elements (e.g of an `ul` or `ol`) sortable, awesome...

######EXAMPLES

```
$(document).ready(function(){
	$("div").hover(
    function(){
     $(this).addClass('active');
    },
    function(){
      $(this).removeClass('active');  
    });
});
```

```
$(document).ready(function() {
    $(document).keydown( function () {
   $('div').animate({left:'+=10px'},500);
    });
});
```
