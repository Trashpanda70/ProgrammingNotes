# Table of Contents:
[[#Basics of Ruby]]
- [[#Comments]]
- [[#Basic Console I O]]
- [[#Variables]]
- [[#Math]]
- [[#Strings]]

[[#Extra Notes]]
- [[#Methods that execute and assign]]
- [[#Curly Braces vs do end|Curly Braces vs do..end]]
- [[#Nil]]
- [[#Printing Strings and Arrays Uniquely]]
- [[#Converting Types|Converting Types and Float]]
- [[#Truthy vs Falsy]]
- [[#Conditional Assignment]]
- [[#Determining Class with is_a]|Determining Class with .is_a?]]

---

## Basics of Ruby
Ruby is generally used for web/Internet development, text processing, games, and is used in Ruby on Rails (A popular web framework)
- High level language
- Interpreted language: Code not compiled into machine code but run by another program
- Object Oriented: Everything is an object in Ruby, even though procedural programming is supported
- [Documentation](https://ruby-doc.org/)

#### Comments
- Use `#` for a single line comment
- Use `=begin` and `=end` for multi-line comments, each of which is on a separate line

```rb
# Single line comment

=begin
multi
line
comment
=end
```

### Basic Console I/O
**Console Output**
- `puts` - Prints the string or variable with a newline character at the end
- `print` - Prints the string or variable without a newline character at the end
	- Can take more than one parameter
	- ex: `print num` or `print num, " "` (for loops perhaps) or `print name, ": ", grade`
- `p` - Prints strings with quotation marks around them, other variables normally, includes a newline character 
	- Used for debugging

**String Interpolation**: Used to print other variables (like integers) within a string
- Similar to what is done in bash
- Use  `#{var_name}` inside the string

```rb
age = 21
puts "At time of writing I am #{age} years old"
```

**Console Input**
- Use `gets` for simple console input
- Ruby adds a new line after each bit of input automatically, to negate this use `gets.chomp`
	- The `chomp` method removes the new line

```rb
print "Enter age: "
age = gets.chomp
puts "You are #{age} years old"
```
### Variables
- Ruby variables do not need to have their type explicitly defined
	- Dynamically typed: Checks type during runtime rather than compile time
	- Strongly typed: Types can change during runtime
- NOTE: Ruby ***Does Not*** have post/pre increment/decrement (`++` and `--`)

#### Naming conventions
- Local variables start with a lowercase letter 
	- Use underscores to separate words (whole variable lowercase)
	- Could make variables start with capital, $, or @
		- Bad style

```rb
num = 25
my_bool = true
my_string = "words"
num = "twenty-five" #allowed
num = 25 
```

### Math
Generic 4 Math operations
- Modulo is still `%`
- Exponentiation is `**`
	- 4 ** 2 = 16
- Supports `+=` and similar operations
- Use `Math.sqrt(value)` for square root
- Again, **does not** support `++` and `--`

### Strings
Strings in Ruby can be single quotes `''` or double quotes `""`. There is no real performance impact between the two, but there are differences.
- Single quotes do not allow escape sequences (except the singe quote character itself)
- Single quotes do not allow **String Interpolation**
	- String Interpolation is how variables can be inserted into strings (cannot just use `+` like Java and some other languages)
	- Syntax for Interpolation is `"the string #{variable} continue the string"`
	- Interpolation will insert the value of the variable as if it were being printed (this includes things like arrays, not just integers)
- As a general rule, use single quotes if you need to print an exact string that double quotes might unintentionally interpolate or mark an escape sequence and use double quotes for everything else
	- Could also use double quotes and escape the `#` or `\` 
- For comparing strings use `==`
	- Can also compare strings using comparison operators to check for alphabetical order
- Can concatenate strings using the concatenation operator
	- `str1 << " " << str2 == str1 str2`
	- This operator can be used with assignment `<<=`
	- Can also be used for [[Arrays and Hashes#Array Methods|arrays]]
	- Operator works with variables

```rb
# Single quotes vs Double Quotes
puts 'Here is a\nNew line!' 
# Here is a\nNew line!

puts "Here is a\nNew line!" 
# Here is a 
# New line!

#Notice the syntax highlighting below
var = 5
puts '#{var} is a cool number'
# #{var} is a cool number
puts "#{var} is a cool number"
# 5 is a cool number

# String comparison
str1 = "yeah"
str2 = "ok"
if str1 < str2
	puts "#{str1} comes first!"
elsif str1 > str2
	puts  "#{str2} comes first!"
else
	puts "They are the same!"
end

# Concatenation
str1 = "ok"
str2 = "buddy"
puts str1 << " " << str2 # puts "ok buddy"
puts str1 << str1 << " wow " << str2 << "!" # puts okok wow buddy!

str1 <<= " wow " 
puts str1 << str2 # puts "ok wow buddy"
```

Strings have many methods to work with in Ruby by default
- `length` - length of the string
- `reverse` - reverse the string
- `upcase` - makes the string uppercase
- `downcase` - makes the string lowercase
- `capitalize` - makes the first letter capital and the rest lowercase
- `include?` - checks to see if the string contains the given substring
	- Syntax: *string_name*.include? "*substring to search for*"
	- ex: `my_string.include? "bruh"`
- `gsub(/s1/, "s2")` - replaces every instance of first string with second string
	- Stands for Global Substitution
	- s1 is between forward slashes, `/`, for reasons explained later
	- s2 is in quotation marks
- `concat(str)` - concatenates another string onto the string (other string specified by str)
- `split(delimiter)` - splits the string using the specified delimiter string. Returns an Array of split substrings
	- substring used can be more than a single character for delimiter
	- if two of the delimiters are next to each other (nothing in-between) then Ruby wil put a blank string for that spot in the array
```rb
my_string = "yo can i split"
my_arr = my_string.split(" ")
# my_arr is ["yo" , "can" , "i" , "split"]

str = "canyoIyosplityoyopls"
arr = str.split("yo")
# arr is ["can", "I", "split", "", "pls"]
```

## Extra Notes
Note that the notes below may use advanced topics from other sections without linking to them. This is just a place to store things for quick access that do not really fit into another category or is general use information.

---
##### Methods that execute and assign
Using an exclamation point will automatically assign the method return to the value of the String. (More on this in notes about methods)
- If a method takes parameters, the exclamation point comes before parenthesis

```rb
name = "matt"
# two below statements are the same
name = name.upcase
name.upcase!

#ex with parenthesis
lisp_speech.gsub!(/s/, "th")
```
---
##### Curly Braces vs do..end
Generally: do..end can be replaced by curly braces 

Below, the following two would do the same
```rb
keyword {
	# some code
}

keyword do 
	# some code
end
```
- This is used (and introduced) in the [[If-Statements and Loops#The Loop Method|Loop Method Notes]] 
- This does not apply unless both the `do` and `end` keywords are present
	- Does not work on if-statements, while loops, etc.

---
##### Nil
`nil` is the "empty object" in Ruby
- Equivalent to `null` in Java

When printed, `nil` will print as the empty string
- Cannot do `nil.method` as it is equivalent to doing `null.method` in Java

**Dereferencing Nil**
Seeing the message:  `undefined method 'method_name' for nil:NilClass` is essentially Ruby's version of a NullPointerException
- Means that you tried to do `nil.method_name` 

`nil` evaluates to false (similar to how NULL is false in C). So can do some neat things

```rb
# pretend theres some array arr that may or may not be nil
if arr
	#do stuff
end

return nil unless arr #return nil unless arr is not nil (return nil if arr is nil)
```

---
##### Printing Strings and Arrays Uniquely
- Since an index of -1 references the last element of an array, can do some cool tricks for printing them 
	- Under the hood, strings are character arrays. Because of this, can use array notation with Strings
	- For doing this remember: `..` is inclusive, `...` is exclusive (only for last index)

Examples:
```rb
str = "Ruby is Fun!"
arr = [1, 2, 3, 4, 5]

puts str[0] # puts "R"
puts str[-1] # puts "!
puts str[0..3] # puts "Ruby" - Remember 2 dots is inclusive
puts str[5...7] # puts "is" - Remember 3 dots is exclusive
puts str[5..-1] # puts "is Fun!" - Since -1 is last element and .. is inclusive

puts arr[1..-1] # puts [2, 3, 4, 5] (brackets and commas included)
puts arr[1...-1] # puts [2, 3, 4] (Since its exlusive)
puts arr[2..-2] # puts [3, 4]
puts arr[3..-3] # puts [] (If range is flipped nothing gets printed)
```

Obviously works for assignment too, not just printing

---
##### Converting Types
Ruby types are dynamic, but still cannot do certain things
- Cannot add a string to an integer
- Cannot concatenate an integer to a string

Can use certain methods to convert types
- `to_i` - Converts to an integer
	- EX: "5".to_i
- `to_f` - Converts to a float (no "double" type)
	- EX: "5.6".to_f
- `to_s` - Converts to a string
	- EX: 104.to_s

**Speaking of Float:**
- Just like Java, if one number is a float in a math expression, the whole thing gets converted to a float.
	- `puts 5/2` - puts 2
	- `puts 5/2.0` - puts 2.5
	- `puts 5/2.to_f` - Also works, puts 2.5

---
##### Truthy vs. Falsy
Truthy and Falsy are ways to describe what certain values evaluate to in a boolean expression
- If it is "truthy" then it will evaluate to true
- If it is "falsy" then it will evaluate to false

>Using C as an example:
>- 1 is truthy 
>- 0 is falsy, NULL is falsy

**In Ruby**
- `false` is falsy
- `nil` is falsy
- Everything else (including 0) is truthy
	- This is why you can do `if object` to check if an object is non-nil

---
##### Conditional Assignment
Can use the conditional assignment operator `||=` to assign a value to a variable only if it is nil
- If the variable is not nil, the assignment will not take place
- Can use it for first assignment when declaring a variable, but no need (just use default assignment)
```rb
favorite_language = nil

favorite_language ||= "Java" # value is now Java
favorite_language ||= "C" # value is still Java
favorite_language = "Ruby" # value is now Ruby

favorite_language = nil # value cleared to be nil
favorite_language ||= "English" # value is now English
```
---
##### Determining Class with .is_a?
- Can use the `.is_a?` method to determine what class an object is
	- Syntax: `obj.is_a? ClassName`
	- Notice there is no parenthesis
	- Returns a boolean

Examples
```rb
1.is_a? Integer # true
1.is_a? String # false

x=5.to_s
x.is_a? String # true
```
---
##### System Calls and CMD Commands
- Similar to `os.system` in Python and `exec*` in C, Ruby can run commands in terminal in multiple ways
- All commands run in the directory of the script

**System**
- Use `System( ... )` to run a command in the terminal
- Return is a boolean `true` if execution was successful, `false` if not

**Backticks**
- Use backticks to run a command similar to `System()` but the return will be the output of the command as a string

```rb
x = System("ls") # will print the result of ls to the console
p x # true

x = `ls` # still prints results of ls to the console
p x # prints results of ls again
p "x is string" if x.is_a? String # prints "x is string"
p "x is integer" if x.is_a? Integer # does not print
```