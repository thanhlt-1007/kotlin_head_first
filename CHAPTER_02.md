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

Boolean variables are used for values that can either be true or false. You create a Boolean object and variable if you declare a variable using code like this

```KOTLIN
var isBarking = true
var isTrained = false
```

### d. Characters and Strings

There are two more basic types: Char and String.

Char variables are used for single characters. You create a Char variable by assigning a character in single quotes like this:

```KOTLIN
var letter = 'D'
```

String variables are used to hold multiple characters strung together. You create a String variable by assigning the characters enclosed in double quotes:

```KOTLIN
var name = "Fido"
```

Char variables are used for single characters. String variables are used for multiple characters strung together.

In these situations, you need to explicitly declare the variable's type. We'll look at how you do this next.

## 5. How to explicitly declare a variable's type

So far, you've seen how to creae a variable by assigning a value to it, and letting the compiler infer the type from the value. But there are times when you need to explicitly tell the compiler what type of variable you want to create. You may want to use Bytes or Shorts instead Ints, for example, because they are more efficient. Or you may want to declare a variable at the start of your code, and assign a value to it later on.

You explicitly declare a variable's type using code like this:

```KOTLIN
var smallNum: Short
```

Instead of letting the compiler infer the variable's type from its value, you put a colon (:) fter the variable's name, followed by the type you want it to be. So the above code is like saying "create a reusable named smallNum, and make sure it's Short".

Similarly, if you want to declare a Byte variable, you use code like this:

```KOTLIN
var tinyNum: Byte
```

### a. Declaring the type AND assigning a value

The above examples create variables without assinging values to them. If you want to explicitly declare a variable's type and assign a value to it, you can do that too. As an example, here's how you create a Short variable named z, and assign it a value of 6

```KOTLIN
var z: Short = 6
```

This example creates a variable named z with a type of Sort. The variable's value, 6, is small enough to fit into a Sort, so a Short object with a value of 6 is created. A reference to the Sort objects is then put into the variable.

When you assign a value to a variable, you need to make sure that the value is compatible with the variable. We'll look at this in more detail on the next page.

## 6. Use the right value for the variable's type

As we said earlier in the chapter, the compiler really cares about a variab;e's type so that it can stop you from performing inappropriate operations that may lead to bugs in your code. As an example, if you try to assign a floating-point number such as 3.21 to an integer variable, the compiler will refuse to compile your code. The following code, for example, won't work

```KOTLIN
var x: Int = 3.21
```

The compiler realizes that 3.12 won't fit into an Int without some loss of precision (like, everything after the decimal point), so it refuses to compile the code.

Similarly, if you try put a lerge integer into a variable that's too small for it, the compiler will get upset. If you try to assign a value of 500 to a Byte variable, for example, you'll get a compiler error

```KOTLIN
// This won't work

var tinyNum: Byte = 500
```

So in order to assign a literal value to a variable, you need to make sure that the value is compatible with the variable's type. This is particularly important when you want to assign the value if one variable to another. We'll look at this next.

The Kotlin compiler will only let you assign a value to a variable if the value and variable are compatible. If the value is too lerge or it's the wrong type, the code won't compile.

THERE ARE NO DUMB QUESTIONS

Q: In Java, numbers are primitives, so a variable holds the actual number. Is that not the case with Kotlin?

A: No, it's not. In Kotlin, numbers are objects, and the variable holds a reference to the object, not the object itself.

Q: Why does kotlin care so much about a variable's type ?

A: Because it makes your code safer, and less prone to bugs. It might sound picky, but trust us, it's a good thing.

Q: In Java, you can trat char primitives as numbers. Can you do the same for Chars in Kotlin?

A: No, Chars in Kotlin are characters, not numbers. Repeat after us, Kotlin isn;t Java.

Q: Can I name my variables anything I want?

A: No. The rules are a little flexible, but you can't, say, give your variable a name that's a reserved word. Naming your variable while, for example, is just asking for trouble. But the great news is that if you try and give a variable a name that it's illegal, IntelliJ IDEA will immediateky highlight it as a problem.

## 7. Assigning a value to another variable

When you assign the value of one variable to another, you need to make sure that their types are compatible. Let's see why by working through the following example:

```KOTLIN
var x = 5

var y = x

var z: Long = x
```

### 1. var x = 5

This creates an Int variable named x, and an Int object with a value of 5. x holds a reference to that object.

### 2. var y = x

The compiler sees that x is an Int object, so it knows that y must also have a type of Int. Rather than create a second Int object, the value of variable x is assigned to variable y. But what does this mean? It's like saying "Take the bits in x, make a copy of them, and stick that copy into y". This means that both x and y contain references to the same object.

