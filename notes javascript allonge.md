## Expressions and values: 

You give a computer an expression and it returns a value.

- All values are expressions. 
- Expressions consist of either representations of values (3.14, true, undefined), operators that combine expressions (3+2), some  special forms for creating arrays out of expressions, or function (arguments) { body statements } for creating functions.
- ("String" returns "String")

but 

- Not all expressions are values.
- ("String" + "String" is an expression that returns a value, but it itself is not a value.)

## Values and identity

We test whether two values are identical with === and !==.

There are two types of values with respect to identity: value types and reference types. Value types share same identity if they have the same content. Reference types do not.

1. Strings and numbers are different **types**, so they are never identical. (Two !== “two”)
2. Two values can have the same type, but different **content** - so they are not identical. (2 !== 5)
3. Strings, numbers and booleans (examples of *value or primitive types*) that have the same content and type are identical. (2 + 2 === 4)
4. Different reference types: Arrays and functions. ([1,2,3] !== [1, 2, 3])

"It's as if JavaScript is generating new cups of coffee with serial numbers on the bottom."

"Every time you evaluate an expression (including typing something in) to create an array, you’re creating a new, distinct value even if it appears to be the same as some other array value."

## undefined and void

Undefined is its own type of value, and it acts like a value type. It means no value.

Void is an operator that takes any value and evaluates to undefined. 

## Basic functions

Functions are values. Functions are also expressions.

Functions represent computation to be performed. Like numbers, strings and arrays, they have a representation. 

The simplest function: function () {}

(This is a function that is applied to no values and produces no value.)

A function is a reference type: (function () {}) === (function () {}) //=> false

### To write & apply a function with arguments:

1. Write the word function
2. Put arguments in ()
3. Put statements (expressions, other functions), separated by semicolons in {}. Use arguments.
4. To apply it, add (). Apply them to zero or more values, called arguments. 
5. To get a function to return a value when applied, use return. Return immediately terminates the function and returns the result of evaluating its expression. Return can accept any valid JavaScript expression (function, array, array of functions).

Example:

function (diameter) { return diameter * 3.14 } (2)
// => 6.26

Diameter is an argument. Apply the argument 2 as diameter.

### call by value & call by sharing

Any expression in the (argument) is applied first:

function (diameter) { return diameter * 3.14159265 })(1 + 1)
// => 6.28

1. JavaScript parses the whole thing as an expression made up of several sub-expressions. It starts to evaluate the expressions.
2. One of the sub-expressions evaluates to a function. Another evaluates to a number (1+1) into 2.
3. JavaScript now evaluates applying the function to the argument, which is 2.
4. An environment is created: the value ‘2’ is bound to the name (variable)  ‘diameter’ in the environment.
5. The expression ‘return diameter * 3.14’ is evaluated within this new environment.
6. The value of a  variable when evaluated in an environment is the value bound to the variable’s name in that environment, which is ‘2’. It evaluates the expression: 2 * 6.14.

Every time a function is invoked (applied), a new environment is created. An environment is a (possibly empty) dictionary that maps variables to values by name.

### call by sharing for reference types

When a value—any value—is passed as an argument to a function, the value bound in the function’s environment must be identical to the original. For value types (strings, numbers, booleans), copies are identical if they have the same content. So JavaScript makes copies of it for the function environment.

For reference type (arrays, functions), it places references to reference types in the environment, and when the value needs to be used, JavaScript uses the reference to obtain the original. Because many references can share the same value, and because JavaScript passes references as arguments, JavaScript can be said to implement ‘call by sharing’ semantics, understood to be a specialization of ‘call by value.’ 

## Variables: free or bound — Functions: closures or pure

- Functions containing no free variables are called pure functions
- Functions containing one or more free variables are called closures
- A pure function can contain a closure.

A free variable is one that is not bound within the function. 

A closure:

function (y) {
  return x 
}

A pure function that contains a closure:

function (x) {
  return function (y) {
    return x 
  }
}

