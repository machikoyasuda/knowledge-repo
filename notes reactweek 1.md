JavaScript
=====

The hardest part about React is not React, it's JS.

Most other options like Angular and Ember provide some sort of remplating language for the UI portion of your code. In React, everything lives in JS, so no DSLs to learn.

Angular's ng-repeat or Handlebar's #each are "mapping" objects into list items.

var itms = assignments.map(function(assignment){
 return React.DOM.li({className: 'assignment'}, assignment.name);
});

* In React, you are using JS to .map, .filter, .reduce

* In JS, you'll need to deal with 'context', or rather, what the value of 'this' is.

* Scope is defined by the function that it is in.

* Context is determined at how the function is called, not determined at the function.

# What's the difference between .call and .apply?

.bind returns a new function, doesn't invoke immediately
.bind as a way to not have to create another new function to invoke the remove from

* .bind - allows us to ignore how a function is called, and instead force that context to be the object we want it to be. Then it doesn't matter how the fxn get called, the THIS will be the object that you bound it to in the fxn.

* => "fat arrow" 

* lexical this

* currying - pre-baking in arguments into a fxn so you have it later

Why React
=====
1. What is changing? (What state is there?)
2. Where is it mutated? (Where/When does it change?)

