# CSS(Cascadiing Style Sheets)

**Searching system**

* It describes how HTML elements are to be displayed on screen, paper or in other media.

* It can control the layout of multiple web pages all at once.

* It defines design, layout, variations in display for different devices and screen sizes.

* css syntax has selector and declaration block;

- `h1 { color: blue; font-size:12px;}`

- selector points to html element we want to select
- declaration block contains css property name and value.

* selector = which element? | declaration = what styling?

# Selectors (Solve targeting problmes)

* which elements should be matched

* Simple selectors - based on name, id, class
`h1{}, .class-name{}, #id-name{}`

* combinator selectors - based on specific relationship between them

* Pseudo-class selectors - based on certain state

* Attribute selectors - based on attribute or attribute-value
`input[type="email"]{}`, `a[href^="https"]{}` ^= attribute value starts with...

**ID selector**

* As `id ` is unique within a page, used to style an unique elements.

* use `#id` to target an html element

**CLASS selector**

* To select a HTML element with a specif class attribute

* use `.class-name` to target an element

**Universal selector**

* selects all Html elements on the page

**Grouping selectors**

* same elements rather giving style individually, we can group it like this:
`h1,h2,h3 { color:blue; font-size:20px;}

**Combinator selectors**

* `.product p{}` means select the `<p>` inside the product class(Descendent combinator)

* `.product > p{}` means select only the direct child of class(Child combinator)

* `h2 + p{}` means select the `<p>` immediately after the `<h2>`(Adjacent Sibling)

* `h2 ~ p{}` means select all the `<p>` following after `<h2>`(General Sibling)

p
↓
"What type of element?"

.card
↓
"What class?"

#header
↓
"What unique identity?"

[type="email"]
↓
"What attribute/value?"

.card p
↓
"What's somewhere inside this?"

.card > p
↓
"What's directly inside this?"

h2 + p
↓
"What's immediately next to this?"

h2 ~ p
↓
"What siblings come after this?"


**Cascading Order**

* All styles in oage will *cascade* into a new *virtual* style sheet by following rules:

1. Inline style
2.External and internal style(order in head section)
3.Browser default

**COMENTS = /*comment line ignored by brower*/**

**CSS ERRORS**

* Missing semicolons `.h1{color:red background-color:yellow;}

* *Invalid property name & values* simply ignored by browser.


# Cascade & Specificity (ISS follow)

* order(highest leftmost applied)
    - inline {high}
    - id {w:100}
    - class {w:010}
    - element {w:001}
    - universal {w:000}

* Importance - is this rule specially marked as important

* specificity - how precisely this selector target the element

* Source order - if everything is equal, which rule came later

* ```css
  p {
    color: blue !important;
  }

  p {
    color: red;
  }
  ```

* The cascade resolves individual property declarations.

# Inheritance ( A fallback mechanism)

* parent element automatically pass thier computed value to descendants, when the child doesn't specify on its own.

* certain properties are inheritable but others don' like "border"

* Inheritance can travel through multiple levels of descendants.

Does this element have a CSS declaration?
        │
       YES
        ↓
   Use that value

       NO
        ↓
Is the property inherited?
        │
       YES
        ↓
Get value from parent

       NO
        ↓
Use property's default/initial behavior

* To explicitly request inheritance use
```css
.child {
    color: inherit;/* 'initial' to use browser default value defined by css*/
}
```

**note** : To establish shared properties high in the DOM tree.

# CSS UNITS(Relative to what?)

**Absolute units**

* **px** : commmonly used when need predictable dimensions like `border: 1px solid black;`

* It is a CSS pixel logical unit, not a one physcial hardware pixel.

**Relative units**

* **%** :  realtive to reference size defined for this property

* ```css
    .parent {
    width: 500px;
  }

  .child {
    width: 50%;
  }
  ```

* **em** : relative to fontsize of the relevant element/parent context(relevant containing/reference width)

* supose parent : 20px then child : 2em = 2 * 20 = 40px

* **rem** : root em `<html>` create a predicatble scale

* em -> content-dependent ; rem -> root dependant

* **vw** : if viewport width is 1000px then 1vw is 10 px, 1% of viewport width.

* **vh** : same as vw on height , 1%bof viewport height

# uses of css units

* px: when want predictable small dimensions usually for fixed sizes

