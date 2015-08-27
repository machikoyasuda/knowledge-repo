## Mixins: Marriage of modules and classes

Mixin: A module is used to mix additional behavior and information into a class. Customize a class without having to rewrite code.

Multiple inheritance: mix trains in from other modules to make combinations of behaviors/classes

module Action
  def jump
  end
end

class Rabbit
  include Action
  end
end

Include: mix module's method at instance level (allowing instances of particular class to use methods)

Extend: mixes module's methods at class level, the whole class itself can use methods (not just the instances)

module Module
 def now
 end
end

class Class
 extend Module
end

Class.now