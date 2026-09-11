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

*  ```css 
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