* % : when an element sclae relative to its containing layout

* em : when sizing should scale with a component's local typography

* rem : Useful for consistent typography and spacing systems.

* vw: useful when respond to viewport width

* vh : useful when respond to viewport height

# Box Model

* It is used when talking about web design and layout.

* A box that wraps around every html element

* parts: 
  - content: content of box(texts / images)
  - padding: clears an area around the content, transparent
  - borders: a border that goes around the padding & content
  - margins: clears an area around the border, transprent.

  **To find total element width/height**

  * Total element width/height = width/height + left padding + right padding + left border + right border

  * To tell the browser the `width` is total width of box, we can use `box-sizing: border-box`

  * `content - box` : width= content ; `border-box` : width = content + padding + border

# Typography

* Controlling how text looks and how it occuoies space.

* font-family  → Which typeface?
    font-size    → How big?
    font-weight  → How thick? 400 normal value
    line-height  → How much vertical space? 1.5 * 16 = 24px
    web font     → Where does the typeface come from?

* **Web Font Integration** 

 - use when we want a font that isn't normally installed on user's computer.

 - two approaches: **Hosted font service** : include the font in body of HTML, so *browser downloads the required font and uses it to render the text.

 - **Host font ourself**
     * create a font file in project folder

     * use css to define it using `@font-face`

     ```css
     @font-face {
    font-family: "MyFont";
    src: url("./fonts/MyFont.woff2") format("woff2");#web oriented compressed font format
    }

    body {
    font-family: "MyFont", sans-serif;
    }
    ```

  * `text-decoration : line,style,color,thickness` 

  * `text-decoration : none,capitalize,uppercase,lowercase`

  * Text spacing : `text-indent`, `letter-spacing`, `line-height`, `word-spacing`, `white-space`

  background:

  * linear-gradient(direction, color1, color2)

  * radient-gradient(shape, color1, color2)

**Background images**

  * `background-image: url("image_url");

  * *problem* : How should image fit inside the element?

  * `background-size: cover`:if image large then element browser may crop it

  * `background-size: coontain`: scale the image to fit inside the element

  - cover   → fill box, cropping may happen
  - contain → show entire image, empty space may happen

  * *problem* : if image is cropped , which part should be visible?

  * `background-position : center` resolves it, 

  * Controlling which part of the oversized image remains visible

COLOR
│
├── What color?
│   ├── Hex
│   ├── RGB
│   └── HSL
│
└── Where?
    ├── Text → color
    └── Behind element → background-color

BACKGROUND IMAGE
│
├── What image?       → background-image
├── How big?          → background-size
├── Which part?       → background-position
└── Visual transition → gradient

# Display property

* Controls the basic layout behaviour of an element

* Decide between this element take its own row or sit beside other content

* `display: block` starts on new line; takes available horizontal space by default.Allows width,height, padding, border and margin

* `display: inline` elements participate in same line as surroundings text, can participate in line layout.

* `display: inline-block` it can sit beside other elements, but can also control width,height,padding,border,margin

* inline-block is especially useful in navigation

* `display:none` the element is not rendered as part of the layout

* **notes** : In `display: none` element doesn't occupy layout space, `visibility: hidden` still occupies layout space.

* block = Give me new row
  inline = let me be inside current line
  inline-block = let me stay in line, but treat me as more like a box.
  none = remove me from layout

# Flexbox

* One-dimensional layout system means flexbox primarily arranges along one axis at a time.

```css 
<div class="container">
<div>A</div>
<div>B</div>
<div>C</div>
</div>
```
  * .container becomes **flex container**
  * It's chidren A,B,C becomes **flex items**

* The main axis -> the directin in which the main items are layout.

* The cross axis - > which is perpendicular to main axis.

* `flex-direction` -> this controls the direction of the main axis

* `justify-content` -> acts based upo the main axis
  - center, flex-start, flex-end, space-between, space-around, space-evenly

* `align-items` -> acts based upon the cross axis

* `flex-wrap` to warp items responding to available space.

*  `flex: 1` each gets an equal share of the available flexible space

display: flex
→ "Parent, arrange my children using Flexbox."

flex-direction
→ "Which direction is my main axis?"

justify-content
→ "How should I distribute items on the main axis?"

align-items
→ "How should I align items on the cross axis?"

gap
→ "How much space should exist between items?"

flex-wrap
→ "Can items move to another line?"

**Flex-items can have following properties**

* order - specify the display order of flex items inside the container

* flex grow - specify how much an flex item can grow relative to the rest of flex items

* flex-shrink -  specify how much an flex item can shrink relative to the rest of flex items

* flex-basis - specifies the intial lenght of a flex item.

* flow is shorthnd property for above three


# Grid Box

* Grid is a 2 dimensional layout system used to arrange elements across both rows and columns.

* Here, we explicitly working with rows, columns and their intersection

*  Creating columns: 
```css
display: grid;
grid-tempelate-columns: 200px 200px 200px;
```

* here, we create 3 columns, each 200px wide

* 1fr = fraction of the available space, 3equal portions.

* `repeat()` 

```css
grid-template-columns: 1fr 1fr 1fr;
```
instead we write
`grid-template-columns: repeat(3, 1fr);`

* just like flex grids also support `gap:20px`

* To control rows we can use: ` grid-template-rows: 100px 200px;`

* so, it is called 2D layout system.

* **Grid lines** if we create 2 cols we have 3 vertical grid lines

* `grid-column: 1/-1`  the element will span over first line to last line.

## Where to use flex and Grid

* use **flex** when we care about how items are arranged along one axis.

* Use **grid** when the relationship between rows and columns matters.



# Positioning

* Used to controls where an element is placed and how it behaves relative to other elements or the viewport.

* CSS `position` property has:

  * `static`
  * `relative`
  * `absolute`
  * `fixed`
  * `sticky`

* Normal flow -> move an element -> remove it from flow -> attach it to viewport -> stick during scrolling

## **static** - stay in normal flow

* Default position of every element.

```css
.box {
    position: static;
}
```

* Element follows the normal document flow.

* `top`, `right`, `bottom`, `left` and `z-index` do not affect a static element.

## **relative** - stay in flow, but allow movement

* Element remains in the normal document flow.

```css
.box {
    position: relative;
    top: 20px;
    left: 10px;
}
```

* The element moves from its normal position.

* The original space of the element is still maintained.

* Important use of `relative` is to create a positioning reference for an absolutely positioned child.

```css
.parent {
    position: relative;
}

