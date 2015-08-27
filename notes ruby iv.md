## Modules

A toolbox that contains a set of methods and constants. Similar to classes, but without instances or subclasses. 

module ModuleNameCamelCase

## Namespacing

Separate methods and constants into named spaces

Double-colon :: scope resolution operator - tells Ruby where you are looking for a specific bit of code

Math::PI -> Look inside Math module to get PI (Not PI from a different module)

Module::Method or Constants

Modules cannot be instantiated, so we have to make new methods. Must define like:

def ModuleName.method(arg)

or

def self.method(arg)


## Require or Include

Use "require" to bring in new modules.

If you use "require" and "include", you pull in all methods and constants at instance level and do not need to use double-colon::scope resolution operator. 