# CHAPTER 03

## Getting Out Of Main

It's time to take it up a notch, and learn about functions.

So far, all the code you've written has been inside your application's main function. But if you want to write code that's better organized and easier to maintain, you need to know how to split your code into separate functions. In this chapter, you'll learn how to write functions and interact with your application by building a game. You'll disciver how to write compact single expression functions. Along the way you'll find out how to interate through range and collections using the powerful loop.

## 1. Let's build a game: Rock, Paper, Scissors

In all the code example you've seen so far, we've added code to the application's main function. As you already know, this function launches your application as it's the function that gets executed when you run it.

This approach has worked well while we've been learning Kotlin's basic syntax, bust most applications in the real-world split the code across multiple functions. This is because:

- It makes your code more organized

Instead of having all your code in one long main function, it's split into more manageable chunks. This makes the code much easier to read and understand.

- It makes your code more reusable

By spliting the code into separate functions, you can reuse it elsewhere.

Each functions is a named section of code that performs a specific task. As an example, you could write a function name max that determines the highest value of two values, and then call this function at various stages in your application.

In this chapter, we've going to take a closer look at how functions work by building a game Rock, Paper, Scissors.

### a. How the game will work

Goal: Make a guess that beats the computer's, and win!

Setup: When the application is launched, the game chooses Rock, Paper or Scissors at random. It then ask you to choose one of these options.

The rules: The game compares the two choices. If they are the same, the result is a draw. if the choices are different, hower, the game determines the winner using the following rules:

The game will be run in the IDE's output window.

## 2. A high-level design of the game

Before we start writing the code for the game, we need to draw up a plan of how it will work.

First, we need to figure out the general flow of the game. Here's the basic idea:

1. You start the game.
The application randomly choose one the options: Rock, Paper or Scissirs.

2. The application asks for your choice.
You type your choice in IDE's output window.

3. The application validates your choice.
If you haven't chosen a valid option, it goes back to step 2, and ask you for another choice. The game does this repeatedlly until you enter a valid options.

4. The game displays the result.
It tells you what choices you and the application have made, and whether you've won, lost, and the result is a draw.

Now that we have a clearer idea of how the application will work, let's look at how we'll code it.

## 3. Here's what we're going to do

There ara a number of steps we're going to go through to build the game:

### 1. Get the game to choose an option.

We'll create a new function named getGameChoice which will choose one of "Rock", "Paper" of "Scissors" at random.

### 2. Ask the user for their choice.

We'll do this by writting another new function named getUserChoice, and this will ask the user to enter their choice. We'll make sure they've entered a valid choice, and if they haven't, we'll keep asking them until they do.

### 3. Print the result.

We'll write a function named printResult, which will figure out whether the user won or lost, or whether the result is a tie. The function will then print the result.

### a. Get started: create the project

We'll start by creating a project for the application. You do this in exactly the same way you did in previous chapters.

Create a new Kotlin project that targets the JVM, and name the project "Rock Paper Scissors". Then create a new Kotlin file named Game.kt highlighting the src folder, clicking on the FIle menu and choosing New -> Kotlin File / Class. When prompted, name the file "Game", and choose File from the Kind option.

Now that you've created the project, let's start writing some code.

## 4. Get the gane to choosen an option

The first thing we'll do is get the game to choose one of the options (Rock, Paper or Scissors) at random. Here's what we'll do:

### 1. Create an array that contains the Strings "Rock", "Paper" and "Scissors"

We'll add this to the application's main function.

### 2. Create a new getGameChoice function that will choose one of the options at random.

### 3. Call the getGameChoice function from the main function.

We'll start by creating the array.

### a. Create the Rock, Paper, Scissors array

We'll create the array using the arrayOf function, just as we did in the previous chapter. We'll add this code to the application's main function launches. This also means that we'll be able to use it in the rest of the code we'll write later in the chapter.

To create the main function and add the array, update your version of Game.kt to match ours below:

```KOTLIN
fun main(args: Array<String>) {
  val options = arrayOf("Rock", "Paper", "Scissors")
}
```

Now that we've created the array, we need to define the new getGameChoice function. Before we can do this, we need to understand more about how you create functions.

## 5. How you create functions

As you learned back in Chapter 1, you define new functions using the fun keyword, followed by the name of function. As an example, if you wanted to create a new function named foo, you'd write code like this:

```KOTLIN
fun foo() {
  // Your code goes here
}
```

