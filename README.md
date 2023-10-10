# AdvancedTopicsInCSharp
Repository to code the course https://www.udemy.com/course/advanced-topics-csharp/

<!-- TOC -->

- [AdvancedTopicsInCSharp](#advancedtopicsincsharp)
- [Numerics](#numerics)
    - [Integral Types](#integral-types)
        - [Integer specifics](#integer-specifics)
        - [Overflow](#overflow)
        - [Division by Zero](#division-by-zero)
        - [Checked and Unchecked modes](#checked-and-unchecked-modes)
        - [Overflow and Checked](#overflow-and-checked)
    - [BigInteger](#biginteger)
- [Reflection](#reflection)
- [Dynamic Programming](#dynamic-programming)
- [Extension Methods](#extension-methods)
- [Memory Management](#memory-management)
- [Assorted Topics](#assorted-topics)

<!-- /TOC -->
# Numerics
## Integral Types
We have this types of integers
* 8-bit (byte)
* 16-bit (short)
* 32-bit (int)
* 64-bit (long)
Each of them could be used as Signed or Unsigned type

### Integer specifics
* Each type has a minumum and maximum value
    - e.g. ```int.MinValue, long.MaxValue ```
* Conversion functions from strings
    - ```int value = int.Parse("123")```
    
        This function throw an exception when it receives an invalid string

    - ```bool success = int.TryParse("123", out int value)```
    
        This function returns false if the parsing fails and initializes  the returned variable with the default value
* These are often hand-optimized in performance-critical scenarios
* The default value for all integer types is Zero (0)

### Overflow
It's when you try to get more bits than ara available on the type

e.g. *Adding 1 to the largest number, or substracting 1 fromthe smallest*. You could recive one of this error types

    Compile-Time error:
    The compiler will throw this error CS0220: The operation overflows at compile time in checked mode

    Run-Time error:
    You'll get a 'garbage' value, it means the value would be a random one

### Division by Zero
If you try to divide an integer by zero you'll receive a Compile-Time or a Run-Time error.

### Checked and Unchecked modes
It's the way we tell to the compiler how it has to treat our code.
* Checked mode = please be sure to check this for me
* Unchecked mode = please don't check this, I take resposibility

This modes only affect the Overflow, the Divisiob by Zero alway throw an exception

### Overflow and Checked
* By default, overflow is disallowed at compile-time (if found) and is totally allowed at run-time
* We can allow obvious overflow situations at compile-time with this kind of statements 
    ```
    unchecked {
        var n = int.MinValue - 1;
    }
    ```
    After this, it'll compile fine but you'll get a *garbage* value
* Also, you can detect overflows at run-time using this
    ```
    checked{
        try{
            int x2 = int.MinValue - 1;
        }
        catch(OverFlowException e){
            Console.WriteLine(e.Message);
        }
    }
    ``` 

## BigInteger
* Allows you have an integer of arbitrary size
* It's part of the System.Runtime.Numerics namespace
* It's good if you're working with huge integers.

The difference between other Integer Types are:
* Is a struct, not a primitive type
* Cannot overflow because it's dynamic, doesn't have a specfic size
* Is immutable, it means the following:
    - When you try to increment the integer using ++, it doesn't modify underlying object, instead of that creates a new object that replaces the original one. This means, it has serious performance implications.


# Reflection

# Dynamic Programming

# Extension Methods

# Memory Management

# Assorted Topics