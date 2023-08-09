# CHAPTER 02

## Basic types and variables: Being a Variable

There's one thing all code depends on - variables.

So in this chapter, we're going to look under the hood, and show you how Kotlin variables really work. You'll discover Kotlin's basic types. such as Ints, Floats and Booleans, and learn how the Kotlin compiler can cleverly infer a variable's typr from teh it's given. You'll find out how to use String templates to construct complex Strings with very little code, and you'll learn how to create arrays to hold multiple values. Finally, you;ll discover why objects are so important to life in Kotlinville.

## 1. Your code needs variables

So far, you;ve learned how to write basic statements, expressions, while loops and if tests. But there's one key thing we need to look at in order to write a great code: variables.

You've already seen how to declare variables using code like:

```KOTLIN
var x = 5
```

The code looks simple, but what's going on behind the scenes?

### a. A variable is like a cup

When you think of a variable in Kotlin, think a cup. Cups come in many different shapes and sizes - big cups, small cups, the giant disposable cups that popcorn comes in at the movies - but they all have one thing in common: a cup holds something.

Declaring a variable is like ordering a drink from Starbucks. When you place your order, you tell the barista what type of drinking you want, what name to shout out when it's ready, and whether to use a fancy reusable cup instead of one that just gets thrown away. When you declare a variable using code like:

```KOTLIN
var x = 5
```

You're telling the Kotlin compiler what value the variable should have, what name to give it and whether the variable can be reused for other values

In order to create a variable, the compiler needs to know three things:

- What the variable's name is: This is so we can use that name in our code.

- Whether or not the variable can be reused: If we initially set your variable to 2, for example, can we later set it to 3? Or should it remain 2 forever?

- What type of variable it is: Is it an integer? A String? Or something complex?

You've already seen how to name a variable, and how to use the val and var keywords to specify whether it can be reused for other values. But what about a variable's type?

## 2. What happens when you declare a variable

### a. The value is tranformed into an object

When you declare s variable using code like:

```KOTLIN
var x = 5
```

the value you're assigning to the variable is used to create a new object. In this example, you're assigning the number 5 to a new variable named x. The compiler knows that 5 is an integer, and so the code creates a new Int object with a value of 5:

NOTE

We're going to look at some different types in more detail a couple of pages ahead.

### b. .. and the compiler infers the variable's type from that of the object

The compiler then uses the type of the object for the type of the variable. In the above example, the object's type is Int, so the variable's type is Int as well. The variable stays this type forever.

Next, the object is assigned to the variable. How does this happen?

## 3. The variable holds a reference to the object

When an object is assigned to a variable, the object itself doesn't go into the variable. A reference to the object goes into the variable instead:

As the variable holds a reference to the object, this give it access to the object.

### a. val vs var revisited

If you declare the variable using val, the reference to the object stays in the variable forever and can't be replaced. But if you use the var keyword instead, you can assign another value to the variable. As an example, if we use the code

```KOTLIN
x = 6
```

to assign a value of 6 to x, this creates a new Int object with a value of 6, and puts a reference to it into x. This replaces the original reference:

Now that you've seen what happens when you declare a variable, let's look at some of Kotlin's basic types for integers, floating points, booleans, characters and Strings.

## 4. Kotlin's basic types

### a. Integers

Kotlin has four basic integer types: Byte, Short, Int and Long. Each type can hold a fixed number of bits. Bytes can hold 8 bits, for example, so a Byte can hold integer values from -128 to 127. Ints, on the other hand, can hold 32 bits, so an Int can hold integer values from -2,147,483,648 to 2,147,483,647.

By default, if you declare a variable by assigning an integer to it ysing code like this:

```KOTLIN
x = 1
```

you will create an object and variable of type Int. If the integer you assign is too large to fit into an Int, it will use a Long instead. You will also create a Long object and variable if you add an "L" to the end of the integer like this:

```KOTLIN
var hugeNumber = 6L
```

Here's a table showing the different integer types, their bit sizes and value ranges:

| Type  | Bits    | Value range               |
|-------|---------|---------------------------|
| Byte  | 8 bits  | - 128 to 127              |
| Short | 16 bits | -32768 to 32767           |
| Int   | 32 bits | -2147483648 to 2147483647 |
| Long  | 64 bits | -huge to (huge - 1)       |

HEXADECIMAL AND BINARY NUMBERS

Assign a binary number by prefixing the number with 0b.

```KOTLIN
x = 0b10
```

Assign a hexadecimal number by prefixing the number with 0x.

```KOTLIN
y = 0xAB
```

Octal numbers aren't supported.

### b. Floating points

There are two basic floating-point types: Float and Double. Floats can hold 32 bits, whereas Double can hold 64 bits.

By default, if you declare a variable by assigning a floating-point number to it using code like:

```KOTLIN
var x = 123.5
```

you will create an object and variables of type Double. If you add and "F" ot "f" to the end of the number, a Float will get created instead:

```KOTLIN
var x = 123.5F
```

### c. Booleans

### d. Characters and Strings

## 5. How to explicitly declare a variable's type

## 6. Use the right value for the variable's type

## 7. Assigning a value to another variable

## 8. We need to convert the value

## 9. What happens when you convert a value

## 10. Watch out for overspill

## 11. Store multiple values in an array

## 12. Create the PhraseO-Matic application

## 13. Add the code to PhraseOMatic.kt

## 14. The compiler infers the array's type from its values

## 15. var means the variable can point to a different

## 16. val means the variable points to the same array forever...

## 17. Code Magnets

## 18. Code Magnets Solution

## 19. Your Kotlin Toolbox
