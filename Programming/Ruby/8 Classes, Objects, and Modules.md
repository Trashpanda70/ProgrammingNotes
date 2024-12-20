
# Table of Contents
[[#Basics of Classes]]
- [[#Variable Scope]]
- [[#Readers, Writers, and Accessors]]
- [[#Inheritance]]
[[#Modules]]


---

## Basics of Classes
Everything in Ruby is a class (almost everything, as mentioned [[7. Blocks, Procs, and Lambdas#Blocks|blocks are an exception]]) 
- Objects are created using `ClassName.new`
	- Already seen this with `Hash.new` and `Proc.new`
	- When creating classes, a `new` method does not need to be made. Instead, make a method called `initialize` to act as a constructor
	- A class does not need an `initialize` method technically, but it does to properly use parameters on creation
	- Can have multiple `initialize` methods for different parameter numbers
	- 
Basic form of a class is below:
```rb
class ClassName
	# stuff in class
end
```

### Variable Scope
Classes can define multiple different kinds of variables:
1. **Global Variables:** Globally accessible everywhere in the program. 
2. **Local Variables:** Normal variables only visible inside a certain method / block. Like local/auto variables in Java/C
3. **Class Variables:** Variables that belong to the class and are accessible in the file declared in. Like static variables in Java. 
4. **Instance Variables:** Fields of a class, belonging to a particular instance

The variables can be declared with the following:
- Note that any variable declared outside a class / method is global. This showcases a way to declare global variables from inside a class.
- For global variables, they must be referenced with a `$` everywhere they are used (if defined with a `$` in the first place)
- For class and instance variables, they must be referenced with `@@` and `@` respectively every time they are referenced in the class
	- This restriction does not apply with referencing a class' methods outside the class
```rb
class Variables
	$global_var = "Im a global variable"
		
	# could add a parameter for local_var by putting "local_var" (no quotes) in parenthesis by initialize
	def initialize
		@local_var = "Im a local variable"
	end
	def get_local_var
		@local_var
	end
	
	@@class_var = "Im a class variable"
	def get_class_var
		@@class_var
	end
end	

puts $global_var # global, so no need to refer to class
puts Variables.get_class_var # belongs to the class
puts Variables.new.get_local_var #need an instance
```

Note that this means that it is possible to make a variable with only 1 instance (similar to Java static) that is shared among all classes.
- This uses a class variable - declared using `@@`

With this, it is possible to create a variable to keep up with information that the scope of a single instance is incapable of tracking, such as the number of instances of a class.
- Code below has a class variable track the number of instances

```rb
class Tracker
	@@count = 0
	def initialize(id)
		@id = id
		@@count += 1 # add 1 each time a Tracker is made
	end
	def count
		@@count
	end
end

Tracker.new(1)
Tracker.new(2)
Tracker.new(7)
puts Tracker.count # puts 3
```

### Readers, Writers, and Accessors
Previously, in order to get a field we needed a method with the field name (or a different name, but that is less convenient) that simply returned the field due to access issues.

If we wanted to set the field, we would need a method like the one below.
- To see more on this go to [[1. Miscellaneous Information#Setter Methods|notes on setter methods]]
```rb
def set_field=(id)
	@id = id
end
```

To make it easier, use attribute readers, writers, and accessors
- **attr_reader**: used to make getter methods
- **attr_writer**: used to make setter methods
- **attr_accessor**: used to make a getter and setter method
	- Like having both attr_reader and attr_writer for a variable

These are made with the syntax `attr_X :field_name`
- Can have multiple fields in one statement via using a comma `attr_X :field1, :field2, :field3`

```rb
class Employee
	attr_reader :id #read only
	attr_accessor :first_name, :last_name, :position
	def initialize(id, first, last, pos)
		@id = id
		@first_name = first
		@last_name = last
		@position = pos
	end
end

e = Employee.new(123, "Mike", "Smith", "Rails Developer")
puts e.id # puts 123
puts e.position # puts "Rails Developer"
e.position = "Lead Rails Developer"
puts e.position # puts "Lead Rails Developer"
```

- **Note that these do not allow for extra lines of code for writers (or setters)**
- For example, if a variable *age* needs to always be positive, there is no way to use an attribute wrtier or accessor to do this, and thus a custom writer method should be made
	- Generally, this is not needed in Ruby as much as it is in languages like Java. For example, an *age* variable can generally be trusted to be non-negative, or the check can happen elsewhere
	- A common practice is to have parameter validation during development to find bugs that might happen, and remove it for deployment

### Inheritance
For one class to inherit another, use `<` in the class declaration
- `X < Y` can be read as "X inherits from Y"
	- X is the subclass
	- Y is the superclass

Use `super(...)` to invoke the constructor of the super class

Subclasses inherit methods and instance variables of super classes
- An example of this is below
```rb
class Parent
	attr_reader :name	
	def initialize(name)
		@name = name
		@test_bool = true
	end
end

# Note how test_bool is set to false but changed by the constructor
class Child < Parent
	attr_reader :num
	def initialize
		@test_bool = false
		super("Ruby")
		@num = 5 if @test_bool
	end
end

test = Child.new
puts m.test_bool # true
puts m.num # 5
```

## Modules