Once you've written the function, you can call it from elsewhere in your application:

```KOTLIN
fun main(args: Array<String>) {
  foo() // This runs a function named foo
}
```

### a. You can send things to a function

Sometimes, a function needs extra information in order for it to perform a task. If you're writing a function to determine the highest of two values, for examples, the function needs to know what these two values are.

You tell the compiler what values a function can accept by specifying one or more parameters. Each parameter must have a name and type.

As an example, here's how you specify that the foo function takes a single Int parameter name param:

```KOTLIN
fun foo(param: Int) { // You declare parameters inside the function's parentheses
  println("Parameter is $param")
}
```

You can then call the function and pass it an Int value:

```KOTLIN
foo(6) // We can't pass a String to foo as it onlt accepts an Int
```

PARAMETERLESS MAIN FUNCTION

Depending on your programming background and personal preferences, you might use the term arguments or parameters for the values passed into a function. Although there are formal computer science distinctions that people who wear lab coast make, we have bigger fish to fry. You can call them whatever you like but we're doing it like this:

A function use parameters. A caller passes it argements.

Arguments are the things you pass into the functions. An argument (a value like 2 or "Pizza") lands face-down into a parameter. And a parameter os nothing more than a local variable: a variable with a name and type that's used inside the body of the function.

## 6. You can send more than one thing to a function

If you want your function to have multiple parameters, you separate them with commas when you declare them, and separate the arguments with commas when you pass them to the function. Most importantly, if a function has multiple parameters, you must pass arguments of the right type in the right order.

### a. Calling a two-parameter function, and sending it two arguments

```KOTLIN
fun main(args: Array<String>) {
  printSum(5, 6)
}

fun printSum(int1: Int, int2: Int) {
  var result = int1 + int2
  println(result)
}
```

### b. You can pass variables to a function so long as the variable type matches the parameters type

```KOTLIN
fun main(args: Array<String>) {
  val x: Int = 7
  val y: Int = 8
  printSum(x, 7)
}

fun printSum(int1: Int, int2: Int) {
  val result = int1 + int2
  println(result)
}
```

As well as passing values to a function, you can also get things back. Let's see how.

## 7. You can get things back from a function

If you want to get something back from a function, you need to declare it. As an example, here's how you declare that a function named max returns an Int value:

```KOTLIN
fun max(a: Int, b: Int): Int { // The : Int tells the compiler that the function returns an Int value
  val maxvalue = if (a > b) a else b
  return maxValue // You return a value using the return keyword, followed by the value you're returning
}
```

If you declare that a function returns a value, then you must return a value of the declared type. As an example, the following code is invalid because it returns a String instead of an Int:

```KOTLIN
fun max(a: Int, b: Int): Int {
  val maxvalue = if (a > b ) a else b
  return "Fish" // We've declared that the function returns an Int value, so that the compiler will get upset if you try and return something else, like a String.
}
```

### a. Functions with no return value

If you don't want your function to return a value, you can either omit the return type from the function declaration, or specify a return type of Unit. Declaring a return type of Unit means that the function returns no value. As an example, the following two function declaration are both valid, and do the same thing:

```KOTLIN
fun printSum(int1: Int, int2: Int) {
  val result = int1 + int2
  println(result)
}

fun printSum(int1: Int, int2: Int) : Unit { // The : Unit here means that the function returns no value. It's completely optional.
  val result = int1 + int2
  println(result)
}
```

If you specify that your function has no return value, then you need to make sure that it doesn't return one. If you try to return a value in a function with no declared return type, or a return type of Unit, your code won't compile.

## 8. Functions with single-expression bodies

If you have a function whose body consist of a single expression, you can simplify code by removing the curly braces and return statement from the function declaration. As an example, on the previous page, we showed you the follwoing function to return the higher of two values:

```KOTLIN
fun max(a: Int, b: Int) : Int {
  val maxValue = if (a > b) a else b // The max function has a single expression in its body, which we then return
  return maxValue
}
```

The function returns the result of a single if expression, which means that we can rewrite the function like so:

```KOTLIN
fun max(a: Int, b: Int) : Int = if (a > b) a else b // Use = to say wjat the function returns, and remove the {}'s
```

And because the compiler can infer the function's return type from if expression, we can make the code even shorter by omitting the : Int:

```KOTLIN
func max(a: Int, b: Int) = if (a > b) a else b // The compiler knows that a and b are Ints, so it can work out the function's return type from the expression.
```

