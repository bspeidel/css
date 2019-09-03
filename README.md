# CSS & SASS coding style

This document defines formatting and style rules. It aims at improving collaboration and code quality.

## Terminology
![selector](/uploads/eb954a811742887ad12545cc50c69f22/selector.gif)
### Rule declaration
A “rule declaration” is the name given to a selector (or a group of selectors) with an accompanying group of properties. Here's an example:

`.listing {
  font-size: 18px;
  line-height: 1.2;
}`

### Selectors
In a rule declaration, “selectors” are the bits that determine which elements in the DOM tree will be styled by the defined properties. Selectors can match HTML elements, as well as an element's class, ID, or any of its attributes. Here are some examples of selectors:

`.my-element-class {
  /* ... */
}`

`[aria-hidden] {
  /* ... */
}`

### Properties
Finally, properties are what give the selected elements of a rule declaration their style. Properties are key-value pairs, and a rule declaration can contain one or more property declarations. Property declarations look like this:

`/* some selector */ {
  background: #f1f1f1;
  color: #333;
}`

for more information about CSS: https://www.w3schools.com/css/default.asp 

## CSS Validity
Use valid CSS where possible.

Unless dealing with CSS validator bugs or requiring proprietary syntax, use valid CSS code.

Use tools such as the W3C CSS validator to test: https://jigsaw.w3.org/css-validator/
<p>
<a href="http://jigsaw.w3.org/css-validator/check/referer">
    <img style="border:0;width:88px;height:31px"
        src="http://jigsaw.w3.org/css-validator/images/vcss-blue"
        alt="CSS Valide !" />
    </a>
</p>

## Class names
* Keep classes lowercase and use dashes (not underscores or camelCase). Dashes serve as natural breaks in related class (e.g., .btn and .btn-danger).
* Avoid excessive and arbitrary shorthand notation (.btn is useful for button, but .s doesn't mean anything).
* Keep classes as short and succinct as possible.
* Use meaningful names; use structural or purposeful names over presentational.
* Prefix classes based on the closest parent or base class.

## Variables

Prefer dash-cased variable names (e.g. $my-variable) over camelCased or snake_cased variable names. It is acceptable to prefix variable names that are intended to be used only within the same file with an underscore (e.g. $_my-variable).

> It's also useful to apply many of these same rules when creating Sass and Less variable names.

## Formatting
* Use soft tabs (2 spaces) for indentation.
* When using multiple selectors in a rule declaration, give each selector its own line.
* Put a space before the opening brace `{` in rule declarations.
* In properties, put a space after, but not before, the `:` character.
* Put closing braces } of rule declarations on a new line.
* Put blank lines between rule declarations.
* Use a semicolon after every declaration.
* Use single `''` rather than double `""` quotation marks for attribute selectors and property values.
* Use shorthand properties where possible.
* Put 0s in front of values or lengths between -1 and 1 (e.g., font-size: 0.8em;).
* Where allowed, avoid specifying units for zero-values (e.g., margin: 0).
* Use 0 instead of none to specify that a style has no border.
* Write detailed comments for code that isn't self-documenting (e.g., compatibility or browser-specific hacks).
* Use lowercase and shorthand hex values (e.g., #aaa).

### Bad
`@import "../main";`

`html {
  font-family: "open sans", arial, sans-serif;
}
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
.TEST {
  color: #FFFFFF;
  display: block;
  height: 100px
  margin: 0px;
}`

### Good
`@import '../main';`

`html {
  font-family: 'open sans', arial, sans-serif;
}`

`.avatar {
  margin: 0;
  border: 2px solid #fff;
  border-radius: 50%;
}
`

`.one,
.selector,
.per-line {
  // ...
}`

## Ordering of property declarations
1. display & flow 

2. position

3. dimension

4. margin / padding / border / outline

5. type of graphic style

6. background

7. opacity / cursor / generated/ content

8. transition

### Example
`  .product-icon {
    // 1.
    display: inline-block;
    visibility: visible;
    float: right;
    // 2.
    position: absolute;
    top: 82px;
    left: 50%;
    // 3.
    width: 100%;
    // 4.
    margin-right: auto;
    margin-left: auto;
    padding-top: 20px;
    padding-bottom: 0;
    border: 1px solid #333;
    border-radius: 3px;
    // 5.
    color: @icon;
    font-size: 12.4em;
    // 6.
    background-color: #333;
    // 7.
    opacity: 0.8;
    cursor: move;
    box-shadow: 1px 1px 10px #333;
    // 8.
    transform: translate(-50%, 0%);
  }`

## Nested selectors
Nested selectors, if necessary, go last, and nothing goes after them. Add whitespace between your rule declarations and nested selectors, as well as between adjacent nested selectors. Apply the same guidelines as above to your nested selectors.

`.btn {
  background: green;
  font-weight: bold;
  @include transition(background 0.5s ease);
// blank line
  .icon {
    margin-right: 10px;
  }
}`

Do not nest selectors more than three levels deep.

`.page-container {
  .content {
    .profile {
      // STOP!
    }
  }
}`

never nest ID selectors!

## ID selectors
While it is possible to select elements by ID in CSS, it should generally be considered an anti-pattern. ID selectors introduce an unnecessarily high level of specificity to your rule declarations, and they are not reusable.

For more on this subject, read CSS Wizardry's article on dealing with specificity: https://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/

## Editor preferences
Set your editor to the following settings to avoid common code inconsistencies and dirty diffs:

* Use soft-tabs set to two spaces.
* Trim trailing white space on save.
* Set encoding to UTF-8.

## Parting Words
Be consistent.

If you’re editing code, take a few minutes to look at the code around you and determine its style.

##### Tools
- stylelint: https://github.com/stylelint/stylelint
- stylelint config stantard: https://github.com/stylelint/stylelint-config-standard
- stylelint order: https://github.com/hudochenkov/stylelint-order
- stylelint rules: [stylelint-config](/uploads/f2b9bc659e54d2f7d7ed8314e7df61bc/stylelint-config.txt)

##### Source 
- The Idiomatic CSS Principles: https://github.com/necolas/idiomatic-css
- Google's CSS Style Guide: https://google.github.io/styleguide/htmlcssguide.html#CSS_Formatting_Rules
- Airbnb's Styleguide: https://github.com/airbnb/css#css
- mdo's Code Guide: http://codeguide.co/#css
