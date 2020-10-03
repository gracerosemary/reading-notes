[Javascript Templating Language and Engine— Mustache.js with Node and Express](https://medium.com/@1sherlynn/javascript-templating-language-and-engine-mustache-js-with-node-and-express-f4c2530e73b2)

## Javascript Templating

- Fast and efficient technique to render client-side view templates with JS using a JSON data source. Template is HTML markup with templating tags that insert variables or run programming logic.
- Template engine replaces variables and instances declared in a template file with actual values at runtime and convert the template into an HTML file sent to the client.

## Mustache

- Logic-less template syntax (because there are no if statements, else clauses, or for loops)
    - only uses tags (some tags are replaced with a value, some nothing, and others a series of values)
- Can be used for HTML, config files, source code, etc.
- Works by expanding tags in a template using values provided in a hash or object
- (mustache.js) / often considered the vase for JS templating but is not a templating engine
    - It is a *specification* for templating language
- Supports various languages

```jsx
Mustache.render(“Hello, {{name}}”, { name: “Sherlynn” });
// returns: Hello, Sherlynn
```

- 2 braces in the example above ( {{name}} ) show that it is a **placeholder.**
- When compiled, Mustache will look for the 'name' property in the passed object and replace {{name}} with the actual value.

## Mustache-Express

Lets you use Mustache and Express together easily and can be installed:

- $ npm install mustach - - save (2 dashes and 'save' have no space)

Configure mustache-express in your server.js/app.js/index.js file:

```jsx
var mustacheExpress = require('mustache-express');

// Register '.mustache' extension with The Mustache Express
app.engine('html', mustacheExpress());

app.set('view engine', 'html');
app.set ('views', _dirname + '/src/views');
```

Create a views folder and add some html view templates (ex. index.html)

```jsx
// html example with “Hello {{name}}” mustache usage
<div>
	<h1>Hello {{name}}</h1>
</div>
```

Within the router configuration, use res.render(TEMPLATE_NAME, JSON_DATA)

```json
res.render('hello', {"name": "Sherlynn"})

// first parameter ‘hello’ refers to the html file
// second parameter would be the JSON data
```

Can also pass in the variable representing the data

```json
var nameObject = {"name": "Sherlynn"}
res.render('hello', nameObject)
```

## [A Complete Guide to Flexbox]([https://css-tricks.com/snippets/css/a-guide-to-flexbox/](https://css-tricks.com/snippets/css/a-guide-to-flexbox/))

### Flexbox Layout (Flexible Box) module

- Provides a more efficient way to lay out, align, and distribute space among items in a container, even when the size is unknown and/or dynamic
- Gives the container the ability to alter its items' width/height (&order) to best fill the available space
    - Used mostly to accommodate all kinds of display devices and screen sizes
- Expands items to fill available free space or shrinks them to prevent overflow
- Layout is direction-agnostics as opposed to regular layout (block which is vertically-based and inline which is horizontally based)
    - direction-agnostic: capacity to work with various directions
    - works well with pages but lacks flexibility to support large or complex applications (esp. orientation changing, resizing, stretching, shrinking)
- Important note: Flexbox layout is most appropriate to the components of an application and small-scale layouts (while the Grid layout is intended for larger scale layouts)

### Basics & Terminology

- Flexbox is a whole module and not a single property.
- It involves many things, including its whole set of properties.
    - some are meant to be set on the container (parent element - known as **flex container)**
    - some are meant to be set on the children (**flex items**)
- Regular layout is based on both block and inline flow directions while flex layout is based on "flex-flow directions"

Items will be laid out following either the main axis (from main-start to main-end) or the cross axis (from cross-start to cross-end).

- **main axis** – The main axis of a flex container is the primary axis along which flex items are laid out. Beware, it is not necessarily horizontal; it depends on the `flex-direction` property.
- **main-start | main-end** – The flex items are placed within the container starting from main-start and going to main-end.
- **main size** – A flex item’s width or height, whichever is in the main dimension, is the item’s main size. The flex item’s main size property is either the ‘width’ or ‘height’ property, whichever is in the main dimension.
- **cross axis** – The axis perpendicular to the main axis is called the cross axis. Its direction depends on the main axis direction.
- **cross-start | cross-end** – Flex lines are filled with items and placed into the container starting on the cross-start side of the flex container and going toward the cross-end side.
- **cross size** – The width or height of a flex item, whichever is in the cross dimension, is the item’s cross size. The cross size property is whichever of ‘width’ or ‘height’ that is in the cross dimension.

## **Properties for the Parent (flex container)**

display: defines a flex container; inline or block depending on the given value. It enables a flex context for all its direct children. CSS columns have no effect on a flex container.

```css
.container {
  display: flex; /* or inline-flex */
}
```

flex-direction: establishes the main-axis, defining the direction flex items are placed in the flex container. Flexbox is (aside from optional wrapping) a *single-direction layout concept*. Think of flex items as primarily laying out either in **horizontal rows or vertical columns**.

```css
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}

/* 
row (default): left to right in 'ltr'; right to left in 'rtl'
row-reverse: right to left in ltr; left to right in rtl
column: same as row but top to bottom
column-reverse: same as row-reverse but bottom to top 
*/
```

flex-wrap: by default, flex items will all try to fit onto one line. Can be changed to allow the items to wrap as needed with this property.

```css
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}

/*
nowrap (default): all flex items will be on one line
wrap: flex items will wrap onto multiple lines, from top to bottom.
wrap-reverse: flex items will wrap onto multiple lines from bottom to top.
*/
```

flex-flow: shorthand for the `flex-direction` and `flex-wrap` properties, which together define the flex container’s main and cross axes. The default value is `row nowrap`.

```css
.container {
  flex-flow: column wrap;
}
```

justify-content: defines the alignment along the main axis. It helps distribute extra free space leftover when either all the flex items on a line are inflexible, or are flexible but have reached their maximum size. It also exerts some control over the alignment of items when they overflow the line.

```css
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
}

/*
flex-start (default): items are packed toward the start of the flex-direction.
flex-end: items are packed toward the end of the flex-direction.
start: items are packed toward the start of the writing-mode direction.
end: items are packed toward the end of the writing-mode direction.
left: items are packed toward left edge of the container, unless that doesn’t make sense with the flex-direction, then it behaves like start.
right: items are packed toward right edge of the container, unless that doesn’t make sense with the flex-direction, then it behaves like start.
center: items are centered along the line
space-between: items are evenly distributed in the line; first item is on the start line, last item on the end line
space-around: items are evenly distributed in the line with equal space around them. Note that visually the spaces aren’t equal, since all the items have equal space on both sides. The first item will have one unit of space against the container edge, but two units of space between the next item because that next item has its own spacing that applies.
space-evenly: items are distributed so that the spacing between any two items (and the space to the edges) is equal.
*/
```

align-items: defines the default behavior for how flex items are laid out along the **cross axis** on the current line. Think of it as the `justify-content` version for the cross-axis (perpendicular to the main-axis).

```css
.container {
  align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
}

/*
stretch (default): stretch to fill the container (still respect min-width/max-width)
flex-start / start / self-start: items are placed at the start of the cross axis. The difference between these is subtle, and is about respecting the flex-direction rules or the writing-mode rules.
flex-end / end / self-end: items are placed at the end of the cross axis. The difference again is subtle and is about respecting flex-direction rules vs. writing-mode rules.
center: items are centered in the cross-axis
baseline: items are aligned such as their baselines align
*/
```

align-content: aligns a flex container’s lines within when there is extra space in the cross-axis, similar to how `justify-content` aligns individual items within the main-axis. This property has no effect when there is only one line of flex items.

```css
.container {
  align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
}

/*
normal (default): items are packed in their default position as if no value was set.
flex-start / start: items packed to the start of the container. The (more supported) flex-start honors the flex-direction while start honors the writing-mode direction.
flex-end / end: items packed to the end of the container. The (more support) flex-end honors the flex-direction while end honors the writing-mode direction.
center: items centered in the container
space-between: items evenly distributed; the first line is at the start of the container while the last one is at the end
space-around: items evenly distributed with equal space around each line
space-evenly: items are evenly distributed with equal space around them
stretch: lines stretch to take up the remaining space
*/
```

### **Properties for the Children (flex items)**

order: controls the order in which they appear in the flex container.

```css
.item {
  order: 5; /* default is 0 */
}
```

flex-grow: defines the ability for a flex item to grow if necessary. It accepts a unitless value that serves as a proportion. It dictates what amount of the available space inside the flex container the item should take up.

```css
.item {
  flex-grow: 4; /* default 0 */
}

/*
If all items have flex-grow set to 1, the remaining space in the container will be distributed equally to all children. If one of the children has a value of 2, the remaining space would take up twice as much space as the others (or it will try to, at least).
*/
/* Negative numbers are invalid. */
```

flex-shrink: defines the ability for a flex item to shrink if necessary.

```css
.item {
  flex-shrink: 3; /* default 1 */
}
/* Negative numbers are invalid. */
```

flex-basis: defines the default size of an element before the remaining space is distributed. It can be a length (e.g. 20%, 5rem, etc.) or a keyword.

```css
.item {
  flex-basis:  | auto; /* default auto */
}
```

flex: shorthand for flex-grow, flex-shrink and flex-basis combined. The second and third parameters (flex-shrink and flex-basis) are optional. The default is 0 1 auto, but if you set it with a single number value, it’s like 1 0.

```css
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
```

align-self: allows the default alignment (or the one specified by align-items) to be overridden for individual flex items.

```css
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

Important note: float, clear and vertical-align have no effect on a flex item

# Flexbox Froggy

Practice Exercises: [https://flexboxfroggy.com/](https://flexboxfroggy.com/)

You win! Thanks to your mastery of flexbox, you were able to help all of the frogs to their lilypads. Just look how hoppy they are!

If you found this ribbeting, be sure to visit [Grid Garden](https://codepip.com/games/grid-garden/) to learn about another powerful new feature of CSS layout. You can also find other coding games over at [Codepip](https://codepip.com/).