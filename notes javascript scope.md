## scope

Entering a function changes the scope. When looking to resolve a variable name, Js works outwards from the innermost level. 

## global scope

function() {
    a = 3;
    alert(a);
}

is the same as

var a;
function() {
    a = 3;
    alert(a);
}

Because it was never specifically declared (using var),  it was assumed to be global. 

So, it uses the window object. This object is around for the entire lifetime of the page, and everything can access it, so it's perfect!