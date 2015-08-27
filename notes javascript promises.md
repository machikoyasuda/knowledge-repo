## Promises

1. Promises give us a way to deal with asynchronous code as an alternative to callbacks. 
2. Give you back a flow of control of order.
3. Error-handling

promise = asyncOperation();

promise.done(function() {
    /* all good */
});

promise.fail(function() {
    /* runs if something went wrong */
});

promise.always(function() {
    /* all good */
});

===

## Composed promise

A **composed promise** will run its handlers when all passed promises execute.

composedPromise = $.when(asyncFunctionOne(), asyncFunctionTwo());

http://martinfowler.com/bliki/JavascriptPromise.html

A jQuery deferred object or futures

===

## States

- "pending"
- "resolved" or "success"
- "failed"

function asyncOperation(){
    setTimeOut(function(){
        console.log('waits 5 seconds before this logs - it waits until pending is over');
    }, 5000); 
}

===

## Promises in the abstract

then()

var promise = asyncFunction() promise.then (onFulfilled, onRejected);

then() unwraps the function to see if it succeeded or failed and why.

==

## From callbacks to promises

readFile(function(err, data){
    if (err) return console.log(err);
    console.log(data);
})

var promise = readFile();

promise.then(console.log, console.error);

==

## Chaining and nesting

var promise = readFile();
var promise2 = promise.then(function (data) {
    return readAnotherFile();
}, function(err) {
    console.error(err)
    return readAnotherFile();
}}

promise2.then(console.log, console.error)

===

## Error handling in promises

JS (synchronous)

try {

} catch {

}

Ruby 

begin
rescue
end

JS (async with promises)

doThisAsync()
.then(doThatAsync)
.then(null, console.error)

Chain async tasks, then check for error.

- implicit exception: throw reference error
- explicit exception: throw new error

## Promises in the wild

promise.state();

http://wildermuth.com/2013/08/03/JavaScript_Promises

var $info = $("#info");

$.ajax({
    // Change URL to see error happen
    url: "/echo/json/",
    data: {
        json: JSON.stringify({
            "name": "someValue"
        })
    },
    type: "POST"
})
.then(function (response) {
    // success
    $info.text(response.name);
}, 
function () {
    // failure
    $info.text("bad things happen to good developers");
})
.always(function () {
    $info.append("...finally");
});

var $info = $('#info');

var promise = $.ajax();
insertSpinner();

function onFulfilled() {
  removeSpinner();
}

promise.then(aRequest);
.then(anotherRequest);
.then(anotherRequest);
.then(null, console.err);

http://jsfiddle.net/SwzkK/light/

var $info = $("#info");

function doWork() {
    return $.ajax({
        // Change URL to see error happen
        url: "/echo/json/",
        data: {
            json: JSON.stringify({
                "name": "doWork promise"
            })
        },
        type: "POST"
    });
}

var onFulfilled =  function(data) {
    $info.append(data.name);
}

var onRejected = function(error) {
    $info.append(error.statusText);
}

var onAlways = function() {
    $info.append(" on always");
}

var promise = doWork();
promise
    .then(onFulfilled, onRejected)
    .always(onAlways);

## Promise vs. Deferred

Promise: as yet unknown value
Deferred: 