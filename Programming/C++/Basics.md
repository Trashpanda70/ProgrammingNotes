## Contents

- [[#Hello World!]]
- [[#Differences With C]]
- [[#Namespaces]]

---

### Hello World!
```cpp
#include <iostream>
int main(int argc, char** argv) {
	std::cout << "Hello World!"
	return 0;
}
```

### Differences With C
- NULL is referred to as `nullptr`
- Do not need `.h` on headerfiles anymore
	- `#include <iostream>`
	- To use functions from libraries, need `using namespace X`
		- `using namespace std;` for standard library
		- Or can do `using std::cout;` (for example) to only use functions you need
			- This is preferred as it does not import the whole namespace [See Explanation](https://stackoverflow.com/questions/1452721)
		- If this is not done, need to do `namespace::functionName` for each use
			- `std::cout`
- Can print output with `cout` and the `<<` operator. Can read input with `cin` and the `>>` operator. For the difference in operators the arrows point to where the data goes to 
	- `cout << "Hello"` (data goes to cout and prints)
	- `cin >> x` (data goes from cin to variable x)
	- Can have multiple `<<` operators stacked
		- `cout << "Hello World! " << "My name is " << name` 
			- assuming name is a defined variable
- C++ supports function overloading, including functions with the same name and number of parameters (but params are different types/order)
- C++ supports default values for arguments, but these need to be the last arguments of a function

### Namespaces