.child {
    position: absolute;
    top: 0;
    right: 0;
}
```

* Here `.child` is positioned relative to `.parent`.

## **absolute**

* Element is removed from the normal document flow.

```css
.child {
    position: absolute;
    top: 20px;
    right: 20px;
}
```

* It is positioned using `top`, `right`, `bottom`, and `left`.

* An absolutely positioned element is positioned relative to its nearest positioned ancestor.

* If there is no positioned ancestor, it is generally positioned relative to the initial containing block.

* Common use:

  * badge on image
  * close button
  * icon inside input
  * overlay


## **fixed** - attached to viewport

* Element is positioned relative to the viewport.

```css
.button {
    position: fixed;
    bottom: 20px;
    right: 20px;
}
```

* It stays in the same place even when the page is scrolled.

* Common use:

  * floating buttons
  * chat buttons
  * fixed navigation
  * back-to-top buttons


## **sticky**

* It behaves like a normal element until a scrolling position is reached.

```css
.header {
    position: sticky;
    top: 0;
}
```

* When the page is scrolled and the element reaches `top: 0`, it sticks to that position.

* It can move again depending on its containing area and scrolling context.

* Common use:

  * sticky header
  * sticky sidebar
  * table headings


```text

static    → normal position

relative  → normal position + can move

absolute  → removed from normal flow + positioned relative to ancestor

fixed     → attached to viewport

sticky    → normal position + sticks while scrolling
```

# Z-Index & Stacking Contexts

* `z-index` controls the stacking order of overlapping elements.

* It works along the Z-axis, which means which element appears in front of another.

```css
.box1 {
    position: relative;
    z-index: 1;
}

