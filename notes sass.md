Pre-processor
Sass > Compiler > CSS

.scss
.sass
.css code is valid .scss code

// single-line comments

@import "file" ;
=> imported into .css & its own _name.scss 

nested selectors

.class {
    h1 {}
    p {}
    
}

.class {
    .another {
    (has class another w/i class .class .another)
    }
    &.another {
    (has both classes at same time: .class.another)
    }
    .another & {
    .another .class
    }
}

nested pseudoclasses, pseudoelements

a {
    color: #;
    &:hover{}
    &:active{}
    .users & {} (.users a)
}

nested properties 

.btn {
    text:  {
        decoration
        transform
    }
}

--  
Nesting is easy but dangerous. Check to make sure it is necessary. 

Limit nest to 3 or 4. 

--##Variables
Variables: booleans, numbers w/w/o units, colors, strings w/w/o quotes, lists with , or space, null;

$base: #777;

border: 1px solid $base;

$rounded: 3px !default;
(if a value isn't provided elsewhere, use by default)

@import "buttons";

Scope

Variables set within a declaration {} are not usable outside that block. Set new values to variables set outside block.

Changing it w/i declaration changes it globally.

Interpolation: #{$variable} into selectors, prop names, strings

$side: top;
sup {
    #{$side}: 0.4em;
}
.callout-#{$side} {
    color: #777;
}

--##Mixin: blocks of reusable code that take optional arguments. good for vendor prefixes

@mixin name{
    
}

.class {
@include name;
}

@mixin box-sizing($x) {
    -webkit: $x;
    -moz: $x;
    -o: $x;
    box-sizing: $x; 
}

.class {
    @include box-sizing(border-box);
    
}

@mixin box-sizing($x: border-box) {
(border-box if no arg is passed)
}

@mixin button($radius, $color: #000) {
    border-radius: $radius;
    color: $color;
    }
.btn-a {
    @include button(4px, #000);
    }
}

// Variable arguments for comma-sep

@mixin transition($val…)
    -webkit: $val;
    -moz: $val;
    transition: $val;

.btn-a {
    @include transition(color 0.3s ease-in, backround 0.5s ease-out);
}

// Var Arg in reverse

@mixin button($radius, $color) {
    border-radius: $radius;
    color: $color;
}

$properties: 4px, #000;

.btn-a {
    @include button($properties…)
}

// Interpolation

@mixin highlight($color, $side) {
    border-#{$side}-color: $color;
}

@include highlight(#fff, right);

## Extend

// Sass tracks and auto-combines selectors for us to make comma-delimited selectors

.btn-a {}

.btn-b {
@extend .btn-a;
}

turns into …
.btn-a, .btn-b {

}


Nested Extend

// %Placeholder selector

Never a selector of its own

%btn {
    }

.btn-a {
    @extend %btn;
    
    }
.btn-b {
    @extend %btn;
    }
    
%ir (html5 bp image replacement, group clearfix)

%group {
  zoom: 1;
  &:before,
  &:after {
    content: '';
    display: table;
  }
  &:after {
    clear: both;
  }
}

.factory {
  @extend %group;
  background: #fff;
}


4095 selector limit in IE

##Directive

// @function fluidize($target, $context) {
    @return: ($target / $context)
}

.sidebar {
    width: fluidize(250/1000);
}   

--

// $width * 9 / 16
@function aspect($width) {
  @return ($width * 9/16)  
}

.intro {
  background: #000;
  height: aspect(500px);
  width: 500px;
}


// @if, elsif, else

$theme: dark;

header {
    @if $theme == dark {
        background: #000;
    } @else if if $theme == pink {
        background: pink;
    }   @else {
        background: #fff;
    }
}

== equal to
!== not equal to
> greater than
>= greater than or equal to
< less than
<= less than or equal to

$size: 18px;

.switch {
  font-size: $size;
  @if $size <= 16px {
  font-family: Arial, sans-serif;
  } @else {
    font-family: Helvetica, sans-serif;
  }
}



// @each: iterate over a list

$authors: nick amy dan drew;
@each $author in $authors {
    .author-#{$author} {
        background: url(author-#{$author}.jpg);
        }

}

// @for: iterate over condition
.item {
    position: absolute;
    right: 0;
    @for $i from 1 through 3 {
        &.item-#{$i} {
            top: $i * 30px;
        }
    }
}

// @while: need to manually update i 

$i: 1;

.item {
    position: absolute;
    right: 0;
    @while $i <= 4 {
        &.item-#${i} {
            top: $i * 30px;
            }
        $i: $i + 2;
    }
}

--
odds

$i: 1;

@while $i <= 7 {
      .row-#{$i} {
      background: #ccc;
      height: $i * 10px;
    }
    $i: $i + 2;
}
// 

Mixin to define similar sets of properties used multiple times with small variations (vendor prefix)

Extend properties that match *exactly* (clearfix)

Fxns commonly-used operations to determine values (responsive, fluid)

//

Check if rounded-btn is true..

@mixin button($color, $rounded:false) {
    color: $color;
    @if $rounded {
        border-radius: $rounded;
    }
}

.btn-a {
    @include button(#000);
}

.btn-b {
    @include button(#333, 4px);
}

@mixin family($size) {
    font-size: $size;
  @if $size <= 16px {
    font-family: Arial, sans-serif;
  } @else if $size <= 24px {
    font-family: Georgia, serif;
  } @else {
    font-family: Helvetica, sans-serif;
  }
}

.switch {
  @include family(18px);
}

---

// % modulo - returns remainder of operation
12 % 5 -> 2

// / division - 

Variable: $size / 10
Paren: ( 100px / 20 )
Longer op: 20px * 5 / 2

// adding concatenating strings

"Helvetica " + "Neue"; // Helvetica Neue
'sans-' + serif // 'sans-serif'

// if units are different, sass attemps combination and conversion, unless imcompatible 

// pre-defined utilities:
round($number) - round up to whole
ceil($n) - round up
floor($n) - round down
abs($n) - absolute value
min($n) - min list value
max($n) - max
percentage($n) - convert to %

line-height: ceil(1.2);
width: percentage(350px/100px);

$context: 1000px;
width: percentage(350px/$context);

// color utility shortcuts & fxn

$color-base: #33333;
.add / $color-base + #111
.sub / - #111
.prod / * 2
.div / 2

Easier to use color utility fxn

rgba ($color,0.8) / converts 
rgba (#000, 0.8)

Workflow-altering convenience 

Remove need for PS to find slightly-altered colors

lighten($color, 30%);
darken($color, 20%);
saturate($color, 20%);
desaturate

mix(#fff, #eee);
mix(#, #, 20%);

grayscale($)
invert($)
complement($)

## Media queries - easier fluid calculation and query handling

// .sidebar {
@media (min-width:700px) {

}
}

// @contents - pass a block of properties to a mixin

@mixin respond-to($val, $query) {
// @if $media == tablet {
 @media ($val: $query) {
    @content;
    
    }
}

.sidebar {
    @include respond-to(max-width, 900px) {
    float: right;
    width: 30%;
}

--
Add @if and @else if

@mixin respond-to($media) {
  @if $media == desktop {
    @media (min-width: 960px) {
      @content;}
  } @else if $media == tablet {
    @media (min-width: 768px) {
      @content;}
  }
}

.factory {
  width: 100%;
  @include respond-to(desktop) {
    width: percentage(600px / 960px);
  }
  @include respond-to(tablet) {
    width: 50%;
  }
}



// Declarations outside @media cannot be extended inside…

// Can extend within same media query.

// Matching media queries cannot be combined. Sometimes manual is best. 



