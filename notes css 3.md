*Responsive

*HTML: Don't forget ... />

<link rel="stylesheet" href="styles.css" />

- Elements, class, id, child http://coding.smashingmagazine.com/2009/08/17/taming-advanced-css-selectors/

- Style priority is determined by position in site -> external, head, inline, !important

- Style priority within external is determined by position in CSS, the latter will be prioritized

#IDs vs .Classes, ID *and* Classes
*Cascading list of selectors

*Universal selector = "*"

# CSS Selectors

Descendent selector (space)
Child selector >
Multiple selector ,

Pseudo-selector
:first, :last
:odd, :even


*Box model: margin, border, padding, content

*display: block (in a column), inline-block (in a row), inline (in same line, no dimensions, better for <p> or <h1> which are blocks by default), none (remove them entirely)

(div, p, ul, ol, li, h1-6) block by default, behave as though there is a line block before and after

(span, a em img strong), inline by default, do not generate line break

- How to horiz center block-lvl element? declare width, apply left and right margin of auto (margin: 0 auto;)

- Horiz center in, inline block (text-align: center;)

*margin: auto;
*margin-(r/l): (negative) => opposite; 

*float: right, left, none;

*clear: left, right, both;
- clearfix: add group class to container to clear floats

*position: static (default), absolute (manually position, take it out of flow / right, top), relative (more relative to where it would have landed if it just had default static / give it top or bottom), fixed (fixed in specifically place and stay regardless of scroll)

*z-index https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Understanding_z_index?redirectlocale=en-US&redirectslug=CSS%2FUnderstanding_z-index


*overflow (-x, -y): visible (default), auto (adds scrollbar), hidden (hides), scroll (auto scroll, no matter what)

*z-index: no z-index or equal index = overlap determined by placement

* make use of semantic elements
* name id/classes not by description but by practical functions
* remember alt/title tags
* separate content from style, never use inline styles within HTML
* continually refactor code

- The longer a selector is, chaining multiple elements together, the more work the browser has to do. Shorter chains = better performance 
- While applying a class to the targeted element may create more code within HTML it will render faster and remove any managing obstacles.
- Drop "px" for 0s

- Children inherit unless you override with nested selector (.class element)

- Specificity prioritizes selector: 0 (inline styles), 0 (# of ID), 0 (# of class), 0 (# of element selectors) : inline > id > class > element

- Recommended to keep the number of IDs you use to a minimum
http://screwlewse.com/2010/07/dont-use-id-selectors-in-css/

- Stay DRY: body text, container, comma delimit, keep shared elements in class and add sub-class with specific styles (ex: class = "class sub-class") (order matters: last in SS = what overrides)

font: 16px/18px bold italic sans-serif; /* size/line-height weight style family */
background: #000 url(image.jpg) no-repeat center top; /* color image repeat x-pos y-pos */
list-style: disc inside none; /* style position image */
margin or padding: 0 10px 0 10px / 0 10px 0 / 0 10px; /* top right bottom left / top right&left bottom / top&bottom right&left */
border: 3px solid #ccc; /* width style color */

- Layout: apply margin to all sections so if you remove element, it won't break layout

- Margin collapsing: takes the larger of the 2, not total of both (but doesn't work with float, rel/abs, padd/bord)

- Reset & normalize, have default styles for elements 

- apply .crop class and set overflow: hidden; to keep at same size without changing proportions / or set height: auto; / or to do vert photos, now do width: auto;

- best way to handle V and H photos is to scale img to become square

- img descriptions: add descriptive text to image replaced elements (text-indent: -9999px;) 

- img sprites: total height is double. use background-position: 0 -100px; to indicate which side of img sprite you want to use

.logo:hover, .logo:focus { background-position: x-axis change, y-axis change; } negative x is to left, positive x to right, negative y to bottom

defaults to 0, 0 

- Don't need second HTTP request if you have sprit. No preloading imgs necessary.

- base65 encoding for IE… 

- pseudo-classes (element: - conditionally select element based on state or position, always start with :colon, (:nth-child(even); :nth-child(odd)),  :nth-child(an+b) (2n = even, 2n+1 =  odd, 3n every 3rd, 4n + 4 every 4th starting with 4th)

:hover, :focus, :active, :visited

:first-child, :last-child, :only-child

:nth-child()
:nth-of-type()

- pseudo-elements p:last-child:after { content: '\2744'; }

:before
:after
:first-letter
:first-line

blockquote:before {
content: '';
}

p:first-child:first-line {



CSS3

/* border-radius for all */
-webkit-border-radius: #px;
-moz-border-radius: #px;
border-radius: #px;

  -webkit-border-top-left-radius: 1px;
  -webkit-border-top-right-radius: 2px;
  -webkit-border-bottom-right-radius: 3px;
  -webkit-border-bottom-left-radius: 4px;

  -moz-border-radius-topleft: 1px;
  -moz-border-radius-topright: 2px;
  -moz-border-radius-bottomright: 3px;
  -moz-border-radius-bottomleft: 4px;

  border-top-left-radius: 1px;
  border-top-right-radius: 2px;
  border-bottom-right-radius: 3px;
  border-bottom-left-radius: 4px;
}


/* text-shadow */

text-shadow: x-offset y-offset blur color;


/* box-shadow */
vendor prefix
box-shadow: inset x y blur color;

/* RGBa opacity */
color: rgba (r, g, b, .5);

/* HSLa opacity */
color: hsla (hue, sat, light, a)

/* opacity img or object */
opacity: 0.5;

/* transform */
-webkit-transform: scale(1.5);
-moz-transform: scale(1.5);
-o-transform: scale(1.5);
transform: scale(1.5) rotate(-2deg);

rotate(-2deg)
skew()
translate(x,y)

/* transition */
transition: all .2s ease-in-out;

ease, ease-in, ease-in-out, linear

transition: width 0.4s linear, background 0.3 ease;

/* gradient colors */
westciv.com/tools/gradients
-mox-linear-gradiation
-webkit-gradient

/* multiple bg parallax */
background:url no-repeat center top;
background:url repeat center top;

/* @font-face */
.OTF .TTF .WOFF 
TypeKit, Google web fonts, fonts.com

use FontSquirrel 

@font-face {
font-family: "League Gothic";
src: url(".ttf") format ("truetype");
}


/* forms */
#sign-up fieldset input[type="text"], #sign-up fieldset input[type="email] {


}

#sign-up input[type="submit"] {
cursor: pointer;
text-shadow: VP;
border-radius: VP;
background-image: CSS GRADIENT;
background-image: V;
}

#sign-up input[type="submit"]:hover {
box-shadow: VP;

}

.copyright {
background: url() left no-repeat;
opacity:;
transition: opacity .3s ease-in-out;
transition VP;

}

.copyright:hover {
opacity:.5;
}

FLUID: 
pixels --> ems
1em=10px, 
font-size: 16px;
font-size: 62.5%;






https://developer.mozilla.org/en-US/

http://learn.shayhowe.com/html-css/box-model

http://learn.shayhowe.com/html-css/organizing-data-tables

http://learn.shayhowe.com/advanced-html-css/performance-organization