### a. Create the getGameChoice function

Now that you've learned how to create functions, see if you can write the getGameChoice function for Rock, Paper, Scissors game by having a go at the following exercise.

## 9. Code Magnets

## 10. Code Magnets Solution

## 11. Add the getGameChoice funcrion to Game.kt

Now that we've added the getGameChoice function to our application, let's look at what's going on behind the scenes when the code runs

THERE ARE NO DUMB QUESTION

Q: Can I return more than one value from a function?

A: A function can declare only one return value. But if you want to, say, return three Int values, then the declared type can be an array of Ints (Array<Int>). Put those Ints into the array, and pass it back.

Q: Do I have to do something with the return value of a function? Can I just ignore it?

A: Kotlin doesn't require you to acknowledge a return value. You might want to call a function with a return type, even though you don't caer about the return value. In this case, you're calling the function for the work it does inside the function, rather than for what it returns. You don't have to assign or use the return value.

## 12. Behind the scenes: what happens

When the code runs, the following things happen:

### 1. val options = arrayOf("Rock", "Paper", "Scissors")

This creates an array of Strings, and a variable maned options that holds a reference to it

### 2. val gameChoice = getGameChoice(options)

The contents of the options variable get passed to the getGameChoice function. The options variable holds a reference to an array of Strings, so a copy of the reference gets passed to the getGameChoice function, and lands in its optionsParam parameter. This means that the options and optionsParam variables both hold a reference to the same array.

## 13. The story continues

### 1. fun getGameChoice(optionsParam: Array<String>) = options[(Math.random() * optionsParam.size).toInt()]

The getGameChoice function selects one of the optionsParam's items at random (for examplem, the "Scissors" item). The function returns a reference to this item.

### 2. val gameChoice = getGameChoice(options)

This puts the reference returned by the getGameChoice function into a new variable named gameChoice. If, for example, the getGameChoice function returns a reference to the "Scissors" object is put into the gameChoice variable.

So when you pass a value to a function, you're really passing it a reference to an object. Does this mean you can make changes to the underlying object?

#### Yes, you can

As an example, suppose you have the following code:

```KOTLIN
fun main(args: Array<String>) {
  val options = arrayOf("Rock", "Paper", "Scissors")
  updateArray(options)
  println(options[2])
}

fun updateArray(optionsParam: Array<String>) {
  optionsParam[2] = "Fred"
}
```

The main function creates an array containing the Strings "Rock", "paper" and "Scissors". A reference to this array is passed to the updateArray function, which updates the thỉd item of the array to "Fred". Finally, the main function prints the value of the array's thỉd items, so it prints the text "Fred".

LOCAL VARIABLES UP CLOSE

As we said earlier in the chapter, a local variable is one that's used inside the body of a function. They're declared within a function, and they're only visible inside that function. If you try to use a variabl that's defined in another function, you'll get a compiler error, as in the example below:

```KOTLIN
fun main(args: Array<String>) {
  var x = 6
}

fun myFunction() {
  var y = x + 3 // This code won't compile because myFunction can't see the x variable that's declared in main
}
```

Any local variables must be initialized before they can be used. If you're using a variable for a function's return value, for example, you must initialize that variable or the compiler will get upset

fun myFunction(): String {
  var message: String
  return message // You must initialize a variable if you want to use it as a function's return value, so this code won't compile
}

Function parameters are virtual the same as local variables, as they only exist within the context of the function. They're always initialized, however, so tiy'll never get a compiler error telling you that a parameter variable might not have been initialized. This is because the compiler will give you an error message if you try to invoke a function without sending the arguments that the function needs; the compiler guarantees that functions are always called with arguments that match the parameters declared in the function, and the arguments are automatically assigned to the parameters.

Note that you can't assign a new value to any of a function's parameter variables. Behind the scenes, the parameter variables are created as local val variables that can't be reused for other values. The following code, for example, won't compile because we're trying to assign a new value to the function's parameter variable:

```KOTLIN
fun myFunction(message: String) {
  message = "Hi!" // Parameter variables are treated as local variables created using val, so you can't reuse them for other values
}
```

## 14. The getUserChoice function

Now that we've written the code to make the game choosen an option, we can move onto the next step: getting the user's choice. We'll write a new function to do this called getUserChoice, which we'll call from the main function. We'll pass the options array to the getUserChoice functions as a parameter, and we'll get it to return the user's choice (a String):

