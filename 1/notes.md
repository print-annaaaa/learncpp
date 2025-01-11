# Section 1 notes
- An object is used to store a value in memory. A variable is an object that has a name (identifier).
- A definition statement can be used to tell the compiler that we want to use a variable in our program
    - At compile-time (when the program is being compiled), when encountering this statement, the compiler makes a note to itself that we want a variable with the name x, and that the variable has the data type int (more on data types in a moment). 
- At runtime (when the program is loaded into memory and run), each object is given an actual storage location (such as RAM, or a CPU register) that it can use to store values. The process of reserving storage for an object’s use is called allocation. Once allocation has occurred, the object has been created and can be used
- The data type of an object must be known at compile-time (so the compiler knows how much memory that object requires).
- After a variable has been defined, you can give it a value (in a separate statement) using the = operator. This process is called assignment, and the = operator is called the assignment operator.
    - By default, assignment copies the value on the right-hand side of the = operator to the variable on the left-hand side of the operator. This is called copy-assignment.
- We can combine defining and assigning a value in a signle step (initialization):
    ```int width {5} ```
- There are 5 common forms of initialization in C++:
```
int a;         // default-initialization (no initializer)

// Traditional initialization forms:
int b = 5;     // copy-initialization (initial value after equals sign)
int c ( 6 );   // direct-initialization (initial value in parenthesis)

// Modern initialization forms (preferred):
int d { 7 };   // direct-list-initialization (initial value in braces)
int e {};      // value-initialization (empty braces) 
```

- The modern way to initialize objects in C++ is to use a form of initialization that makes use of curly braces. This is called list-initialization (or uniform initialization or brace initialization).

- List-initialization comes in two forms:
```
int width { 5 };    // direct-list-initialization of initial value 5 into variable width (preferred)
int height = { 6 }; // copy-list-initialization of initial value 6 into variable height (rarely used) 
```
- If you try to list-initialize a variable using a value that the variable can not safely hold, the compiler is required to produce a diagnostic (narrowing conversions):
```
int w1 { 4.5 }; // compile error: list-init does not allow narrowing conversion
int w2 = 4.5;   // compiles: w2 copy-initialized to value 4
int w3 (4.5);   // compiles: w3 direct-initialized to value 4
```
- List-initialization (including value-initialization i.e empty braces) is generally preferred over the other initialization forms because it works in most cases (and is therefore most consistent), it disallows narrowing conversions, and it supports initialization with a list of values.
- Instantiation is a fancy word that means a variable has been created (allocated) and initialized (this includes default initialization). An instantiated object is sometimes called an instance. 
- Settings are set to produce errors on seeing unused variables. This can be fixed with [[maybe_unused]]:
```
[[maybe_unused]] double pi { 3.14159 };  // Don't complain if pi is unused
    [[maybe_unused]] double gravity { 9.8 }; // Don't complain if gravity is unused
    [[maybe_unused]] double phi { 1.61803 }; // Don't complain if phi is unused

```