### 3. var z: Long = x

This line tells the compiler that you want o create a new Long variable, z, and assign it the value x. But there's a problem. The x variable contains a refernce to an Int object with a value of 5, not a Long object. We know that the object has a value of 5, and we know that 5 fits into a Long object. But because the z variable is a different type to the Int object, the compiler gets upset and refuses to compile the code.

So how do you assign the value of one variable to another if the variables are of different types.

## 8. We need to convert the value

Suppose you want to assign the value of an Int variable to a Long. The compiler won't let you asign the value directly as the two variables are different types; a Long variable can only hold a reference to a Long object, so the code won't compile if you try and assign an Int to it.

In order for the code to compile, you first have to convert the value to the right type. So if you want to assign the value of an Int variable to a Long, you first have to convert its value to a Long. And you do this using the Int object's functions.

### a. An object has state and behavior

Being an object means that it has two things: state and behavior.

An object's state refers to the data that's associated with the object: its properties and values. A nummeric object, for example, has a numeric value, such as 5, 42 or 3.12 (depending on the object's type). A char object has a value that's a single character. A boolean is either true or false.

An object's behavior describes the things the object can do, or that can be done to it. A String can be capitalized, for example. Numeric objects know how to perform basic math, and convert their value into an object of a different numeric type. The object's nehavior is exposed through its functions.

### b. How to convert a numeric value to another type

In our example, we want to assign the value of an Int variable to Long. Every numeric object has a function called toLong(), which takes the object's value, and uses it to create a new Long object. So if you want to assign the value of an Int variable to a Long, you use code like this:

```KOTLIN
var x = 5
var z: Long = x.toLong()
```

The dot operator (.) allows you to call an object's functions. So x.toLong() is like saying "Go to the object that variable x has reference to, and call its toLong() function".

We'll walk through what the code does on the next page.

Every numeric type has the following conversion functions: toByte(), toShort(), toInt(), toLong(), toFloat() and toDouble().

## 9. What happens when you convert a value

### 1. var x = 5

This create an Int variable named x, and an Int object with a value of 5. x holds a reference to that object.

### 2. var z: Long = x.toLong()

This creates a new Long variable, z. The toLong() function on x's object is called, and this creates a new Long object with a value of 5. A reference to the Long object gets put into the z variable.

This approach works well if you want to convert a value into an object's that larger. But what if the new object is too small to contain the value?

## 10. Watch out for overspill

Trying to put a large valur into a small variable is like trying to pour a bucket-load of coffee into a tiny teacup. Some of the coffee will fit into the cup, but some will spill out.

Suppose you want to out the value of a Long into an int. As you saw earlier in the chapter, a Long can hold lerger numbers than an Int.

If the Long's value is within the range of values that an Int will hold, converting the value from a Long to an Int isn't problem. As an example, converting a Long value of 42 to an Int will give you an int with a value of 42:

```KOTLIN
var x = 42L

var y: Int = x.toInt() // Value is 42
```

But if the Long's value is too big for an Int, the compiler chops up the value, and you're left with some weird(but calculable) number. As an example, if you try to convert a Long value if 1234567890123 to an Int, your Int wll have a value of 1912276171:

NOTE

It involes signs, bít, binary and other geekery that we're not going into here. If you're really curious, however, search for "two's complement".

```KOTLIN
var x = 1234567890123

vả y: Int = x.toInt() // Value is 1912276171!
```

The key thing is that when you're converting numeric values from one type to another, make sure the type is large enough for the value of you may get unexpected results in your code.

Now that you've seen how variables work and have some experience with Kotlin's basic types, have a go at the following exercise.

## 11. Store multiple values in an array

There's one more type of obejct we want to introduce you to - the array. Suppose you wanted to store the names if liffty ice cream flavors, or the bar codes of all books in a library. To do that with variables would quickly get awkward, you can use an array.

Arrays are greate if you want to quick and group of things. They're easy to create, and you get fast access to each item in the array.

You can think of an array as being like a tray of cups, where each item in the array is a variable:

### a. How to create an array

You create an array using the arrayOf() function. As an example, here's how you use the function to create an array with three items (the Ints 1, 2 and 3), and assign the array to a variable named myArray:

```KOTLIN
var myArray = arrayOf(1, 2, 3)
```

You can get the value of an item in the aray by referencing the aray variable with an index. As an example, here's how you print the value of the first item:

```KOTLIN
println(myArray[0])
```

And if you want to get the size of the array, use

```KOTLIN
myArray.size
```

On the next page, we'll put this together to write a serious bysiness application - the PhraseOMatic.

## 12. Create the PhraseO-Matic application

We're going to create a new application that generates useful makerting slogans. First create a new project in IntelliJ IDEA. To do this:

1. Open InteiilJ IDEA and choose "Create New Project" from the welcome screen. This starts the wizard you saw in Chapter 1.

2. When prompted, choose the options to create a Kotlin project that targets the JVM.

3. Name the project "PhraseOmatic", accept the rest of the defaults, and click on the Finish button.

4. When your new project appears in the IDE, create a new Kotlin file named PhraseOMatic.kt by highlighting the src folder, clicking on the File menu and choosing New -> Kotlin File/Class. When prompted, name the file "PhraseOMatic", and choose File from the Kind option.

## 13. Add the code to PhraseOMatic.kt

The PhraseOMatic code consist of a main function that creates three arrays of words, randomly picks one word from each and then joins them together. Add the code below to PhraseOMatic.kt

```KOTLIN
fun main(args: Array<String>) {
  val wordArray1 = arrayOf("24/7", "multi-tier", "B-to-B", "dynamic", "pervasive")
  val wordArray2 = arrayOf("empowered", "leveraged", "aligned", "targeted")
  val wordArray3 = arrayOf("process", "paradigm", "solution", "portal", "vision")

  val arraySize1 = wordArray1.size
  val arraySize2 = wordArray2.size
  val arraySize3 = wordArray3.size

  val rand1 = (Math.random() * arraySize1).toInt()
  val rand2 = (Math.random() * arraySize2).toInt()
  val rand3 = (Math.random() * arraySize3).toInt()

  val phrase = "${wordArray1[rand1]} ${wordArray2[rand2]} ${wordArray3[rand3]}"
  println(phrase)
}
```

You've already seen what most of the code does, bit there are a couple of lines we want to draw your attention to.

First, the line

```KOTLIN
val rand1 = (Math.random() * srraySize1).toInt()
```

We need a

- multi-tier leveraged solution

- dynamic targeted vision

- 24/7 aligned paradigm

- B-to-B empowered portal

generates a random number Math.random() returns a random number between 0 and almost 1, so we have to multiply it by the number of items in the array. We then use toInt() to force the result to be an integer.

Finally, the line

```KOTLIN
val phrase = "${wordArray1[rand1]} ${wordArray2[rand2]} ${wordArray3[rand3]}"
```

uses a String template to pick three words and put them together. We'll look at String template on the next page, and then we'll show you more stuff you can do with arrays.

STRING TEMPLATES UP CLOSE

String templates provide a quick and easy way of referring to a variable from inside a String.

To include the value of a variable inside a String, you prefix the variable name with a $. To include the value of an Int variable named x inside a String, for example, you would use:

```KOTLIN
var x = 42
var value = "Value of x is $x."
```

You can also use String templates to refer to an object's properties, or call its function. In this case, you enclose the expression in curly braces. As an example, here's how you include an array's size in a String, and the value of its first item:

```KOTLIN
var myArray = arrayOf(1, 2, 3)
var arraySize = "myArray has ${myArray.size} items"
var firstItem = "The first item is ${myArray[0]}"
```

You can even use String templates to evaluate more complex expressions from inside a String. Here's how, for example, you would use an if expression to include different text depending on the size of the array myArray

```KOTLIN
var result = "myArray is ${if (myArray.size > 10) "large" else "small"}"
```

NOTE

Notice how {}'s enclose the expression we want to evaluate inside the String.

So String templates allow you to construct complex Strings with very little code.

THERE ARE NO DUMB QUESTIONS

Q: Is Math.random() the standard way of getting a random number in Kotlin?

A: It depends which version of Kotlin you're using.

Before version 1.3, Kotlin didn't have a built-in way of gejerating its own random numbers. For applications running on a JVM, however, you could use the random() method from the Java Math library, as we have.

If you're using version 1.3 or above, you can use Kotlin's built-in Random functions instead. The following code, for example, uses Random's nextInt() function to generate a random Int:

```KOTLIN
kotlin.random.Random.nextInt()
```

In this book, we've decided to continue using Math.random() to generate random numbers, as this approach works with all versions of Kotlin running on the JVM.

## 14. The compiler infers the array's type from its values

You've seen how to create an array and access its items, so let's look at how you update its values

Suppose you have an array of Ints named myArray:

```KOTLIN
var myArray = arrayOf(1, 2, 3)
```

If you want to update the second itm so that it has a value of 15, you use code like the following:

```KOTLIN
myArray[1] = 15
```

But there's a catch: the value to be the right type.

The compiler looks at the type of each item in the array, and infers what type of items the array should contain forever. In the above example, we've declared an array using Int values, so the compiler infers that the array can hold Ints. If you try and put anything other than an Int into the array, your code won't compile:

```KOTLIN
myArray[1] = "Fido" // This won't compile
```

Arrays hold items of a specific type. You can either let the compiler infer the type from the array's values, or explicitly define the type using Array<Type>.

### a. How to explicitly define the array's type

Just as we did with other variables, you can explicitly define what type of items an array should hold. As an example, suppose you wanted to declare an array that hold Byte values. To do this, you would use code like the following

```KOTLIN
var myArray: Array<Byte> = arrayOf(1, 2, 3)
```

The code Array<Byte> tells the compiler that you want to create an array that holds Byte variables. In general, simply specify the type of array you want to create by putting the type between the angle brackets (<>).

## 15. var means the variable can point to a different

There's one final thing we need to look at: what effect val and var have when you declare an array.

As you already know, a variable holds a reference to an object. When you declare a variable using var, you can update the variable so that it holds a reference to different object instead. If the variable holds a reference to an array, this means that you can upadte the variable so that it refers to a different array of the same type. As an example, the following code is perfectly valid and will compile:

```KOTLIN
var myArray = arrayOf(1, 2, 3)
myArray = arrayOf(4, 5)
```

Let's walk through what happens.

### 1. var myArray = arrayOf(1, 2, 3)

This create an array of Ints, and a variable named myArray that holds a reference to it

### 2. myArray = arrayOf(4, 5)

This creates a new array of Ints. A reference to the new arrays gets put into the myArray variable, replacing the previous reference.

So what happens if we use the variable using val instead?

## 16. val means the variable points to the same array forever...

When you declare an array using val, you can no longer update the variable so that it holds a reference to a different array. The following code, for example, won't compile:

```KOTLIN
val myArray = arrayOf(1, 2, 3)
myArray = arrayOf(4, 5)
```

Once the variable is assigned an array, it holds a reference to that array forever. But even though the variable maintains a reference to the same array, the array itself can still be updated.

Declaring a variable using val means that you can't reuse the variable for another object. You can, however, still update the object itself.

### a. ...but you can still update the variables in the aray

When you declare a variable using val, you're telling the compiler that you want to create a variable that can't be reused for other values. But this instruction only applies to the variable itself. If the variable holds a reference to an array, the items in the array can still be updated.

As an example, suppose you have the following code:

```KOTLIN
val myArray = arrayOf(1, 2, 3)
myArray[2] = 6
```

This creates a variable named myArray that holds a reference to an array of Ints. It's declared using val, so the variable must hold a reference to the same array for the duration of the program. The third item in the array is then successfully update to 6, as the array itself can be updated:

Now that you know how arrays work in Kotlinville, have a go at the following exercises.

BE THE COMPILER

Each of the Kotlin files on this page represents a complete source file. Your job is to play like you're compiler and determine whether each of these files will compile and run without errors. If they won't, how wouch you fix them?

## 17. Code Magnets

## 18. Code Magnets Solution

## 19. Your Kotlin Toolbox

BULLET POINTS

- In order to create a variable, the compiler needs to know its name, its type, and whether it can be reused.

- If the variable's type insn't explicitly defined, the compiler infers it from its value.

- A variable holds a reference to an object.

- An object has state and behavior. Its behavior is exposed through its functions.

- Defining the variable with var means the variable's object reference can be replaced. Defining the variable with val means the variable holds a reference to the same object forever.

- Kotlin has a number of basic types: Byte, Short, Int, Long, Float, Double, Boolean, Char and String.

- Explicitly define a variable's type by putting a colun after the variable's name, followed by the type

```KOTLIN
var tinyNum: Byte
```

- You can only assign a value to a variable that has a compatible type.

- You can convert one numeric type to another. If the value won't fit into the new type, some precision lost.

- Create an array using the arrayOf function

```KOTLIN
var myArray = arrayOf(1, 2, 3)
```

- Access an array;s items using, for example, myArray[0]. The first item in an array has an index of 0.

- Get an array's size using myArray.size.

- The compiler infers the array's type from its items. You can explicitly define an array's type like this:

```KOTLIN
var myArray: Array<Byte>
```

- If you define an array using val, you can still update the items in the array.

- String templates provide a quick and easy way of referring to a variable or evaluating expression from inside a String.