```KOTLIN
fun getUserChoice(optionsParam: Array<String>) : String {
  // Code goes here
}
```

Let's go through what we need the getUserChoice function to do it:

### 1. Ask the user for their choice.
We'll loop through the items in the option array, and ask the user to type their choice into the output window.

### 2. Read the user's choice from the output window.
After the user's entered their choice, we'll assign its valus to a new value variable.

### 3. Validate the user's choice.
We'check that the user has entered a choice, and that it's in the array. If the user has entered a valid choice, we'll get the function to return it. If they haven't, we;ll keep asking until they do.

Let's start with the code to prompt the user for their choice.

### a. Ask for the user's choice

To ask the user to input their choice of option, we'll make the getUserChoice function print the following message: "Please enter one of the following: Rock, Paper, Scissors."

One way of doing this would be to hard-code the message using the println function like this:

```KOTLIN
println("Please enter one of the following: Rock, Paper, Scissors.")
```

Instead of using a while loop to do this, we're going to use a new type of loop called a for loop. Let's see how it works.

## 15. How for loops work

A for loop is useful in situations where you want to loop through a fixed range of numbers, or through every item in an array (or some other type of collection - we'll look at this collections in Chapter 9). Let's look at how you do this.

### a. Looping through a range of numbers

Suppose you wanted to loop through a range of numbers, from 1 to 10. You've already seen how to do this kind of thing using a while loop:

```KOTLIN
var x = 1
while (x < 11) {
  // Your code goes here
  x += 1
}
```

But it's much cleaner, and requires hewer line of code, if you use a for loop instead. Here's the equivalent code:

```KOTLIN
for (x in 1..10) {
  // Your code goes here
}
```

It's like saying "for each number between 1 and 10, assign the number to a variable named x, and run the body of the loop".

To loop through a range of numbers, you first specify a name for the variable the loop should use. In the above case, we;ve named the variable x, but you can use any valid variable name. The variable gets created when the loop runs.

You specify the range of values using the .. operator. In the case above, we've used a range of 1..10, so the code loops through the numbers 1 through 10. At the beginning of each loop, it assigns the current number to the variable (in our case x).

Just like a while loop, if the loop body consist of a single statement, you can omit the curly braces. As an example, here's how you would use a for loop to print the numbers 1 to 100:

```KOTLIN
for (x in 1..10) println(x)
```

Note that the .. operator includes the end number in its range. If you wanted to exclude it, you would replace the .. operator with until. As an example, the following code prints the numbers from 1 to 99, excludes 100:

```KOTLIN
for (x in 1 until 100) println(x)
```

MATH SHORTCUTS

The increment operator ++ adds 1 to a variable. So:

```KOTLIN
x++
```

is a shortcut for

```KOTLIN
x = x + 1
```

Similarly, the decrement operator -- substract 1 from a value. Use:

```KOTLIN
x--
```

as a shortcut for

```KOTLIN
x = x - 1
```

If you want to add a number other than 1 to a variable, you can use the += operator. So:

```KOTLIN
x += 2
```

does the same as

```KOTLIN
x = x + 2
```

Similarly, you can use -=, *= and /= shortcuts for subtraction, multiplication and division.

While loops run while a given condition is true.

For loops run over a range of values or items.

### b. Use downTo to reverse the range

If you want to loop through a range of numbers in reverse order, you use downTo instead of ... or until. As an example, you'd use the following code to print the numbers from 15 down to 1:

```KOTLIN
for (x in 15 downTo 1) println(x) // Using downTo instead of ... loops through the numbers in reverse order
```

### c. Use step to skip numbers in the range

be default, the .. operator, until and downTo step through the range one number at a time. If you want, you can increase the size of the step using step. As an example, the following code prints alternate numbers from 1 to 100:

```KOTLIN
for (x in 1 .. 100 step 2) println(x)
```

### d. Looping through the items in an array

## 16. Ask the user for their choice

### a. Use the readLine function to read the user's input

## 17. We need to variable the user's input

### a. "And" and "Or" operators (&& and ||)

### b. Not equals (!= and !)

### c. Use parenthese to make your code clear

## 18. Add the getUserChoice function to Game.kt

### a. Test drive

### b. We need to print the results

## 19. Add the printResult function to Game.kt

### a. Test drive

## 20. Your Kotlin Toolbox
