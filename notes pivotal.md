## What is a gem?

A gem is a self-contained package for Ruby code. 

## Gemsets

A self-contained bundle of gems that you load with RVM, Ruby Version Manager. Load a Gemset in your application to keep and specify your gems versions. 

## What’s in a gem?

gem/
    bin/
    lib/
    spec/
    README.md
    Rakefile
    your_gem.gemspec

your_gem.gemspec
    Name
    Platform
    version.rb - VERSION constant will define version number
bin/
    executable file, an OS command
lib/
    your_gem.rb
    your_gem/ gets added to $LOAD_PATH

## Big types of gems
Vendor gems - wrappers for jQuery libraries and CSS libraries. Deployed from Asset Pipeline.
Plug-in gem - No front-end functionality.
Engine gem - Has views