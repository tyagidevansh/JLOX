# JLOX
JLOX is a tree-walk interpreter implemented in Java for the Lox language by Robert Nystrom, based on his book - crafting interpreters. It is a simple but fully functional interpreter - running on top of the JVM. 

JLOX makes use of Java's built in type-conversion and garbage collector, but implements everything else from the ground up. Reads code from top to bottom, executing lines as it comes across them. 

Supports functions, loops, strings and more! Comes with a built in print statement to display output to the console, no standard library required. Currently does not support arrays or other non-primitive data types.

## Usage
1. Clone the repository
2. Compile all the java files
3. Run Lox.java in either of two modes:
 - Run it right from the terminal by running `java Lox`
 - Write code in a text file and run it using `java Lox path/to/file`

## Syntax

### Statments
- Every statement must be end with a semicolon
- 'print' is also a statement, not a function. To print the sum of two numbers: `print 5 + 10;`
- Any statement beginning with `// is a comment` and will not be evaluated

### Variables
- All variables need to be declared before use, using the var keyword. This language has two basic data types: numbers and strings
- Numbers are internally always stored as double-precision floating point numbers.
- No type information needs to provided when initialising variables
```plaintext 
    var a = 5;               //number
    var fruit = "apple";    //string, quotation necessary
``` 

### Operators

- Mathematical expressions evaluate the same as any other modern language, supports binary as well as unary operators.
- Supported operators: `+  -  *  /  =  ==  !=  >  <  >=  <=  !`
- nil and false are 'falsey', everything else is 'truthy'

### Scoping
- Block scoping can be done with `{}`
- Variables can be in any of these scopes, or be global. 
- Scoped variables cannot be re-initialised (values can be changed). Syntax analysis checks for duplicate definitions at compile time.
- Functions also create their own scopes.
- Every variable which is mapped to a scope is only available in that environment

### Conditionals
- if and else statements supported, with C-like syntax.

```plaintext 
    if (a == b) print a;
    else print b;
    
             OR
    
    if (a == b){
        print a;
    } else {
        print b;
    }
```

### Loops
- For loop:
```plaintext 
    for (var i = 0; i < 10; i = i + 1) {
        print i;
    }
```
- While loop:
```plaintext 
    var n = 10;
    while (n >= 0) {
        print n;
        n = n - 1;
    }
```

### Functions
- Functions can be defined with the keyword 'fun' followed by an identifier and parameter. They can be called by their name and '()'
- Parameters and arguments must be separated by ',', only variable names required.
- Return statements are not required, but supported. Every function returns 'nil' by default, but can return a number or string.
Example:
```plaintext 
    //Recursively calculating the nth fibonacci number
    
    fun fib(n) {   //define the function
        if (n <= 1) return n;
        return fib(n - 2) + fib(n - 1);
    }
    
    fib(20);    //call the function
```
