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

## 3. Here's what we're going to do

### a. Get started: create the project

## 4. Get the gane to choosen an option

### a. Create the Rock, Paper, Scissors array

## 5. How you create functions

### a. You can send things to a function

## 6. You can send more than one thing to a function

### a. Calling a two-parameter function, and sending it two arguments

### b. You can pass variables to a function so long as the variable type matches the parameters type

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
