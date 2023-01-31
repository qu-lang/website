# a guide to qu
Programming languages can be complicated. This guide aims to help the reader understand how to use the qu programming language as well as display what can be done with qu through rich examples. This is intended for intermediate level programmers who have experience in other languages.




&copy;2022 Waterlilly co-op. All rights reserved.




# PART 1: Scripts
A programming language often isn't very useful if simple actions are complicated to execute. This section demonstrates simple actions in qu, and will end with the creation of a script that plays a simple song from a file.
## Chapter 1.1: Values & Operations
Fundamentally, every operation in qu converts some value into another value. These operations are chained together to create the simplest type of qu program, the *script*. In the context of qu, a script is a list of operations that are executed in order by the interpreter, without any sort of control flow. Although this may not sound like a very useful program, it is the fundamental base of every single other type of qu program.
### Example 1.1.1: Zero-operator script
In the following two scripts, two methods of zero-operator scripts are given. First, one where the script is empty. Second, one where the input value is given as a constant field. NOTE: To learn how to interpret this block, view the qu interpreter manual.
```lisp
qu >> (#new ex1.1.1.qu)
	> ()
qu >> (exec ex1.1.1.qu "Hello world!")
ex1.1.1.qu >>> "Hello world!"
qu >> eval
	> "Hello world!"
)
evaluator >>> "Hello world!"
```
---
Scripts are stateless. This means that they simply have a list of inputs and a list of outputs. This can often make programming them somewhat challenging, since there is no mutable state. Instead of using variables, data operates in a singular stream, writing from the inputs downwards through each operation until it reaches the output. External inputs and outputs can still work, although they are somewhat complicated by this restriction.
### Example 1.1.2: Outputting to stdout
```lisp
; inputs: None
"Hello world!\n" ; Puts the text inline as a constant
(write #STDOUT) ; Writes to stdout
clear ; It's bad practice to return unused data
; outputs: None
```
---
In this form, math cannot be done with traditional functions. Only the heapless operators can be used.
### Example 1.1.3: Binary Math Operators on Stack
```lisp
; inputs: 5
(subtract 2, ???) ; There is no direct way to enter this data, since subtract operates on two numbers, not a number and the stack. Therefore, the operation cannot be executed.
; outputs: N/A
```
### Example 1.1.4: Unary Math Operators
```lisp
; inputs: 5
(#import qu.std.heapless.math) ; Imports the necessary math library
(math.subtract 2)
math.invert
; Outputs: -3
```
---
String manipulation is difficult, but doable, requiring some more advanced techniques.
### Example 1.1.5: Basic String Manipulation
```lisp
; inputs: "Hello world!"
(#import qu.std.string qu.std.heapless.list) ; Imports string utility as well as heapless list utility
(string.split " ") ; Splits at the space
(heapless.list.map ; Since this is operating on the stack, this will essentially be a mutation of the stack.
	(string.alphanumeric $) ;Alphanumericize the strings. $ is a variable.
	(string.capitalize $) ; Capitalize the strings.
) 
; outputs: ("Hello" "World")
```