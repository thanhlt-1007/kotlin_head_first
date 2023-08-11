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

### a. Functions with no return value

## 8. Functions with single-expression bodies

### a. Create the getGameChoice function

## 9. Code Magnets

## 10. Code Magnets Solution

## 11. Add the getGameChoice funcrion to Game.kt

## 12. Behind the scenes: what happens

## 13. The story continues

## 14. The getUserChoice function

### a. Ask for the user's choice

## 15. How for loops work

### a. Looping through a range of numbers

### b. Use downTo to reverse the range

### c. Use step to skip numbers in the range

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