.box2 {
    position: relative;
    z-index: 2;
}
```

* `.box2` appears above `.box1` when they overlap.

* Higher `z-index` normally means the element appears above a lower `z-index` within the same stacking context.

* `z-index` does not mean "always appear above everything".

* Parent stacking contexts can limit how children are layered.

## **Stacking Context**

* A stacking context is an independent layering environment.

* Some CSS properties can create a new stacking context.

* Examples include:

  * positioned elements with a `z-index` value other than `auto`
  * `position: fixed`
  * `opacity` less than `1`
  * `transform` other than `none`

* Because of stacking contexts, a child with a very high `z-index` cannot necessarily appear above an element belonging to another higher stacking context.


# Responsive Design

* Responsive design means making a website adapt to different screen sizes.

* The same website should work properly on:

  * mobile
  * tablet
  * laptop
  * desktop

* Main goal is not to create separate websites for each device, but to make the layout adapt.

# Media Queries

* Media queries allow CSS rules to be applied only when a condition is true.

* If the  SCREEN/DEVICE matches this condition, apply these styles.

```css
@media (max-width: 600px) {
    .container {
        grid-template-columns: 1fr;
    }
    .menu {
        flex-direction: row;
    }
}
```

* Here the CSS inside the media query applies when the viewport width is `700px` or less.

* Common conditions:

  * `max-width`
  * `min-width`
  * `orientation`

## **max-width**

```css
@media screen and (max-width: 700px) {
    body {
        font-size: 14px;
    }
}
```

* Applies when screen width is 700px or smaller.

## **min-width**

```css
@media screen and (min-width: 1000px) {
    body {
        font-size: 18px;
    }
}
```

* Applies when screen width is 1000px or larger.

## **orientation**

```css
@media (orientation: landscape) {
    body {
        background-color: lightgray;
    }
}
```

* Applies when the viewport is wider than it is tall.

**breakpoint**

* A breakpoint should be chosen based on when your layout starts becoming uncomfortable or broken.


# Fluid Layouts

* Fluid layout means designing elements so they can adapt to the available space instead of depending only on fixed dimensions.

* **main idea** : Instead of giving elements a fixed size, allow them to grow and shrink according to the available space, while setting sensible limits.

* prevents overflow of layout in differnet screens.


* Fixed:

```css
.container {
    width: 1000px;
}
```

* This can create problems on a screen smaller than 1000px.

* Instead, we can use relative sizes and constraints.

## %

* using % will make the element size depends on it's parent.

## **max-width**

```css
.container {
    width: 100%;
    max-width: 700px;
}
```

* `width: 100%` allows the container to use available space.

* `max-width` prevents it from becoming too wide.


## **min-height**

```css
.container {
    min-height: 300px;
}
```

* Element should not become shorter than the specified value.


## **clamp()**

* `clamp()` allows a value to have a minimum, preferred and maximum value.

```css
h1 {
    font-size: clamp(24px, 5vw, 60px);
}
```

* Syntax:

```css
clamp(minimum, preferred, maximum)
```

* The value can grow with the viewport but cannot become smaller than the minimum or larger than the maximum.


## **min()**

* `min()` selects the smaller value.

```css
.container {
    width: min(90%, 1200px);
}
```

* This means the width will be whichever is smaller:

  * `90%`
  * `1200px`


## **max()**

* `max()` selects the larger value.

```css
.container {
    width: max(300px, 50%);
}
```

* The width will be whichever is larger:

  * `300px`
  * `50%`


## Fluid + Grid Pattern
```css
.container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
}
```

* here, the grid should be least 200px wide. If there is more space, it can take it.


# Transitions

* Transition creates a smooth change between two CSS states.

* Without transition, a property changes immediately.

```css
.button:hover {
    background-color: black;
}
```

* We can make the change smooth using:

```css
.button {
    transition: background-color 0.3s;
}
```

* Common transition properties:

  * `transition-property`
  * `transition-duration`
  * `transition-timing-function`
  * `transition-delay`

* Shorthand:

```css
.button {
    transition: background-color 0.3s ease;
}
```

* Example:

```css
.button {
    background-color: blue;
    transition: background-color 0.3s ease;
}

