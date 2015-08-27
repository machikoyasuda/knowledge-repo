# jQuery

What does it do:
1. Find - elements in HTML page
2. Change - HTML elements
3. Listen - to what user does and react accordingly
4. Animate - Content on page
5. Talk - over network to fetch new content

# DOM

DOM: Tree-like structure of HTML elements created by browsers so we can quickly find HTML elements using JS 

Parent, sibling & children elements become "nodes"

JavaScript gives developers language to interact with DOM

// $(document).ready(<event handler function>);

Ready method takes an event handler function as an arg.

// function () {
executing the function runs the code between the braces
}


# Selecting elements

.find(elements) with traversing

It takes more code, but it's faster. Specify selector and traversing element.

$("#id").find("element").first/last;

# Walking the DOM

$("li").first();
$("li").first().next().prev();

# Traverse up/down the DOM

$("li").first().parent();
$("#div").children("li");

Children only gets direct descendants, unlike find();

# Appending to DOM

.append
.appendTo
.prepend
.before
.after
.insertAfter
.insertBefore
.remove

# Watching for Click

.on('click', function () {
//run this code
});

# $(this)

this refers to the element that was clicked that triggered the next event

# Walk up the DOM to find the ancestor

/ $(this).closeset('.parent').append(thing);

# Adding data

Add HTML5 attribute 'data-name="xx"'

.data('name');
.data(name, value);

// var amount = $(this).closest('.vacation').data('price');

// var price = $('<p> From $'+amount+'</p>');

# On DOM Load

1. Set CSS display:none;
2. Find the element
3. Use:
- .slideDown()
- .slideUp()
- .slideToggle()

.on('event to watch for', 'element to watch', function to do)

* Don't add () at the end of the function, or it would execute immediately.


# JavaScript Debugging

alert("Hello"); +
$('button').length;

Fetch a DOM element using jQuery and call the .length to see how many nodes are on the page.

Combined:

$(document).ready(function() {
alert($('button').length);
};

# event Handler

function() {
}

# mouseEvents to listen to: 

.on()
- click
- focusin
- focusout
- mousedown
- mouseup
- mousemove
- mouseover
- mouseout
- mouseleave
- mouseenter
- dbclick

# keyboard & form events
.on()
- keypress
- keydown
- keyup
- blur
- select
- change
- focus
- submit

# Value
.val(newvalue);
.val()

var name = +(statement) turns string into number

# Fades
.fadeIn
.fadeTo
.fadeToggle();

# Preventing bubble ups:

event.stopPropogation();

event.preventDefault();

# Changing CSS

.css(attar, value)
.css(attr)
.css(object)

$(this).css(
{'attar': 'value', 
'attar': 'value'});

.addClass();
.removeClass();
.hasClass(class);
.toggleClass(class);

Pass in a JavaScript Object as an argument 

.show
.hide


# Advanced selectors

$('ol.economy-class li.row:first li:first a')

.html() - grab html
.text() - grab text only
.attr() - grab attribute within ()
.data() - grab data-attr
.show() - 

$('ol.economy-class li.row:eq(1) li:eq(3) a').attr('href')

element.class:eq(1) - first
element.class:eq(2) - second

# Classes
.removeClass
.addClass

# .bind()

.bind('click', selectSeat);

# .unbind();

Unbind so that clicking twice has no effect.

If you unbind, need to bind before that. Since you remove click handler from one, need to re-bind to previously clicked.

# delegate
$('div').delegate('a', 'click', doSomething);
