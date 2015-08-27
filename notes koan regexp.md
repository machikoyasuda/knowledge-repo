## Regular Expressions

// /pattern/.class

test if Regexp

// "search string for"[/match/]

search a string for matching content and returns it

// "no matching"[/missing/] returns nil

// ? : optional
returns any/all

"abbcccddddeeeee"[/ab?/] > 'ab'
"abbcccddddeeeee"[/az?/] > 'a'

// + : one or more
returns any/all

"abbcccddddeeeee"[/bc+/] > 'bccc'

// * : zero or more
"abbcccddddeeeee"[/ab*/] > 'abb'
"abbcccddddeeeee"[/az*/] > 'a'

// first left-most match wins 
"abbccc az"[/az*/] > 'a'

// character classes give options for a character. they can include ranges

|a| a[/[options]at/]

[/[0-9]/]

O or P or T or I or N or S + (at)
animals = ["cat", "bat", "rat", "zat"]

animals.select { |a| a[/[cbr]at/] }

["cat", "bat", "rat"]

// \d : digital character
[/\d+/] -- search for any digits


// \s : whitespace