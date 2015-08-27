// HTTP: HyperText Transfer Protocol

Clients (request info)
Servers (store or get info)

Client makes HTTP request and the Internet finds server that knows how to fill that request. Server sends response back to you. 

// REST: Representational State Transfer

# RESTful: Following REST  model - by clicking from page to page. 

# state transition: navigating by clicking links

// A RESTful API has:

1. Separate client from server
2. No data is held by server from request to request. No holding data b/w requests.
3. Use HTTP & methods


// Making API request

require 'open-uri' (module) 

variable = open('http://URL.com')
get = var.read[#, #]

puts get


// HTTP: 

GET (retrieve), 
POST (add), 
PUT (update), 
DELETE (delete)

// A HTTP request:

1. Request line (GET, POST, PUT or DELTE) + what it's looking for

2. Header (Sends server  info, like who the client is)

3. Body (GET leaves it empty or POST/PUT contains data)

# POST /codecademy/learn-http HTTP/1.1
# Host: www.codecademy.com
# Content-Type: text/html; charset=UTF-8

# Name=Eric&Age=26

// A HTTP Response

1. Status code

1xx - Got it.
2xx - Okay.
3xx - I can do it, but I have to do something first.
4xx - 404 error
5xx - Server goofed up & can't respond

"puts var.status

# HTTP/1.1 200 OK
# Content-Type: text/xml; charset=UTF-8

# <?xml version="1.0" encoding="utf-8"?>
# <string xmlns="http://www.codecademy.com/">Accepted</string>"

2. Header (More info)

3. Body (Text of response)


// XML: Extensible Markup Language - Make up your own tags

<pet>
  <name>Jeffrey</name>
  <species>Giraffe</species>
</pet>


require "rexml/document"

file = File.open("pets.txt")

doc = REXML::Document.new file

file.close

doc.elements.each("pets/pet/name" do |element|

puts element

end

// JSON: JavaScript Object Notation

{
  "pets": {
    "name": "Jeffrey",
    "species": "Giraffe"
  }
}

require 'json'

pets = File.open("pets.txt")

doc = ""

pets.each do |line|
  doc << line
end
pets.close

puts JSON.parse(doc)


// Endpoints: API-defined locations where data is stored 

//

URI: Uniform resource identifier
URL: Locator (location of thing)
URN: Name (name of thing)

Your browser replicates and creates a representation of the thing.

* Before: Actual hard-coded files
* Now: Servers generate files on the fly -- virtual directory structure -- but it's just a piece in a database that the website creates for you

## Controller:
- Tell your website what it should generate
- In Controller, write actions that create templates to dynamically make page

1. List:    Index       C   GET
2. Show:    Show(id)    M   GET
3. Create:  Create      C   POST
4. Update:  Update(id)  M   PUT
5. Delete:  Destroy(id) M   DELETE

7. New:     Form        Create GET
8. Edit:    Edit(id)    Update PUT

Create/Update/Delete redirects to Index or Show

GET /           List
GET /<id>       Show item with ID
POST/           Create a new item
GET/new         New form
PUT/<id>        Update item with ID
GET/<id>/edit   Edit form for ID
DELETE/<id>     Delete ID

* GET is nullipotent: it should not change anything in the server. Has no power. *Safe* methods

* PUT is idempotent: safely changes (updates) -- only happens once, you can repeat it without screwing things up

* POST: To hell with the POST! It's dangerous. 

###

Request-Response Cycle

Request URL
Request Method: GET
Status Code: 

## State Machine: A machine that can be in one or another state, but not both. A website is a state machine. Each page is a different state. When you click from one page to another, you are transferring states. A URL marks state changes and saves states. 

## FAT Clients:         ## DUMB:      
Browser does most work  Server works
Move processing to C    
Not as secure           More control

Use a FAT client and do what it takes to be secure.

### HATEOAS

Hypermedia as the Engine of the Application State

### REST

Representational State Transfer

Scalability makes REST possible.

* How do we get to it? Resources & URL
* Transfer them
* Manipulate them
* Delete them
* States: Maintain state w. Cookies: save info on user on their computer so it will remember states
* Stateless: What happens on client stays on client. Server forgets.
* Generalizability of interfaces: As long as there is a standardized way to talk to two things, we can insert new layers at any time. Allows you to scale. 

1. Client-server
2. Stateless
3. Cacheable
4. Layered
5. Uniform interface

Load-balancer: nginx

## SEPARATION OF CONCERNS ##

Each thing does what it supposed to do, and nothing else.