- A pure function always means the same thing because all of their  inputs are fully defined by their arguments. Not so with closures.

### How are closures evaluated? What is their environment?

All functions are associated with an environment. For closure that is contained within a pure function, the closure’s environment is contained within the pure function’s environment (the parent environment). JavaScript always searches for a binding starting with its own function’s environment, and then each parent until it finds one.

If a variable has the same name as an ancestor’s environment’s bindings, it is said to shadow the ancestor. 

Currying a function:

function (x) {
  return function (y) {
    return function (z) {
      return x + y + z
    }
  }
} 

does the same thing as

function (x, y, z) {
  return x + y + z
}

Only you call it with (1)(2)(3) instead of (1, 2, 3). The other big difference is that you can call it with (1) and get a function back that you can later call with (2)(3). 

Calling a curried function with only some of its arguments is called a partial application.

## IIFE that binds values to names

**Functions as “first class entities.” Functions are values that can be bound to names like any other value, passed as arguments, returned from other functions, and so forth.
**

### The long way: With two environments

function (diameter) {
  return diameter * 3.14159265
}

function (diameter) {
  return diameter * Pi
}

(function (Pi) {
  return ????
})(3.14159265)

(function (Pi) {
  return function (diameter) {
    return diameter * Pi
  }
})(3.14159265)

(function (Pi) {
  return function (diameter) {
    return diameter * Pi
  }
})(3.14159265)(2)
  //=> 6.2831853

### Another way: With one environment

function (diameter, Pi) {
  return diameter * Pi
}

(function (diameter, Pi) {
  return diameter * Pi
})(2, 3.14159265)
  //=> 6.2831853

### Or, use var to bind a variable to a number:

function (diameter) {
  var Pi = 3.14159265;

  return diameter * Pi
}

(function (diameter) {
  var Pi = 3.14159265;

  return diameter * Pi
})(2)
  //=> 6.2831853

You can bind any expression. Functions are expressions, so you can bind helper functions:

### Using var to bind a variable with a function: 

function (d) {
  var calc = function (diameter) {
    var Pi = 3.14159265;

    return diameter * Pi
  };

  return "The circumference is " + calc(d)
}

function (d) {
  var Pi   = 3.14159265,
      calc = function (diameter) {
        return diameter * Pi
      };

  return "The circumference is " + calc(d)
}

These two examples use the var keyword to bind names in the *same* environment as the function. 

You can also create a new scope using an IIFE if you want to bind names within only one part of a function:

function foobar () {

  // do something without foo or bar

  (function () {
    var foo = 'foo',
        bar = 'bar';

    // ... do something with foo and bar ...

  })();

  // do something else without foo or bar

}

## Naming functions: named function expressions

The functions we dealt with above are ALL **anonymous functions.**

Even this is an anonymous function:

var repeat = function (str) {
  return str + str
};

It simply binds the word “repeat” to the function in an environment, but the function itself remains anonymous.

### Using var vs. using function names:

var bindingName = function actualName () {
};

**bindingName**: name in environment, a property of the environment

**actualName**: function’s name, not bound in the environment where we use that function — bound within the function itself, but not outside of it. useful for recursive functions.

bindingName
  //=> [Function: actualName]

actualName
  //=> ReferenceError: actualName is not defined

### Using function declarations:

function someName() {

}

Is a little bit like: binding a name in environment to a named function

var **someName** = function **someName** () {
  // ...
}

- Function declarations cannot exist inside any expression, otherwise, it is a function expression. Don’t put it inside parenthesis. 

## Higher-order functions

A JavaScript function that either takes functions as arguments or returns functions as values is a ‘higher-order function.’

# combinators

A combinator is:
- higher-order 
- pure function
- take only functions as arguments
- return a function

Compose (B Combinator)

function compose (a,b) {
  return function (c ) {
    return a(b(c )) 
  }
}

For example: if you have two named, pure functions:

function addOne (number) {
  return number + 1
}

