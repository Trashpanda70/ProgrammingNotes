# Table of Contents

---

## Blocks
A *Block* is a code fragment (typically surrounded by curly braces) 
- Used as method parameters
	- EX: 
		- `.times` takes a block as a parameter
		- `.sort()` takes a block as an optional parameter

### Applying a Code Block with .Collect()
The `collect` method is an array method that takes a block as a parameter and applies the given code to every element of the array.
- Returns a *copy* of the array (original array is unchanged)
- Can modify the given array by using `.collect!`

If a given element is not able to be modified (like if conditionals are used to determine modification) then the element becomes `nil` 
- Elements will not remain unchanged if nothing happens
- Can prevent this using an `else` statement to return the variable passed
	- See example below

- `collect()` is aliased with `map()`
```rb
my_nums = [1, 2, 3]

new_nums = my_nums.collect { |num| num ** 2} # remember ** is exponent
puts new_nums # puts [2, 4, 9]
puts my_nums  # puts [1, 2, 3] since original array unchanged

my_nums.collect! { |x| x * 5}
puts my_nums # puts [5, 10, 15]

# collect using if statemnts
random_stuff = [1, "string", "yo", true, 5, "bruh"]
random_stuff.collect! { |element| 
	if element.is_a? Integer
		element * 2
	elsif element.is_a? String
		element.reverse
	end
}
puts random_stuff # puts [2, "gnirts", "oy", nil, 10, "hurb"]

# notice true got turned into nil because it was not able to be modified
# can fix using simple modification below:

random_stuff = [1, "string", "yo", true, 5, "bruh"]
random_stuff.collect! { |element| 
	if element.is_a? Integer
		element * 2
	elsif element.is_a? String
		element.reverse
	else
		element # since this will return the given variable
	end
}
puts random_stuff # puts [2, "gnirts", "oy", true, 10, "hurb"]

```

### Yield Keyword
Methods that accept blocks have a way of transferring flow of control from the method to the block (and back to the method again). 
- This can be done using the `yield` keyword in a user-defined method that takes a block
- Wherever `yield` is placed, the method trasnfers flow of control to the block, and when the block finishes, the method executes again

Note that any method can take a block as a parameter (it does not have to be explicitly stated)
- Only methods with a `yield` call will actually use the block
- A method that encounters a yield during runtime must have a block passed to it 
	- Will cause error if method without a block parameter encounters yield
- Can have optional yields (like in if-statements) to control when blocks should be passed/used

```rb
def yield_ex
	puts "in code block"
	puts "going to yield"
	yield
	puts "no longer yielding"
end
puts yield_ex { puts " >> in the block now"}
# puts the following:
#
# in code block
# going to yield
# in the block now
# no longer yielding
```

#### Yielding with Parameters
A method can take normal parameters along with a block parameter
- To use parameters in the passed code block, pass the parameters when calling `yield` as if it was a method
- Can use multiple parameters, and pass multiple parameters to the block (or not pass certain ones)
	- Update the parameters between pipes `||` in the block, method call, method header, and yield call
- Can also hard code a yield inside the method

```rb
# Display the info about someone a specified amount of times, defaults to 1
# The message to display is up to the caller
def yield_person(name, age, times=1)
	puts "INFO:"
	times.times {
		yield(name, age)
	}
	puts "End of Info"
end

yield_person("Joe", 30, 3) {|name, age| puts "My name is #{name} and I am #{age} years old" }
# puts:
#
# INFO:
# My name is Joe and I am 30 years old
# My name is Joe and I am 30 years old
# My name is Joe and I am 30 years old
# End of Info

yield_person("Bob", 20) {|name, age| puts "#{name} is #{age} right now"}
# puts: 
#
# INFO:
# Bob is 20 right now
# End of Info


# Hard Coded yield
def hard(name)
	puts "Gonna Yield"
	yield("Barry")
	yield(name)
	puts "kk done"
end

hard("Mike") {|n| "#{n} is cool." }
# puts:
#
# Gonna Yield
# Barry is cool.
# Mike is cool.
# kk done
```

## Procs
In Ruby "Everything is an Object" is not necessarily true
- Blocks are not objects
- Therefore, they cannot be saved to variables and reused

To keep code DRY (Don't Repeat Yourself), can use procs
- A Proc is a way to save a code block as an object

To define a proc, can use `Proc.new`
- If you want to assign the proc to a new proc, must use `Proc.new` again
- Without `Proc.new`, it would be like trying to assign it to a block (blocks are not objects)
- `Proc.new` takes 1 parameter, which is a code block
- Can use `do..end` or curly braces

Use `&` with the proc when passing it to a function that normally takes a block
```rb
# multiples of 3
multiples = Proc.new { |n| 
	n % 3 == 0
}
print (1..10).collect(&multiples) # prints [3, 6, 9]

multiples = Proc.new { |n| n = n*2 } # reassign to a new proc
print (1..5).collect(&multiples) # prints [2, 4, 6, 8, 10]
```

### Calling Procs Directly
Unlike blocks, it is possible to call procs directly
- This is done via the `.call` method
- Can have methods on a proc since procs are objects

The `.call` method can take parameters if the proc takes a parameter

```rb
# no parameter
hi = Proc.new { puts "Hi!"}
hi.call # puts "Hi!"

# parameter
hi = Proc.new { |x| puts "Hello #{x}!"}
hi.call("there") #puts "Hello there!"
```

### Using Symbols in Procs
Referencing the same mechanic as [[Hashes and Symbols#Checking Compatability with .response_to?|In the symbols notes]]
- Can convert symbols to procs using `&`
- Taking the symbol of a method name and using `&` allows the passing of that method as a proc
	- Syntax: `&:method_name`

The code below converts all members of an integer array to a string using this technique
```rb
numbers_array = [1, 2, 3, 4, 5]
puts numbers_array # [1, 2, 3, 4, 5]

# remember .map is an alias of .collect
# applies the code to all members of the array
strings_array = numbers_array.map(&:to_s)
puts strings_array # ["1", "2", "3", "4", "5"]
```
In the code above, the `to_s` method is being passed essentially as a block 
- Have the method name `to_s` and use `:` to get it as a symbol
- Use the `&` operator on the method name symbol to get that method as a proc



