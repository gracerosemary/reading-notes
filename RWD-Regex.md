## [Grid Garden Game]([https://cssgridgarden.com/](https://cssgridgarden.com/))

Completed!

## [A Complete Guide to Grid]([https://css-tricks.com/snippets/css/complete-guide-grid/](https://css-tricks.com/snippets/css/complete-guide-grid/))

### Important Terminology:

- Grid Container: element on which `display: grid` is applied. It's the direct parent element of all the grid items.
- Grid Item: the children of the grid container.
- Grid Line: the dividing lines that make up the structure of the grid. Vertical → column grid lines. Horizontal → row grid lines.
- Grid Cell: space between two adjacent row and two adjacent column grid lines. It's a single unit of the grid.
- Grid Track: space between two adjacent grid lines. Think of them like the columns/rows of the grid.
- Grid Area: total space surrounded by four grid lines. It may be composed of any number of grid cells.

### Special Functions and Keywords

- sizing: `min-content`, `max-content`, `auto`, & `fr` → ex: `grid-template-columns: 200px 1fr 2fr min-content`
- function to set boundaries: to set a column to be 1fr, but shrink no further than 200px →  `grid-template-columns: 1fr minmax(200px, 1fr)`
- `repeat()` function: making 10 columns → `grid-template-columns: repeat(10, 1fr)`

## [Common Responsive Layouts with CSS Grid]([https://medium.com/samsung-internet-dev/common-responsive-layouts-with-css-grid-and-some-without-245a862f48df](https://medium.com/samsung-internet-dev/common-responsive-layouts-with-css-grid-and-some-without-245a862f48df)]

- images stretching out of proportion can be fixed by `object-fit: cover;` (but it causes cropping)

Demos: 

1. [Large image followed by articles]([https://grid-cats.glitch.me/](https://grid-cats.glitch.me/))
2. [The Full Page Image Gallery]([https://cat-grid.glitch.me/](https://cat-grid.glitch.me/))
3. [Card Layout]([https://card-layout.glitch.me/](https://card-layout.glitch.me/))
4. [The Holy Grail Layout (with no set heights!)]([https://grid-grail.glitch.me/](https://grid-grail.glitch.me/)]

## [Regex tutorial — A quick cheatsheet by examples]([https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285](https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285))

### Basic topics

Anchors — `^` and `$`

```jsx
^The        // matches any string that starts with The -> Try it!
end$        // matches a string that ends with end
^The end$   // exact string match (starts and ends with The end)
roar        // matches any string that has the text roar in it
```

Quantifiers — `*` `+` `?` and `{}`

```jsx
abc*        // matches a string that has ab followed by zero or more c 
abc+        // matches a string that has ab followed by one or more c
abc?        // matches a string that has ab followed by zero or one c
abc{2}      // matches a string that has ab followed by 2 c
abc{2,}     // matches a string that has ab followed by 2 or more c
abc{2,5}    // matches a string that has ab followed by 2 up to 5 c
a(bc)*      // matches a string that has a followed by zero or more copies of the sequence bc
a(bc){2,5}  // matches a string that has a followed by 2 up to 5 copies of the sequence bc
```

OR operator — `|` or `[]`

```jsx
a(b|c)     // matches a string that has a followed by b or c (and captures b or c) -> Try it!
a[bc]      // same as previous, but without capturing b or c
```

Character classes — `\d` `\w` `\s` and `.`

```jsx
\d         // matches a single character that is a digit 
\w         // matches a word character (alphanumeric character plus underscore)
\s         // matches a whitespace character (includes tabs and line breaks)
.          // matches any character
```

- \d, \w and \s also present their negations with \D, \W and \S

    \D will perform the inverse match with respect to that obtained with \d

    ```jsx
    \D         // matches a single non-digit character
    ```

    In order to be taken literally, you must escape the characters ^.[$()|*+?{\with a backslash \ as they have special meaning.

    ```jsx
    \$\d       // matches a string that has a $ before one digit
    ```

### Flags

- Placed at the end of the delimit slashes
- **`g`** (global): does not return after the first match, restarting the subsequent searches from the end of the previous match
- **`m`** (multi-line): when enabled `^` and `$` will match the start and end of a line, instead of the whole string
- **`i`** (insensitive): makes the whole expression case-insensitive (ex: **`/aBc/i`** would match **`AbC`**)

### Intermediate topics

Grouping and capturing — `()`

- Useful when extracting information from strings or data

```jsx
a(bc)           // parentheses create a capturing group with value bc
a(?:bc)*        // using ?: we disable the capturing group 
a(?<foo>bc)     // using ?<foo> we put a name to the group
```

### Bracket expressions — `[]`

All special characters lose their special powers so we do not apply the escape rule → escaping with a backslash

```jsx
[abc]            // matches a string that has either an a or a b or a c -> is the same as a|b|c 
[a-c]            // same as previous
[a-fA-F0-9]      // a string that represents a single hexadecimal digit, case insensitively
[0-9]%           // a string that has a character from 0 to 9 before a % sign
[^a-zA-Z]        // a string that has not a letter from a to z or from A to Z. In this case the ^ is used as negation of the expression
```

### Greedy and Lazy match

`* + {}` : greedy operators → expands the match as far as they can through the provided text

```jsx
<.+?>            // matches any character one or more times included inside < and >, expanding as needed
<[^<>]+>         // matches any character except < or > one or more times included inside < and >
```

### Boundaries — `\b` and `\B`

`\b` represents an anchor like caret (it is similar to `$` and `^`) matching positions where one side is a word character (like `\w`) and the other side is not a word character.

`\B` : negation → matches all positions where `\b` doesn't match and could be if we want to find a search pattern full surrounded by word characters. 

```jsx
\babc\b          // performs a "whole words only" search
```

### Back-references — `\1`

```jsx
([abc])\1              // using \1 it matches the same text that was matched by the first capturing group
([abc])([de])\2\1      // we can use \2 (\3, \4, etc.) to identify the same text that was matched by the second (third, fourth, etc.) capturing group
(?<foo>[abc])\k<foo>   // we put the name foo to the group and we reference it later (\k<foo>). The result is the same of the first regex
```

### Look-ahead and Look-behind — `(?=)` and `(?<=)`

```jsx
d(?=r)       // matches a d only if is followed by r, but r will not be part of the overall regex match 
(?<=r)d      // matches a d only if is preceded by an r, but r will not be part of the overall regex match
```

- Negation operator:

```jsx
d(?!r)       // matches a d only if is not followed by r, but r will not be part of the overall regex match 
(?<!r)d      // matches a d only if is not preceded by an r, but r will not be part of the overall regex match
```