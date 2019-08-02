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