.button:hover {
    background-color: black;
}
```

* The button smoothly changes from blue to black.


# Animations

* CSS animations are used when an element needs to go through multiple stages of change.

* Transition - when the user hovers, smoothly changes from A -> B

* Animation - Run this sequence of changes automatically

* `@keyframes` defines the stages of the animation.

```css
@keyframes move {
    from {
        transform: translateX(0);
    }

    to {
        transform: translateX(100px);
    }
}
```

* Apply the animation:

```css
.box {
    animation: move 2s;
}
```

* Here:

  * `move` → animation name
  * `2s` → animation duration

* Unlike a simple transition, an animation can contain multiple stages.

```css
@keyframes example {
    0% {
        transform: translateX(0);
    }

    50% {
        transform: translateX(100px);
    }

    100% {
        transform: translateX(0);
    }
}
```

* `animation: spin 1s linear infinite;`

* animation:
    spin       → animation name
    1s         → duration
    linear     → timing function
    infinite   → iteration count

# Transforms

* `transform` changes the visual position, size or shape of an element without changing the normal document flow in the same way as layout properties.

* Common transform functions:

  * `translate()`
  * `rotate()`
  * `scale()`
  * `skew()`

## **translate**

* Moves an element.

```css
.box {
    transform: translate(20px, 10px);
}
```

* First value → horizontal movement.
* Second value → vertical movement.


## **rotate**

* Rotates an element.

```css
.box {
    transform: rotate(45deg);
}
```


## **scale**

* Increases or decreases the size visually.

```css
.box {
    transform: scale(1.2);
}
```

* `1` → original size
* `1.2` → 120% of original size
* `0.8` → 80% of original size


## **skew**

* Slants an element.

```css
.box {
    transform: skew(20deg);
}
```


## **2D and 3D transforms**

* 2D transforms work on horizontal and vertical dimensions.

* 3D transforms can also work with the Z-axis.

```css
.box {
    transform: rotateX(45deg);
}
```

## **transform-origin**

* Transformations generally happen around the center of the element 

* we can change that `transform-origin: top left;`.


*Note* : `transform` visually transforms an element after normal layout, without changing the space allocated to it in normal document flow.


# CSS Custom Properties (Variables)

* CSS custom properties are reusable values stored in CSS.

* **One sourceof truth -> many usages**

```css
:root {
    --main-color: #333;
    --spacing: 20px;
}
```

* Use the variable with `var()`.

```css
.header {
    background-color: var(--main-color);
    padding: var(--spacing);
}
```

* Main benefit is **reusability**.

* If the value needs to change, we can change it in one place.

```css
:root {
    --main-color: #333;
}
```

* Why **root** means, it refers to <html> so variables declared there are generally available throughout the page.

* **var()** means retrieve the variables's value.

* Not only for color, "reusable named value".

* CSS custom properties are inherited by default.f

* Instead of writing the same color many times:

```css
color: #333;
background-color: #333;
border-color: #333;
```

* We can use:

```css
color: var(--main-color);
background-color: var(--main-color);
border-color: var(--main-color);
```

* Variables can also be scoped to a particular element.

```css
.card {
    --card-color: blue;
    color: var(--card-color);
}
```


# Pseudo-Classes

* Pseudo-classes select an element based on its state or position.

* Syntax:

```css
selector:pseudo-class
```

## **:hover**

* Applies when the mouse is over an element.

```css
a:hover {
    color: red;
}
```

## **:focus**

* Applies when an element receives focus.

```css
input:focus {
    border-color: blue;
}
```

* Commonly used for form inputs.

## **:nth-child()**

* Selects an element based on its position among its siblings.

```css
li:nth-child(2) {
    color: red;
}
```

* This selects the second `li` that matches the structural condition.

## **Other common pseudo-classes**

```css
:first-child
:last-child
:checked
:disabled
:not()
```

* Pseudo-classes do not create new HTML elements.
* They allow us to target an existing element based on its state or position.


# Pseudo-Elements

* Pseudo-elements allow us to style a specific part of an element or create a generated cosmetic piece.

* Syntax:

```css
selector::pseudo-element
```

## **::before**

```css
.title::before {
    content: "★ ";
}
```

* Adds generated content before the element's content.

## **::after**

```css
.title::after {
    content: "";
    display: block;
    width: 50px;
    height: 2px;
    background-color: black;
}
```

* Adds generated content after the element's content.

* `::before` and `::after` commonly require the `content` property.

## **Other common pseudo-elements**

```css
::first-letter
::first-line
::selection
```

* Pseudo-elements are mainly useful for visual/cosmetic effects without adding extra HTML elements.

---

# Pseudo-Class vs Pseudo-Element

* **Pseudo-class** → selects an element based on its state or position.

```css
button:hover
li:nth-child(2)
input:focus
```

* **Pseudo-element** → targets a part of an element or creates generated content.

```css
p::first-letter
.title::before
.title::after
```


# CSS Architecture

* As a project becomes larger, CSS can become difficult to maintain.

* Problems can happen when:

  * class names are unclear
  * styles affect unintended elements
  * the same styles are repeated
  * changing one component breaks another component

* CSS architecture means organizing CSS so that it is:

  * reusable
  * predictable
  * maintainable
  * easier to understand

# BEM

* BEM stands for:

```text
Block
Element
Modifier
```

* It is a naming methodology used to organize CSS classes.

## **Block**

* A block is an independent component.

```html
<div class="card">
</div>
```

```css
.card {
    padding: 20px;
}
```

* `card` is the block.

---

## **Element**

* An element is a part of a block.

```html
<div class="card">
    <h2 class="card__title">Laptop</h2>
    <p class="card__description">Good laptop</p>
