# qu cheatsheet
This document lists every function within the qu core libraries (qu.std.core.*), their arguments, and their products.
## Code Execution
### call <Selector(Function) selector> -> Any
Executes the expressions at the given function, and returns the result.
### eval <String code> [Any input] -> Any
Interprets the string as if it were a program, and returns the output data. **Avoid using, as it is highly dangerous!**
### exec <File code> <Any input> -> Any
Executes the qu code in a file with the given input data and returns the output data. **Use sparingly!**
## Functional
### fn <Selector identifier> [Type return] <Expression... body> -> None
Stores a list of expressions at an allocated address and creates a selector that references that address. If the selector is already defined and is a function, the value will be mutated. If a type is provided, the function will return that value when invoked. If the selector is #MAIN and the code is in compile mode, this function will be the main function and does not require being called.
## Stack Manipulation
### clear -> None
Clears the stack.
## I/O
### write <Stream output_stream> -> None
Takes a stream object and writes the current stack data to it. Formatting is determined by the stream and data type.
## Variables
### set <Selector name> <Expression... value> -> Any
Stores the result of an expression at an allocated address, creates a selector that references that address, and return's the expression's result. If the selector is already defined and is references data of the same type as the given expression, the value will be mutated. If the types do not match, a TypeError will be thrown.
## Control Flow
### exit <SignedInteger return> -> SignedInteger
Clears the stack and replaces it with a single number return code, and exits the program.
### if <Boolean condition> <Expression do> [Expression else] -> None
If condition = true, execute the expression do. If it is not true, and is provided, execute else.
## Math
### add <Number a> <Number b> -> Number
Returns a + b.
### divide <Number a> <Number b> -> Number
Returns a / b.
### multiply <Number a> <Number b> -> Number
Returns a * b.
### subtract <Number a> <Number b> -> Number
Returns a - b.
### root <Number n> <Number b> -> Number
Returns nth root of b.
## Lists & Iterators
### list <Any... elements> -> List<Any>
Returns the elements wrapped in a List.
### map <List input> [UnsignedInteger index] <Expression closure> -> List
Applies an expression to each element of a List. The reserved character $ will serve as a reference to the current list element in the body of the expression.
## Tuples
