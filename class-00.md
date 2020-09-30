# [Responsive Web Design](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/)

**Notes**
### Responsive Overview
- Building a website that is suitable for all devices and every screen size. 
- Focused around providing an intuitive and gratifying experience for everyone. 
- Largely developed by Ethan Marcotte - also has a book called "Responsive Web Design". 

#### Responsive vs Adaptive vs Mobile
- Responsive: react quickly and positively to any change. 
- Adaptive: easily modified for a new purpose or situation. 
- Mobile: website built on a new domain solely for mobile users. 

### Flexible Layouts
- 3 main components of Responsive web design: flexible layouts, media queries, and flexible media
- Flexible layout is the practice of building the layout of a website with a flexible grid, capable of dynamically resizing to any width. Built using relative length units (most commonly percentages or em units) 
- The relative length units are used to declare common grid property values (ex. width, margin, padding).
- Does not adovocate for the use of fixed measurement units (ex. pixels, inches) because the viewport height and width contiually change based on the device being used (too many constraints). 
- Formula based on taking target width of an element and dividing it by the width of it's parent element:

`target ÷ context = result`

#### Relative Viewport Lengths
- New relative length units include:
    1. vw: viewports width
    2. vh: viewports height
    3. vmin: min of the viewport's height and width
    4. vmax: max of the viewport's height and width

#### Flexible Grid
- Take all the fixed units of length and turn them into relative units: 
    Example: 
        `section,`
        `aside {`
        `margin: 1.858736059%;` /*  10px ÷ 538px = .018587361 */
        `}`
        `section {`
        `float: left;`
        `width: 63.197026%;`    /* 340px ÷ 538px = .63197026 */  
        `}`
        `aside {`
        `float: right;`
        `width: 29.3680297%;`  /* 158px ÷ 538px = .293680297 */
        `}`

### Media Queries
- Built as an extension to media types. 
- It provides the ability to specify different styles for individual browser and device circumstances. 
- Being able to apply uniquely targeted styles opens up more opportunities for responsive web design. 

#### Initializing Media Queries
- @media rule inside of an existing stylesheet (generally this method is recommended)
- @import rule imports a new styleshet
- linking to a separate stylesheet from within HTML doc
- Common media types include all, screen, print, tv, and braille
- if a media type not be specified the media query will default the media type to screen
- When a media feature and value allocate to true, the styles are applied. If the media feature and value allocate to false the styles are ignored.

#### Logical Operators in Media Queries
- Helps build powerful expressions
- 3 different operators:
    1. and: allows extra condition to be added
    2. not: negates the query, specifying any query but the one identified
    3. only: selects only the condition written in the expression
- When using the not and only logical operators the media type may be left off. In this case the media type is defaulted to all.

#### Media Features in Media Queries
- Media features identify what attributes / properties will be targeted within the media query expression

#### Height & Width Features
- May be found using the height and width media features. 
- Can also be prefixed with the min or max qualifiers, building a feature such as min-width or max-width.

#### Using Minimum & Maximum Prefixes
- min: indicates a values of greater than or equal to
- max: indicates a value of less than or equal to

#### Orientation Media Feature
- Orientation media feature determines if a device is in the landscape or portrait orientation
    1. Landscape mode: triggered when the display is wider than taller 
    2. Portrait mode: triggered when the display is taller than wider

#### Aspect Ratio Media Features
- The aspect-ratio and device-aspect-ratio features specifies the width/height pixel ratio of the targeted rendering area or output device.
- The min and max prefixes are available to use with the different aspect ratio features, identifying a ratio above or below that of which is stated.
- The value for the aspect ratio feature consist of two positive integers separated by a forward slash. 
    - The first integer identifies the width in pixels while the second integer identifies the height in pixels.

         `@media all and (min-device-aspect-ratio: 16/9) {...}`

#### Pixel Ratio Media Features
- Includes the device-pixel-ratio feature as well as min and max prefixes
- Great for identifying high definition devices, including retina displays

`@media only screen and (-webkit-min-device-pixel-ratio: 1.3),only screen and (min-device-pixel-ratio: 1.3) {...}`

#### Other Media Features
- Include identifying available output colors with use of the color, color-index, and monochrome features
- Include identifying bitmap devices with the grid feature
- Include identifying the scanning process of a television with the scan feature

### Mobile First
Includes using styles targeted at smaller viewports as the default styles for a website, then use media queries to add styles as the viewport grows.
- Downloading unnecessary media assets can be stopped by using media queries

### Viewport (Height and Width)
- Using the viewport meta tag with either the height or width values will define the height or width of the viewport respectively. 
- Each value accepts either a positive integer or keyword. 
- For the height property the keyword device-height value is accepted, and for the width property the keyword device-width is accepted. 

#### Viewport Scale
Properties
- minimum-scale: value should be a positive integer lower than or equal to the initial-scale (should always be a positive integer between 0 and 10)
- maximum-scale: value should be a positive integer greater than or equal to the initial-scale (should always be a positive integer between 0 and 10)
- initial-scale: should be set to 1 as this defines the ratio between the device height, while in a portrait orientation, and the viewport size (should always be a positive integer between 0 and 10)
- user-scalable: if value is set to 'no', it will disable any zooming. Setting it to 'yes' will turn on zooming. 

#### Viewport Resolution
- target-densitydpi value may be used
    - accepts values: device-dpi, high-dpi, medium-dpi, low-dpi, or an actual DPI number

#### Combining Viewport Values
- viewport meta tag accepts both individual values and multiple values -> allows multiple viewport properties to be set all at once
- requires a comma to separate them within the content attribute value

### Flexible Media
Images, videos, and other media types need to be scalable, changing their size as the size of the viewport changes.

#### Flexible Embedded Media
- Embedded element needs to be absolutely positioned within a parent element
- The parent element needs to have a width of 100% so that it may scale based on the width of the viewport
- The parent element also needs to have a height of 0 to trigger the hasLayout mechanism for IE
- Padding is given to the bottom of the parent element (the value is set in the same aspect ratio of the video)



