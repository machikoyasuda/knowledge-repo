## RVM: Ruby Version Manager

May need to deploy app with different versions of Ruby

Conflict between gems in different projects, esp. with Rails 2 and 3

// install different versions
rvm install 1.9.2

// use different versions
rvm use 1.9.2

irb

// switch back to syste
rvm system

// set default
rvm use 1.9.2-p180
               
// list:
rvm list #list rubies
rvm list gemsets #list gemset/rubies
rvm gem set list #list gem set for current ruby



## RVMRC: .rvmrc file

// Place .rvmrc file into root of project, have correct Ruby version and gems loaded

rvm ree@ree_projectname_
rvm jruby@jruby_project


// Create gemset 

rvm gem set create 'ree_project'

gem env gemdir
gem path isolated from the rest

tw

http://screencasts.org/episodes/how-to-use-rvm


http://cheat.errtheblog.com/s/rvm

// Check which rubies
rvm list known

// rvm notes
see what dependencies you should install

http://net.tutsplus.com/tutorials/why-you-should-use-rvm/