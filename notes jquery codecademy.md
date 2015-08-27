jQuery interacts with DOM's parents, children, siblings. 

jQuery is a library of JavaScript, that's easier to manipulate DOM to create visual web effects.

What does jQuery do?

    .   Finding html elements
    .   Moving around a page's code
    .   Editing elements
    .   Making animations
    .   Making dynamic web sites

<script type="text/javascript" src="src"></script>

==========

# JavaScript v. jQuery

//javascript:
document.getElementById('myElement').style.display = "none";
//jquery:
$('#myElement').hide();


==========

A basic jQuery model 

$(document).ready(function() {
    $('thingToClick').event(function() {
    $(thingToAffect).effect();
    });
});

$() = function that turns whatever's inside the parentheses into a jQuery object

============

Define a jQuery function

var myFunction = function() {
    //do something;
}

============

var sayHello = function (){
        return("hello");
    };
    var multiplyThree = function(x,y,z){
        return(x*y*z);
    };

x = function(){alert('functional!')}

=============
- A function is a first class object
- I can pass, and reassign, x just like any other variable. This has the side effect that I can pass a function to a function.
- 
=============
- A callback is a specific example of a function being passed into another function, in case we want to execute.
- Synchronous: one event after another
- Asynchronous: one event responds to another event, action occurs only when the proper event tells it to (trigger event)
- scope of a function is the set of variables that it has access to.
- When you declare a variable with var, it is 'scoped' to the function that you are in.
- If no var, var is scoped to all.
- If a function is declared inside another function, the inner function can access variables in the outer.
=============


$().ready(); = a function of an event that will occur as soon as the HTML DOC is ready

; = end of command

# Function: basic unit of action 

put function inside ready -
function(){
    jQuery magic;
}

$(document).ready(function() {
    jQuery magic;
    });
    
- Always end in semicolon
- Function between {} and ()
- function(){}
- Convert HTML/DIV object into jQuery object with $('div')
- add .function()
- end with ;

# More on functions:
1. function
2. inputs between ()
3. actions between {}
4. ends with ;

function (input1, 2) {
    Do thing
    Do thing 2
}

# Assigning values
var $p = $('p');

# "this" 

- Use jQuery to convert HTML elements, classes, IDs into objects. Apply actions to them. 

// adding Classes

$(document).ready(function() {
    $('#text').click(function() {
        $(this).addClass('highlighted');
    });
});

// modify .css
.css("attribute", "property")

// modify .html
.html() can be used to set the contents of the first element match it finds.

// add html elements
.append()

'<div class="item">' + toAdd + '</div>'

$('.list').append("<div class='item'>" + toAdd + "</div>");

// grab value from form and set in variable
.val() is used to get the value of form elements.

var variable = $('input[name=fieldName]').val();


$(document).ready(function(){
    $("#button").click({
        var toAdd = $('input[name=checkListItem]').val();
    });
});

// .on
.on() as a general handler that takes the event, its selector, and an action as inputs.

$(document).on('event', 'selector', function() {
    Do something!
});

===

## Set-up:

// As soon as the document is ready

$(document).ready(function() {

// when thingToTouch's event happens, do function() to thingToAffect

    $('thingToTouch').event(function() {
        $('thingToAffect').effect();
    });
});

thingToTouch = or != thingToAffect

// for events right away: 

$(document).ready(function() {
    $('thingToAffect').effect();
});

## .addClass()

## .click()
## .hover()

## .fadeOut(), .fadeTo()

## .dblclick()
## .mouseenter()
## .mouseleave()

## .focus

## .keydown()
## .animate({direction: '#px'}, milliseconds)

$(document).ready(function() {
   $('div').animate({left:'+=10px'},500);
});
