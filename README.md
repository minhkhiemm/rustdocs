# rustdocs
## immutable:
    - variables in Rust immutable by default, can not chage through out the life time
    - thus, it resolve the problem of safety in Rust. If things immutable by default, the Rust compiler can check how safe the variable is
    - the un-addresable value: 
```go
            var x int // x = 0
```
```rust
            let x: i64 // x is un-addresable value, cannot be use util set x = somevalue
```
## expression-based language:
    - Rust allow user do something like:
```rust
            let y = if x == 5 {
                10 // y = 10
            } else {
                15 // y =15
            }
```
        `if` here is the expression, it return value
```rust 
    let mut counter = 0;
    let result = loop {
        counter += 1
        if counter == 10 {
            break counter * 2;
        }
    }
```
    - in Rust, there are two kind of statements, and anything else is expression
```rust
            let x = (let y = 2); // compile error
```
        let can only be begin of statement, not an expression. let here is one type of statement: declaration statement
    - expression statement: turn statement into expression
    - (): a special type of Rust system pronounced unit.
```rust
        let x = 5;
        let y = if x == 5 {
            10;
        } else {
            15;
        }
```
        error rising here because `;` turn the expression into a statement by throwing away its value and return `()` (unit)
        
## functions:
    - return only one value
    - divergin function(do not return):
```rust
            fn diverges() -> ! {
                panic!("do not return anything");
            }
```
## tupple:
    - one of the reason Rust have tupple is the function just return one value, therefore, user can have something like that
```rust
            fn complex() -> (i64,&str) {1,"string"}
```
## heap and stack:
    - stack is a memory region that created as LIFO, avaiable in runtime. Data stored on the stack must have a known, foixed size. Put data to the stack is not consider as allocaing memory. becasue the region of stack is already known and fixed size -> push thing into the stack is faster than heap, accessing data in stack is faster than heap.
    - when put data in heap, is request a certain amout of space. OS finds an empty spot in the heap that big anough, mark it as being in use, and return a pointer(allocaing heap) 

## Ownership:
    - Each value in Rust has a variable that's called its owner
    - There can only be one owner at a time
    - When the owner goes out of scope, the value will be dropped
    - Variable scope is range within a program for which an item is valid
    - String type in Rust allow user to create new unknown size of text(put into heap).
```rust
    let x = String::from("hello");
    let y = x;
```
    - it create variable x in stack, len 5, cap 5, ptr to heap contain content
    when assign y = x, Rust disable the x in stack(no longer usable), and create new y have ptr to ptr of x
```rust
    let x = 5;
    let y = x;
```
    - x still usable after assign. The reason for that is integer in Rust save in stack -> implemented Copy trait. The price of copy in stack doesnot expensive as the other heap types(String). Therefore, Rust let user to do this thing by implement Copy trait for some types that save in stack(integer type,boolean type, floating point types, character type, typles that only contain above types).
    - Other types that allocating memory in heap when implement Drop trait. That mean variables of that type will drop if out of scope. And if user try to implement Copy trait for this will goy compile-time error.