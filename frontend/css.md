#CSS
##Selectors

- **Tag** `p { color: red; }`
- **Class** `.fancy { color: red; }`
- **Id** `#serious { color: red; }`
- **Multiple (nested)** `div div h3 { color:red; }` *selectors with greater specificity value will override others*
- **Direct children** `div > p { color:red}` *literally direct children,  meaning there are no other tags in between*
- **Pseudo-class** *Are used to access HTML items that aren't part of the document tree, such as hover o link clicked*
	* `a:hover { boder: 1px; }`
	* `a:visited { boder: 1px; }`
	* `a:link { boder: 1px; }`
	* `p:first-child { color:red; } `
	* `p:nth-child(2) { color:red; } `
	* `li:after{ content: '\\;}` will add a \ after each list element
	* `li:before{ content: '\\;}` will add a \ before each list element

- **Universal** `*{ border: 1px;}`

##Styles

- font-family
- color
- background-color
- background (e.g for images) `background: url(../img/banner.png) no-repeat;`
- text-align
- text-decoration (e.g. underline) `text-decoration: none`
- font-size
- border `border: 1px dashed blue;`
- border-radius (makes buttons rounded) `border-radius: 5px;`
- font-weigth `font-weight:bold;`

##Positioning
###The boxes
![GitHub Logo](http://www.w3schools.com/css/box-model.gif)

- margin `margin:auto` (to equal margins on each side)
- padding `padding: 10px 20px 10px 1px`
- z-index for depth 

######THE DISPLAY PROPERTY
**block**: This makes the element a block box. It won't let anything sit next to it on the page! It takes up the full width but also responds to widht, height and %. This is the default value

**inline-block**: This makes the element a block box, but will allow other elements to sit next to it on the same line. Responds to widht, height and %

**inline**: This makes the element sit on the same line as another element, but without formatting it like a block. It only takes up as much width as it needs (not the whole line).

**none**: This makes the element and its content disappear from the page entirely!

###Moving the boxes
######THE FLOAT PROPERTY
If you assign an `img`, `div`, or other element a value of float:right or float:left, it will float to the right or left and the text will flow around it.

- float `	float:[right | left]` to determine where elements go in the page. Combined with
	-	`clear: [right|left|both]` to move the element below.

######RELATIVE POSITONING
**static** The default

**absolute** Positioned in relation to the first non-static parent, or if there is none, relative to `<html>`. Notice that, when no styling is applied to the child, it stays within the parent, so to apply the positioning, `position:absolute` should be followed by something else. `left` will mean: "I want this on the left with some pixels"

**relative** Move relative to where it would have landed if it just had the default static positioning. Note that the element still 'takes up' its original space.

**fixed** Anchors an element to the browser window.If you scroll up and
 down, the fixed element stays put even as other elements scroll past.



##EXAMLES
###Link at HTML file###
	`<link type="text/css" rel="stylesheet" href="stylesheet.css"/>`
###Menu with \ separator
```
.meta li:after {
	content: \\;
	padding : 0 2px;
}

.meta li:last-child:after {
	content:none;
}
```

##TRICKS
- Use `overflow:hidden` to set a height to a div containing floated elements and to force the following elements to be displayed below.
- Transparency can be set by using the `rgba` function like `background: rgba(0,0,0, .5);`
- `clearfix` A clearfix is a way for an element to automatically clear its child elements. It is often used when a div colapses because it's wrapping a collection of floated elements.
- Adding padding to a box will increase its overall size. However, using `box_sizing:border-box` will make the size of the box remain the same.

##RESPONSIVITY
- Use foundation, and display flex