</div>
```

* Naming pattern:

```text
block__element
```

Examples:

```text
card__title
card__description
card__button
```


## **Modifier**

* A modifier represents a different state or variation of a block or element.

```html
<div class="card card--featured">
</div>
```

* Naming pattern:

```text
block--modifier
```

Examples:

```text
card--featured
button--large
button--disabled
```

* The original block can still be used together with the modifier.

```css
.card {
    padding: 20px;
}

.card--featured {
    border: 2px solid blue;
}
```

* Here:

```text
card
↓
base component

card--featured
↓
variation of the component
```

# BEM Naming Example

```html
<div class="product-card product-card--featured">

    <h2 class="product-card__title">
        Laptop
    </h2>

    <p class="product-card__price">
        ₹50,000
    </p>

    <button class="product-card__button">
        Buy Now
    </button>

</div>
```

* `product-card` → Block

* `product-card__title` → Element

* `product-card__price` → Element

* `product-card__button` → Element

* `product-card--featured` → Modifier

* BEM helps prevent unclear class relationships and makes CSS easier to maintain as the project grows.

# Preprocessors & Frameworks

CSS preprocessors and frameworks help us to write and manage CSS more easily, especially in large projects.

Examples:

- **Sass** → CSS Preprocessor
- **Tailwind CSS** → Utility-first CSS Framework

---

# 1. CSS Preprocessor

A CSS preprocessor allows us to write CSS with some extra features.

It converts the code into normal CSS before the browser uses it.

```text
Sass / SCSS
    ↓
Compiler
    ↓
CSS
    ↓
Browser
```

Browser does not directly understand Sass.

---

# 2. Why use CSS Preprocessors?

Normal CSS is enough for small projects.

In large projects we may have:

- Many CSS rules
- Repeated values
- Large stylesheets
- Many components
- Difficult maintenance

A preprocessor gives features which help us organize and reuse CSS.

---

# 3. Sass

**Sass** means **Syntactically Awesome Style Sheets**.

Sass is a CSS preprocessor which provides features like:

- Variables
- Nesting
- Mixins
- Functions
- Modules

Sass commonly uses `.scss` files.

---

# 4. Sass Variables

Variables are used to store values and reuse them.

```scss
$primary-color: blue;
$border-radius: 8px;

.button {
    background-color: $primary-color;
    border-radius: $border-radius;
}

.card {
    border-radius: $border-radius;
}
```

Instead of writing the same value many times, we can store it once and reuse it.

---

# 5. Sass Nesting

Sass allows us to write selectors inside another selector.

```scss
.navbar {
    background-color: black;

    a {
        color: white;

        &:hover {
            color: yellow;
        }
    }
}
```

It helps us keep related styles together.

But too much/deep nesting can make CSS difficult to maintain.

---

# 6. Sass Mixins

A mixin is a reusable group of CSS declarations.

```scss
@mixin center {
    display: flex;
    justify-content: center;
    align-items: center;
}

.container {
    @include center;
}

.card {
    @include center;
}
```

Mixins help to avoid repeating the same CSS.

---

# 7. Sass Functions

Sass can be used for calculations and reusable operations.

```scss
$base-size: 16px;

