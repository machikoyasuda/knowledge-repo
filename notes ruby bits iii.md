## Level 3: Classes

// Encapsulation: Classes are all about encapsulation.  

- Passing around data as strings & numbers breaks encapsulation
- Places using data need to know how to handle it
- Individual changes require updates at various places
* Create a class and variables to get around it

* Instead of passing "owner_id" into a method, create a class with variables (tweet.owner_id) into the method instead. 
* May not be worth the overhead of a class if all you have is data. A hash may suffice.

// Private

Declare methods private -- cannot be called with explicit receiver 

Hidden from outside but accessible from other instances of same class

// Inheritance

Do not duplicate code. Move duplicated code into a parent class so lower classes can inherit from it.

class Video < Attachment

If a method only makes sense in a subclass, only define it there.

// Super

Super(name) - look for method by the same name in a parent method

How can Super find it?

// Overriding methods

Instead of many case & when statements where one is more common than the others...

Set the more common one as the default and add a special handling subclass:

class Audio < Attachment
  def preview
    player
  end
end

// Hide instance variables

[var, @var, @var]

