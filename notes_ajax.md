# Asynchronous JavaScript & XML

Asynchronous JavaScript allows us to do respond to events, without loading slowly in order.

Encapsulate a function. At a certain time after a certain event, the JS will load it.

## JSON: JavaScript Object Notation

- JSON text format is syntactically identical to JavaScript objects

Properties:
- plain-text
- self-describing
- hierarchical
- parsed by JavaScript
- can be transported with AJAX

{ key: value }

Data:
- key : value
- separated by commas
- {} holds objects
- [] holds arrays

## HTTP & AJAX

Create  - POST
Read    - GET
Update  - PUT
Delete  - DELETE


## jQuery.ajax

http://api.jquery.com/jQuery.ajax/

jQuery.ajax( url [, settings ] )

$ajax.('api/resumes') {
    complete: function(response)}

- accepts: 
- async: (default - true)
- cache (default - true)


## RESTful

Always has a endpoint, which is the end of the URL: url.com/api/

