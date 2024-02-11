# ULR/ULF C++

ULR/ULF C++ is a modified flavor of C++ with different semantics. It is a ULR language that compiles to native C++ (normal/g++ C++) in order to run with the ULR. ULR/ULF C++ differs from native C++ in *some* of the following ways:

Native C++:
```cpp
#include <iostream>

int main(int argc, char** argv)
{
	std::vector<int>* vec = new std::vector<int>();

	std::cout << "Hello, World!" << std::endl;

	delete vec;
	
	return 0;
}
```

ULR/ULF C++:
```cpp
#include <ULR/C++-Intellisense-Stubs.hpp> // if you are using native C++ intellisense rather than ULR/ULF C++ specialized intellisense, you should include this stub header file for better ULR/ULF intellisense. Note that all preprocessor directives will be ignored by the ULR/ULF C++ compiler

typedecl(public) class Program // need to use typedecl() to add modifiers like public and static to classes
{
	public:
	 	static int Main(string[] args) // need to define Main(string[] args) method for the ULR
		{
			List<int> myList = new List<int>(); // `new` expressions do not return pointers, all type creation is managed by the compiler based on reference/value typeness. This maintains a uniform object creation syntax for both reference and value types. The reference objects are auto-garbage collected; no explicit delete statement is required.

			Console::WriteLine("Hello, World!"); // use the console class to write to stdout

			return 0;
		}
};
```