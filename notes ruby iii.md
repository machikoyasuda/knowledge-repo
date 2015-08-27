## classes

// creates class

class Name

  # boot-up object & require attribute
  
  def initialize(attribute) 
  
  # define attributes
  
    @attribute = instance var
    @attribute = instance var 2
end

// create object

me = Name.new("Attribute")

## variables 

// scope: context in which it is visible to the program

$global: available everywhere
::local: only certain methods
@@class: only certain class
@instance: only particular object

some methods are global, class-only, instance-only

// class methods: class method belongs to the class itself, and is prefixed with classname: Machine.hello (Class.method). 

use class method to grab @@class variable 

// $global variables

1. define variable outside of class/method

2. w/in class/method: start a variable with $

** $global can be changed from anywhere, but that's a bad idea **


// @@class variables: attached to entire class, not just instance

// @instance variable: belong to particular object (instance)

## inheritance: classes take on attributes or methods of another

is-a 

CartoonFox is a CartoonMammal
CartoonFox < CartoonMammal
DerivedClass < BaseClass
SubClass < SuperClass
Child < Parent

// declaring inheritance

< "inherits from"

def SubClass < SuperClass
end

// override: class that takes on methods/attributes of another and overrides them

Email < Message
  but send method in Email is more specific
  create send method in Email class and have it do all the work
  the NEW send will override the inherited send
  
Declare the class AGAIN in SubClass to overwrite SuperClass 

// un-override with super: use keyword to access attribute/method of superclass from inside a method

Ruby will look at superclass of current class and find a method with the snake name. It will use the superclass version.

**Only one SuperClass per class: No multi-inheritance**

// Semi-colon in Ruby: If you want to end a Ruby statement without going to a new line, use ;

class Monkey
end

=

class Monkey; end

## make methods private or public

Methods are public by default.

- public: allow classes/instances to interface with rest of program

can be called from outside

- private: unreachable by objects 

can only be called from inside 

// attributes

attr_reader: access method attributes (instance vars)

att_writer: change method attributes

attr_accessor: both read and write a variable

class Person
  attr_reader :name
  attr_writer :name
  def initialize(name)
    @name = name
  end
end

which equals to

def name
  @name
end

def name=(value)
  @name = value
end

*Use :SYMBOLS to pass @INSTANCE VARIABLES*

(That name= might look funny, but you're allowed to put an = sign in a method name. That's just a Ruby convention saying, "hey, this method sets a value!")
