# Methods and Classes

// Optional arguments: define method and make some of the args optional by marking them equal to nil if no value is presented.

>> BAD
def tweet(msg, lat, long)

tweet("Tweet goes here", nil, nil)


>> GOOD: Add default with = 
def tweet(msg, lat = nil, long = nil)

def initialize(name, bal = 100)

set optional parameter: if no val is passed, it will be set to the default 100

// Option hash arg: but defaulting two values to nil is not idea. Use hash options instead.

def tweet(msg, options = {})
    status = Status.new
    status.lat = options[:lat]
    status.lon = options[:long]
    status.body - msg
end

def new_game(name, options = {})
 {
    name: name,
    year: options[:year],
    system: options[:system]
  }
end
Reference keys from hash

To call it:
tweet("sfsdfsdf",
    :lat => 23.22
    :long => 22.13
    :reply_id => 33333
)
    lat: 234,
    long: 234,
    id: 234
)

Can order them in anyway

// Raise Exceptions: Raise error if something is nil

raise Error unless name 

(will raise error if nil)

// "SPLAT" *
def mentions(status, *names)
 
*Several names into a list instead of an array.

// You need a class when...

class Name
    def initialize(first, last=nil)
        @first = first
        @last = last
    end
    def format
        [@last, @first].compact.join(',')
    end
end

user_names.each {|n| puts n.format }

You can re-open and change any class.

But be careful. May overwrite old fxn.

Only re-open classes you own

SELF