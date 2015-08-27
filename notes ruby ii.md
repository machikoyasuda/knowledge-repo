## Blocks, Procs & Lambdas

# Blocks: A block of code that is executed with (do..end) or {}. Blocks are not objects. Blocks cannot be saved into variables.

[1,2,3].each do |num|
  puts num
end

[1,2,3].each { |num| puts num }

"collect" method: takes a block and applies the expression in the block to every element in an array

"collect!": mutates original array 

"collect" same as "map"

"yield" keyword: methods accept blocks using the yield keyword

# Procs: A "saved" block. 

// define a proc 
proc = Proc.new {|x| x ** 3 }

define a new Proc and pass in a block

// pass proc to a method: (&proc)

[1,2,3].collect!(&cube)

& converts proc into block

1. Procs are objects.
2. Procs can be called over and over without rewriting them. 

// call proc directly using .call

proc_name.call

// convert symbols (method) to procs 

strings = ["1", "2", "3"]
nums = strings.map(&:to_i)
# ==> [1, 2, 3]

Use map to apply method/symbol/proc &:to_i to each element in array

# Lambdas: similar to prods

A Lambda is a function without a name - anonymous. 

lambda { puts "Hello!" }
similar to
Proc.new { puts "Hello!" }

// define lambda

name = lambda { block }

- Lambda checks the # of args. Proc does not.
- When a Lambda returns, it passes control back to the calling method. When a proc returns, it immediately returns itself -- without going back to calling method.

// call lambda and pass into method




