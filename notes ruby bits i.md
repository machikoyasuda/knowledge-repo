# Unless v. if/else
- Use if, if you need if/else
- Use Unless only with Unless
- Unless is a negative if

# Implied Nil: comparing something with nil is not needed in Ruby. Delete !=nil

- "" treated as true
- 0 treated as true
- [] treated as true
- nil is false

# Don't need != nil

>>BAD CODE 
if attach.file_path != nil
    attach.post
end

>>GOOD CODE
if attachment.file
    attach.post
end

# Use in-line if/unless: put if-statement at the end

>>BAD CODE
if pass.length < 8
    fail "Password too short"
end

>>GOOD CODE
fail "Password too short" if pass.length < 8

# Short-circuit "and" &&: Combine if-statements with &&. Do not nest two ifs.

>>BAD
if user
    if user.signed_in?
     # ...
    end
end

>>GOOD: 
if user && user.signed_in?
    #...
end

If user is nil, it won't run.

result = nil || 1 -> 1
result = 1 || nil -> 1
result = 1 || 2 -> 1

## Default values - "OR" ||

tweets = timeline.tweets
tweets = [] unless tweets

If nil, default to empty array:
tweets = timeline.tweets || []

# Short-circuit eval: clean up code 

def sign_in
    current_session || sign_user
end

Not evaluated unless current session is nil.

Or can do if/else if more readable

>> BAD
def search_index(games, search_term)
  search_index = games.find_index(search_term)

  if search_index
    search_index
  else
    "Not Found"
  end
end


>>GOOD
def search_index(games, search_term)
  search_index = games.find_index(search_term)
  search_index || "Not Found"
end


>>BETTER
def search_index(games, search_term)
  games.find_index(search_term) || "Not Found"
end

# Conditional assignment ||=

i_was_set = 1
i_was_set ||=2

puts i_was_set => 1

i_not_set ||=2
puts -> 2

search ||= "" means, set search to all, unless search is set already.


Set defaults, if nil:

>> BAD
options[:country] = 'us' if options[:country].nil?

>> GOOD
options[:country] ||= 'us'

# Conditional return value

>> BAD
if list_name
    options[:path] = "/#{user_name}/#{list_name}"
    else
    options[:path] = "/#{user_name}"
end

>> GOOD
options[:path] = if list_name
    "/#{user_name}/#{list_name}
else
    "/#{user_name"
end


>>BAD

search_index = games.find_index(search)
if search_index
  search_result = "Game #{search} found: #{games[search_index]} at index #{search_index}."
else
  search_result = "Game #{search} not found."
end

>>GOOD

search_result = if search_index 
  "Game #{search} found: #{games[search_index]} at index #{search_index}."
else
  "Game #{search} not found."
end

>> BETTER

eliminate search_result variable



When/Then

http://net.tutsplus.com/tutorials/ruby/ruby-for-newbies-conditional-statements-and-loops/

