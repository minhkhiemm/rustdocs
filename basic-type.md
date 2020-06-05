Rust's types serve several goals:
1. Safety:
  By checking a program's types, the Rust compiler rules out whole classes of common mistakes. By replacing null pointers and unchecked unions with type-safe alternatives, Rust is even able to eliminate errors that are common sources of crashes in other languages
2. Efficiency:
   Programmers have fine-grained control over how Rust programs represent values in memory, and can choose types they know the processor will handle efficiently. Programs needn't pay for generality or flexibility they don't use.
3. Concision:
   Rust manages all of this without requiring too much guidance from the programmer in the form of types written out in the code. Rust programs are usually less cluttered with types than the analogous C++ program would be

- Rather than using an interpreter or a just-in-time compiler, Rust is designed to use ahead-of-time compilation: the translation of your entire program to machine code is completed before it ever begins execution.
- Rust is a statically typed language: without actually running the program, the compiler checks that every possible path of execution will use values only in ways consistent with their types. This allows Rust to catch many programming mistakes early, and is crucial to Rust's safety guarantees.
- Compared to a dynamically typed language like JavaScript or Python, Rust requires more planning from you up front: you must spell out the types of functions' parameters and return values, members of struct types, and a few other constructs. however, two features of Rust make this less trouble than you might expect:
  - Given the types that you did spell out, Rust will infer most of rest for you. In practice, there's often only one type that will work for a given variable or expression; when this is the case, Rust lets you leave out the type. For example, you could spell out every type in a function, like this:
  ```rust
  fn build_bector() -> Vec<i16> {
    let mut v: Vec<i16> = Vec::<i16>::new();
    v.push(10i16);
    v.push(20i16);
    v
  }
  ```
    But this is clutterred and repetitive. Given the function's return type, it's obvious that v must be a Vec<i16>, a vector of 16-bit signed integers; no other type would work. And from that it follows that each element of the vector must be an i16. This is exactly the sort of reasoning Rust's type inference applies, allowing you to instead write:
  ```rust
  fn build_vector() -> Vec<i16> {
    let mut v=Vec::new();
    v.push(10);
    v.push(20);
    v
  }
  ```
  - Functions can be generic: when a function's purpose and implementation are general enough, you can define it to work on any set of types that meet the necessary criteria. A single definition can cover an open-ended set of use cases.
- Rust has several types that represent memory addresses.
- This is a big difference between Rust and most languages with garbage collection. In Java, if class Tree contains a field Tree left;, the left is a reference to another separately created Tree object. Object never physically contain other objects in Java.
- Rust is differenct. The languae is designed to help keep allocations to a minimum. Values nest by default. The value ((0, 0), (1440, 900)) is stored as four adjacent integers. If you store it in a local variable, you've got a local variable four integers wide. Nthing is allocated in the heap
- References:
  - a value of type &String (pronounced "ref String") is a reference to a String value, a &i32 is a reference to an i32 and so on
  - It's easiest to get started by thinking of references as Rust's basic pointer type. A reference can point to any value anywhere, stack or heap. The expression &x produces a reference to x; in Rust terminology, we say that it borrows a reference to x. Given a reference r, the expression *r refers to the value r points to. These are very much like the & and * operators in C and C++. And like a C pointer, a reference does not automatically free any resources when it goes out of scope.
  - Unlike C pointers, howeer, Rust references are never null: there is simply no way to produce a null reference in safe Rust. And Rust references are immutable by default
- Boxes:
  - The simplest way to allocate a value in the heap is to use Box::new