function double (number) {
  return number * 2
}

With compose, you would write:

function doubleOfAddOne (number) {
  return double(addOne(number))
}

You could also write:

var doubleOfAddOne = compose(double, addOne);

Naming combinators: Combinators tend to name the functions with verbs or adverbs, avoiding nouns and keywords. They are useful when you want to emphasize what you are doing, rather than what you are working with.


# function decorator

A function decorator is:
- a higher-order function
- that takes one function as an argument
- returns another function
- and the returned function is a variation of the argument function
- does not have to be a pure function (can have non-mentioned args)

function something (x) {
  return x != null
}

function nothing (x) {
  return !something(x)
}

Or:

var nothing = not(something);

===

## Building blocks of functions

Learning a small number of simple patterns is useful so you can structure your code around some basic building blocks.

# composition

function cookAndEat (food) {
  return eat(cook(food)))
}

- chaining two or more functions together
- can use the B Combinator (compose)

function compose(a,b) {
  return function© {
    return a(b(c )))
  }
}

var cookAndEat = compose(eat,cook);

# partial application

- only providing some of the arguments for the function
- instead of a value, you get a function that represents part of the application

function mapWith (fn) {
  return function (array) {
    return _.map(array, fn)
  }
}

var squareAll = mapWith(function (n) { return n * n });

squareAll([1, 2, 3])
  //=> [1, 4, 9]

- partial application is orthogonal to composition

var safeSquareAll = mapWith(maybe(function (n) { return n * n }));

safeSquareAll([1, null, 2, 3])
  //=> [1, null, 4, 9]

===

## Arguments

Never use these words:
- this: the function’s context
- arguments: a list of a function’s arguments (an object)

===

## Summary

# functions
- functions are values that can be part of expressions, returned from other functions, passed as arguments
- functions are reference values
- functions are applied to arguments, passed by sharing - ‘pass by value’
- function bodies have zero or more expressions (statements)
- function application evaluates to the value of the last expression evaluated, or undefined.
- function application creates a scope. scopes are nested and free variable references closed over.
- variables can shadow variables in an enclosing scope.
- let is an idiom where we create a function and call it immediately in order to bind values to names.
- var is used to bind variables within a function’s scope.

================

## Recipe cheat sheet

# apply and call

Functions are applied with:
- ()
- .call
- .apply

function plus (a, b) {
  return a + b
}

plus(2, 3) 
  //=> 5
  
plus.call(this, 2, 3)
  //=> 5
  
plus.apply(this, [2, 3])
  //=> 5

# slice

Slice creates a new array:
- .slice(0) copies an array
- .slice(#) copies array from the 0th to the end
- .slice(#, ##) copies array from #+1 to ##

# concat

Concat returns an array created by adding receiver to argument.

[1, 2, 3, 4, 5].slice(1, 4)

# function lengths

Length counts the number of arguments declared.

function (a, b, c) { return a + b + c }.length
  //=> 3

## Recipes with basic functions

# Partial application recipe

Quickly apply a single argument, either leftmost or rightmost

var __slice = Array.prototype.slice;

function callFirst (fn, larg) {
  return function () {
    var args = __slice.call(arguments, 0);
    
    return fn.apply(this, [larg].concat(args))
  }
}

function callLast (fn, rarg) {
  return function () {
    var args = __slice.call(arguments, 0);
    
    return fn.apply(this, args.concat([rarg]))
  }
}

function greet (me, you) {
  return "Hello, " + you + ", my name is " + me
}

var heliosSaysHello = callFirst(greet, 'Helios');

heliosSaysHello('Eartha')
  //=> 'Hello, Eartha, my name is Helios'
  
var sayHelloToCeline = callLast(greet, 'Celine');

sayHelloToCeline('Eartha')
  //=> 'Hello, Celine, my name is Eartha'

As noted above, our partial recipe allows us to create functions that are partial applications of functions that are context aware. We’d need a different recipe if we wish to create partial applications of object methods.
