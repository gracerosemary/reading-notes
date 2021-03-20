# Reading
JavaScript and jQuery book by Jon Duckett pages 293-301, 306-331 and 354-357
[6 Reasons for Pair Programming](https://www.codefellows.org/blog/6-reasons-for-pair-programming/)
> "Write less, do more"

## JQUERY 
**Select Elements**: Simpler to access elements using jQuery's CSS-style selectors than it is using DOM queries. Selectors are also more powerful and flexible. 
**Perform Tasks**: Methods let you update DOM tree, animate elements into and out of view, and loop through a set of elements, all in one line of code. 
**Handle Events**: Includes methods that allow you to attach event listeners to selected elements without having to write any fallback code to support older browsers. 

### Find elements using CSS-Style Selectors
- Function `jQuery()` lets you find one or more elements in the page. 
- It creates an object called **jQuery** which holds references to those elements. 
- `$()` is often used as shorthand for `jQuery()` and only has one parameter: a CSS-style selector
    Example: `$('li.hot')`
    - This selector finds all of the `<li>` elements with a **class** of **hot**. 

### Do something with the elements using jQuery methods
- Object and elements are referred to as a **matched set** or a **jQuery selection**
- Use the methods of the **jQuery** object to update the elements that it contains

`$('li.not').addClass('complete');`

`$('li.hot')` - jQuery Object
`.` - member operator
`addClass('complete');` - method
`'complete'` - parameter(s)

    - The method adds a new value to the **class** attribute

### Basics
1. Include jQuery to html (before the body tag)
    `<script src="js/jquery-1.11.0.js"></script>`
2. Include a second JS file that uses jQuery selectors and methods to update the content of the HTML page
    `<script src="js/basic-example.js"></script>`

### Selectors Definitions
#### BASIC SELECTORS
*: All elements
element: All elements with that element name
#id: Elements whose id attribute has the value specified
.class: Elements whose cl ass attribute has the value specified
selectorl, selector2: Elements that match more than one selector (see also the .add()
method, which is more efficient when combining selections)

#### HIERARCHY:
ancestor descendant: An element that is a descendant of another element (e.g., 1 i a)
parent > child: An element that is a direct child of another element (you can use* in
the place of the child to select all child elements of the specified parent)
previous + next: Adjacent sibling selector only selects elements that are immediately
followed by the previous element
previous - s ib Zings: Sibling selector will select any elements that are a sibling of the
previous element

#### BASIC FILTERS:
:not (selector): All elements except the one in the selector (e.g., div: not ('#summary'))
:first: The first element from the selection
:last: The last element from the selection
:even: Elements with an even index number in the selection
:odd: Elements with an odd index number in the selection
:eq(index): Elements with an index number equal to the one in the parameter
:gt(index): Elements with an index number greater than the parameter
:lt(index): Elements with an index number less than the parameter
:header: All `<hl>` - `<h6>` elements
:animated: Elements that are currently being animated
:focus: The element that currently has focus 

#### CONTENT FILTERS 
:contains('text '): Elements that contain the specified text as a parameter 
:empty: All elements that have no children 
:parent: All elements that have a child node (can be text or element) 
:has (selector): Elements that contain at least one element that matches the selector
(e.g., d; v: has (p) matches all d; v elements that contain a `<p>` element) 

#### VISIBILITY FILTERS 
:hidden: All elements that are hidden 
:visible: All elements that consume space in the layout of the page
Not selected if: d; sp 1 ay: none; he; ght I w; dth: O; ancestor is hidden
Selected if: v; s; bi U ty: hidden; opacity: 0 because they would
take up space in layout 

### Matched Set / jQuery Selection
##### Single Element
If a selector returns one element, the jQuery object contains a reference to just one element node
    `$('ul')`
    This selector picks the `<ul>` element from the page. Contains a references to just one node (the only `<ul>` element on the page)
##### Multiple Elements
If a selector returns several elements, the jQuery object contains references to each element
    `$('li')`
    This selector picks all the `<li>` elements and has references for each of the nodes that was selected

### Storing References to Elements
When a selection is created, it stores a referenece to the corresponding nodes in the DOM tree. It does NOT create copies of them. 
- It stores the location of a piece of inofmraiton in the browser's memory

### Caching selections in variables
Caching a jQuery object stores a reference to it in a variable. 
- Note: when a variable contains a jQuery object, it is ogten given a name beginning with the $ symbol, to help differentiate it from other variables in your script. 
    `$listItems = $('li');`

### Looping
- When a selector returns multiple elements, you can update all of them using the one method. There is no need to use a loop. 
- The ability to update all of the elements in the jQuery selection is known as implicit iteration.
- When you want to get information from a series of elements, you can use the `.each()` method rather than writing a loop. 

### Chaining
The proess of placing several methods in the same selector
- You can list several methods at a time using dot notation to separate each one
    `$('li[id!="one"]').hide().delay(500).fadeIn(1400);`

### Checking a page is ready to work with
jQuery's `.ready()` method checks that the page is ready for your code to work with
    `$(document).ready(function(){//script});`

### Getting element content
`.html()` - used to retrieve information from a jQuery selection and only retrieves the HTML inside the *first* element in the matched set, along with any of its descendants
    `$('ul').html();` will return all `<li>` descendants within `<ul>`

`.text()` - used to retrieve the text from a jQuery selection and returns the content from every element in the jQuery selection, along with the text from any descendants

### Updating Elements
`.replaceWith()` - replaces every element in a mtached set with new content. Also returns the replaced elements. 
`.remove()` - removes all the elements in the matches set

### Inserting Elements
`.before()` - inserts content before the selected element
`.after()` - inserts content after the selected element
`.prepend()` - inserts content after the opening tag
`.append()` - inserts content before the closing tag

### Getting and Setting attribute values
`.attr()` - can get or set a specified attribute and its value
`.removeAttr()` - removes a specified attribute and its value
`.addClass()` - adds a new value to the existing value of the class attribute but does not overwrite the existing values
`.removeClass()` - removes a value from the class attribute, leaving any other class names within that attribute intact

### Working with Each element in a selection
`.each()` - allows you to perform one or more statements on each of the items in the selection of elements that is returned by a selector (like a loop in JS)
`this` or `$(this)` - used to access the current element

### Event Methods
`.on()` - used to handle all events

`.on(*events*[, selector][, data], function(e));`

### Loading jQuery from a CDN
- Starts with a `<script>` tag that tries to load the file from the CDN
- Protocal Relative URL: URL for the script starts with two forward slashes (not http:)

### Placement of scripts
- At the end of the page before the closing `</body>` tag so that it does not affect the rendering of the rest of the page



