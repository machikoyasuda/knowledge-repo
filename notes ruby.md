## For loops: when you know how many times you'll be looping

Exclusive range, (0...5)
Inclusive range, (0..5)

## Iterators: repeat an action 

/ Loop / method 

loop do
  i += i
  print "#(i}"
  break if i > 5
end

/ Next / keyword

/ For / keyword

for number in (0..5)
  puts number
end

/ Each / method

object.each { |item| # Do something }

object.each do |item| # Do something end

/ Iterate over array

The variable name between | | can be anything you like: it's just a placeholder for each element of the object you're using.each on.

array.each { |element| action }
order.each { |lunch| puts lunch }

/ new_Hash = Hash.new 
/ new_hash = { "one" => 1}

/ Iterate over hash

hash.each { |key, value| puts "#{key}:  #{value}" }

my_hash.each do |key, value|
  puts key, my_hash[key]
end


/ Add item to hash
words.each { |word| frequencies[word] += 1 }

/ New hash with symbols:

new_hash = { one: 1,
  two: 2,
  three: 3
}

/ .select to filter a hash for values that meet key/value criteria

good_movies = movie_ratings.select { |movie, rating| rating > 3}

/ .each_key
/ .each_value
my_hash = { one: 1, two: 2, three: 3 }

my_hash.each_key { |k| print k, " " }
# ==> one two three

my_hash.each_value { |v| print v, " " }
# ==> 1 2 3

/ Case statement
Instead of many if/elses, use case when you have a set number of options.

case 
  when
  when
  when
  else
end

/ SPLAT

 splat arguments. Splat arguments are arguments preceded by a*, which signals to Ruby: "Hey Ruby, I don't know how many arguments there are about to be, but it could be more than one."
 
def what_up(greeting, *bros)

// How blocks differ from methods

# method that capitalizes a word
def capitalize(string) 
  puts "#{string[0].upcase}#{string[1..-1]}"
end

capitalize("ryan") # prints "Ryan"
capitalize("jane") # prints "Jane"

# block that capitalizes each string in the array
["ryan", "jane"].each {|string| puts "#{string[0].upcase}#{string[1..-1]}"} # prints "Ryan", then "Jane"

Block does the same thing but you can't repeat it later

// Sorting with blocks

.sort! (! to change the actual array and re-write it)

/ Combined comparison operator
<=>

0 if first equals second
1 if first greater than second
-1 if first less than second

/ Ternary comparison  ? :
If Condition is true ? Then value X : Otherwise value Y

puts 1 < 2 ? "One is less than two!" : "One is not less than two."

