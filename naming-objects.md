# Naming Objects
## Value
- The word value indicates an abstract, mathematical concept. For example, when you say the value 12 you mean the mathematical concept of the number 12. IN mathematics, there is just one number 12 in the world.
- But values may be stored in the memory of a computer. You can store the number 12 or the string "hello" in several locations of the memory.
- The portion of memory that contains a value is named "object". Two distinct objects located in different positions of memory, are said to be "equal" if they contain the same value. Instead, two values are said to be "equal" if and only if they are not distinct, that is, they are actually the same value
- When Rust source code is compiled, the resulting executable program contains only objects that have a memory location and a value. Such objects do not have names. But in source code, you may want to associate names to objects, to reference them later. For example, you can write, as the body of the main function
- let num = 12; do:
    - it reserves an object(an area of memory) large enough to contain an integer number;
    - it stores the value 12 in such object, in binaru format;
    - it associates the name number to such object, so that such name can be used in later points of the source code to indicate such object
- A emory space shall be reserved to contain initially the value 12, and from now on, every time we use the word number, we will mean such memory space. So, such state ment declares both an object and a name of that object

## Mutable Variables
- let mut number = 12; do:
    - Declares the variable number and initializes it to the value 12. "mut" is a keyword of Rust, and it is an abbreviation of mutable.
    