.title {
    font-size: $base-size * 2;
}
```

Compiled CSS:

```css
.title {
    font-size: 32px;
}
```

---

# 8. Sass Files and Modules

Large projects can divide styles into multiple files.

```text
styles/
├── _variables.scss
├── _buttons.scss
├── _navbar.scss
└── main.scss
```

Modern Sass uses `@use` to use modules.

```scss
@use "variables";
@use "buttons";
```

This helps organize large CSS projects.

---

# 9. Sass vs CSS Variables

Sass variable:

```scss
$primary-color: blue;
```

CSS custom property:

```css
:root {
    --primary-color: blue;
}
```

Main difference:

```text
Sass variable
→ Used during compilation/build time

CSS variable
→ Exists in browser at runtime
```

CSS variables can also be changed dynamically.

---

# 10. CSS Framework

A CSS framework provides ready-made styles, utilities or components which help us build UI faster.

Examples:

- Bootstrap
- Tailwind CSS
- Bulma

Instead of creating every style from scratch, we can use the framework's utilities or components.

---

# 11. Tailwind CSS

Tailwind CSS is a **utility-first CSS framework**.

It provides small utility classes for styling.

```html
<button class="bg-blue-500 text-white px-4 py-2 rounded">
    Submit
</button>
```

Conceptually:

```text
bg-blue-500 → background color
text-white  → text color
px-4        → horizontal padding
py-2        → vertical padding
rounded     → border radius
```

We combine these utilities to create the required UI.

---

# 12. Why Utility-first?

A utility class performs a small styling job.

For example:

```text
flex
→ display: flex

text-center
→ text-align: center

font-bold
→ font-weight: 700
```

So instead of creating a custom CSS class for every component, we can combine utility classes.

---

# 13. Tailwind Responsive Design

Tailwind provides responsive variants.

```html
<div class="text-sm md:text-lg">
    Hello
</div>
```

```text
Small screen
→ text-sm

Medium screen and above
→ md:text-lg
```

Example:

```html
<div class="flex flex-col md:flex-row">
```

Default:

```text
flex-direction: column
```

Medium screen and above:

```text
flex-direction: row
```

---

# 14. Tailwind States

Tailwind also provides state variants.

```html
<button class="bg-blue-500 hover:bg-blue-700">
    Submit
</button>
```

`hover:` applies the style when the element is hovered.

Other examples:

```text
hover:
focus:
active:
disabled:
```

---

# 15. Tailwind and CSS

Tailwind does not mean we don't need to understand CSS.

For example:

```html
<div class="flex items-center justify-between">
```

This represents CSS concepts such as:

```css
display: flex;
align-items: center;
justify-content: space-between;
```

So understanding CSS fundamentals is important before using Tailwind.

---

# 16. Sass vs Tailwind CSS

| Sass | Tailwind CSS |
|---|---|
| CSS Preprocessor | CSS Framework |
| Extends CSS | Provides utility classes |
| Uses SCSS/Sass files | Mainly uses utility classes |
| Variables, nesting, mixins | Responsive/state utilities |
| Helps organize CSS | Helps build UI faster |

### Simple difference

```text
Sass
↓
Helps us write and organize CSS better

Tailwind
↓
Helps us build UI faster using utility classes
```

---

# 17. What happens behind the scenes?

### Sass

```text
SCSS
 ↓
Sass Compiler
 ↓
CSS
 ↓
Browser
```

### Tailwind

```text
HTML / Templates
 ↓
Tailwind build process
 ↓
Generate CSS
 ↓
Browser
```

In the end, the browser uses CSS.

---

# 18. When to use?

### Sass

Useful when:

- Project has a lot of custom CSS
- We need reusable CSS logic
- We want to organize CSS into multiple files
- Team already uses Sass

### Tailwind

Useful when:

- We want to build UI quickly
- We prefer utility-first styling
- We need responsive utilities
- We work with component-based frameworks like Vue or React

For small projects, normal CSS may be enough.

---

# 19. What I should remember

```text
Sass
→ CSS Preprocessor
→ Adds features like variables, nesting and mixins
→ Compiles into CSS

Tailwind CSS
→ Utility-first CSS Framework
→ Provides utility classes
→ Helps build UI faster

Browser
→ Ultimately understands CSS
```

### Main difference

> **Sass changes how we write and organize CSS, while Tailwind helps us build UI using utility classes.**

