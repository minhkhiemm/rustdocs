# rustdocs
## immutable:
    - variables in Rust immutable by default, can not chage through out the life time
    - thus, it resolve the problem of safety in Rust. If things immutable by default, the Rust compiler can check how safe the variable is
    - the un-addresable value: 
        ```go
            var x int // x = 0
        ```
        ```rust
            let x: i64 // x is un-addresable value, can use util set x = somevalue
        ```