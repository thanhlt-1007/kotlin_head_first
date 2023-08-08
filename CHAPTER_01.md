# CHAPTER 01

## Getting started: A Quick Dip

Kotlin is making waves.

From its first release, Kotlin has impressed programmers with its friendly syntax, conciseness, flexibility and power. In this book, we'll teah your how to build your own Kotlin applications, and we'll start by getting you to build a basic application and run it. Along the way, you'll be introduced to some of Kotlin's basic syntax, such as statements, loops and conditional branching. Your journey has just begun ...

## Welcome to Kotlinville

Kotlin has been taking the programming world by storm. Despite being one of the youngest programming languages in town, many developers now view it as their language of choice. So what makes Kotlin is special?

Kotlin has many morden language features that mekt it attractive to developers. You'll find out about these features in more detaul later in the book, but for now, here aer some of the highlights.

### It's crisp, concise and readable

Unlike some languages, Kotlin code is very concise, and you can perform powerful tasks in just one line. It provides shortcuts for common actions so that you don't have to write lots of repetitive boilerplate code, and it has a rich library of functions that you can use. And as there's less code to wade through, it's quicker to read, write and understand, leaving you more time to do other things.

### You can use object-oriented AND functional programming

Can't decide whether to learn object-oriented or functional programming? Well, why not do both? Kotlin lets you create object-oriented code that use classes, inheritance and polymorphism, just as you can in Java. But it also supports functional programming, giving you the best of both worlds.

### The compiler keeps you safe

Nobody likes unsafe, buggy code, and Kotlin's compiler puts a lot of effect into making sure your code is as clean as possible, preventing many of the errors that can occur in other programming languages. Kotlin is statically typed, for example, so you can't perform inappropriate actions on the wrong tyoe of variable and crash your code. And most of the time, you don't even need to explicitlt specify the type yourself as the compiler can infer it for you.

So Kotlin is a morden, powerful and flexible programming language that offers many advantages. But that's not the end of the story.

## You can use Kotlin nearly everywhere

Kotlin is so powerful and flexible that you can use it as a general-purpose language in many different contexts. This is because you can choose which platform to compile your Kotlin code against.

### Java Virtual Machines (JVMs)

Kotlin code can be compiled to JVM (Java Virtual Machine) bytecode, so you can use Kotlin practically anywhere that you can use Java. Kotlin is 100% interoperable with Java, so you can use existing Java libraries with it. If you're working on an application that contains a lot of old Java code, you don't have to throw all the old code away; your new Kotlin code will work alongside it. And if you want to use the Kotlin code you've written from inside Java, you can do so with ease.

### Android

Alongside other languages such as Java, Kotlin has first-class support for Android, Kotlin is fully supported in Android Studio, and you can make the most of Kotlin's many advantages when you develop Android apps.

### Client-side and server-side JavaScript

You can also transpile or translate and compile Kotlin code into JavaScript, so that you can run it in a browser. You can use it to work with both client-side and server-side technology, such as WebGL or Node.js

### Native apps

If you want to write code that will run quickly on less powerful devices, you can compile your Kotlin code directly to native machine code. Thif allows you to write code that will run, for example, on iOS or Linux.

In this book, we're going to focus on creating Kotlin applications for JVMs, as this is the most straightforward way of getting to grips with the language. Afterwards, you'll be able to apply the knowledge you've gained to other platforms.

Let's dive in.

## What we'll do in this chapter

In this chapter, we're going to show you how to build a basic Kotlin application. There are a number of step we're going to go through to do this:

### 1. Create a new Kotlin project.

We'll start by installing IntelliJ IDEA (Community Edition), a free IDE that supports Kotlin application development. We'll then use the IDE to build a new Kotlin project:

### 2. Add a function that displays some text.

We'll add a new Kotlin file to the project, then write a simple main function that will output the text "Pow!"

### 3. Update the function to make it do more.

Kotlin includes basic languages structures such as statements, loops and conditional branching. We'll use these to change our function so that it does more.

### 4. Try out code in the Kotlin interactive shell.

Finally, we'll kool at how to try out snippets of code in the Kotlin interactive shell (or REPL).

## Install IntelliJ IDEA (Community Edition)

The easiest way of writting and running Kotlin code is to use IntelliJ IDEA (Community Edition). This is a free IDE from JetBrains, the people who invented Kotlin, and it comes with everything you need to develop Kotlin applications, including:

- A code editor: The code editor offers code completion to help you write Kotlin code, and formatting and color highlighting to make your code easier to read. It also gives you hints for improving your code.

- Build tools: You can compile and run your code using quickly and easy shortcuts.

- Kotlin REPL: You have easy access to the Kotlin REPL, which lets you try out code snippets outside your main code.

- Version control: IntelliJ IDEA interfaces with major version control systems such as Git, SVN, CVS and more.

To follow along with us in this book, you need to install IntelliJ IDEA (Community Edition). You can download the IDE here

```
https://www.jetbrains.com/idea/download/index.html
```

Once you've installed the IDE, open it. You should see the IntelliJ IDEA welcome screen. You're ready to build your first Kotlin application.

## Let's build a basic application

Now you've set up your development environment, you're ready to create your first Kotlin application. We're going to create a very simple application that will display the text "Pow!" in the IDE.

Whenever you create a new application in IntelliJ IDEA, you need to create a new project for it. Make sure you have the IDE open, and follow along with us.

### 1. Create a new project

The IntelliJ IDEA welcome screen gives you to a number of options for what you want to do. We want to create a new project, so click on the option for "Create New Project".

### 2. Specify the type of project

Next, you need to tell IntelliJ IDEA what sort of project you want to create.

IntelliJ IDEA allows you to create projects for various languages and platformsm such as Java and Android. We're going to create a Kotlin project, so choose the option for "Kotlin".

You also need to specify which platform you want your Kotlin project to target. We're going to create a Kotlin application with a JVM target, so select the Kotlin / JVM option. Then click on the Next button.

### 3. Configure the project

You now need to configure the project by saying what you want to call it, where you want to store the files, and what files should be used by the project. This includes which version of Java should be used by the JVM, and the library for the Kotlin runtime.

Name the project "MyFirstApp", and accept the rest of the defaults.

When you click on the Finish button, IntelliJ IDEA will create your project.

## You've just created your first Kotlin project

After you've finished going through the steps to create a new project, IntelliJ IDEA sets up the project for you, then display it. Here's the project that the IDE created for us:

As you can see, the project features an explorer which you can use to navigate the files and folders that make up your project. InteliJ IDEA creates this folder structure for you when you create the project.

The folder structure is comprised of configuration files that are used by the IDE, and some external libraries that your application will use. It also includes a src folder, which is used to hold your source code. You'll spend most of your time in Kotlinville working with the src folder.

The src folder is currently empty as we haven't added any Kotlin files yet. We'll do this next.

## Add a new Kotlin file to the project

before you can write any Kotlin code, you first need to create a Kotlin file to put it in.

To add a new Kotlin file to your project, highlight the src folder in IntelliL IDEA's explorer, then click on the FIle menu and choose New -> Kotlin File/Class. You will prompted for the name and type of Kotlin file you want to create. Name the file "App", and choose File from the Kind option, like this:

When you click on the OK button, IntelliJ IDEA creates a new Kotlin file named App.kt, and adds it to the src folder in your project:

Next, let's look at the code need to add to App.kt to get it do something.

## Anatomy of the main function

We're going to get our Kotlin cpde to display "Pow!" in the IDE's output window. We'll do this be adding a function to App.kt

Whenever you write a Kotlin application, you must add a function to it called main, which start your application. When you run your code, the JVM looks for this function, and executes it.

The main fuction looks like this

```JAVA
fun main(args: Array<String>) {
  // Your code goes here
}
```

- "fun" means it's a function

- The name of this function

- The function's parameters, enclosed in parenthese. The function is given an array of Strings, and the array is named "args"

- Opening brace of the function

- The "//" denotes a comment Replace the comment with any code you want the function to execute

- Closing brace of the function

The function begins with the work fun, which is used to tell the Kotlin compiler that it's a function. You use the fun keyword for each new Kotlin function you create.

The fun keyword is followed by the name of the function, in this case main. Naming the function main means that it will be automatically executed when you run the application.

The code in the braces () after the function name tells the compiler that arguments (if any) the function takes. Here, the code args: Array<String> specifies that the function accepts and array of Strings, and this array is named args.

You put any code you want to run between the curly braces {} of the main function. We want our code to print "Pow!" in the IDE, and we can do that using code like this:

```JAVA
fun main(args: Array<String>) {
  println("Pow!")
}
```

println("Pow!") prints a string of characters, or String, to the standard output. As we're running our code in an IDE, it will print "Pow!" in the IDE's output pane.

Now that you've seen what the function looks like, let's add it to our project.

PARAMETERLESS MAIN FUNCTION

If you're using Kotlin 1.2 or an earlier version, your main function must take the following form in order for it so start your application:

```JAVA
fun main(args: Array<String>) {
  // your code goes here
}
```

From Kotlin 1.3, however, you can omit main's parameters so that the function looks like this:

```JAVA
fun main() {
  // your code goes here
}
```

Through most of this book, we're going to use the longer form of the main function because this works for all versions of Kotlin.

## Add the main function to App.kt

To add the main function to your project, open the fike App.kt by double-clicking on it in IntelliJ IDEA's explorer. This open the code editor, which you use to view and edit files.

Then, update your version of App.kt so that it matches ours below:

```
fun main(args: Array<String>) {
  println("Pow!")
}
```

Let's try running our code to see what happens

THERE ARE NO DUMP QUESTIONS

Q: Do I have to add a main function to every Kotlin file I created?

A: No. A Kotlin application might use dozens (or even hundreds) of files, but you may only have one with a main function - the one that starts the application running.

You run code in IntelliJ IDEA by going to the Run menu, and selecting the Run command. When prompted, choose the Appkt option. This builds the projects, and runs the code.

After a sort wait, you should see "Pow!" displayed in an output window at the bottom of the IDE like this:

### What the Run command does

When you use the Run command, IntelliJ IDEA goes through a couple of steps before it shows you the output of your code:

#### 1. The IDE compiles your Kotlin source code into JVM bytecode.

Assuming your code has no errors, compiling the code creates one or more class files that can run in a JVM. In our case, compileing App.kt creates a class file AppKt.class

NOTE

It specifically compiles our source code into JVM bytecode because when we create the project, we select JVM option. Had we chosen to run it in another environment, the compiler sould have compiled it into code that environment instead.

#### 2. The IDE starts the JV< and runs AppKt.class

The JVM translates the AppKt.class bytecode into something the underlying platform understands, then runs it. This displays the String "Pow!" in the IDE's output window.

Now that we know our function works, let's look at how we can update it to make it do more.

## What can you say in the main function?

Once you're inside the main function (or any other function, for that matter), the fun begins. You can say all the normal things that you say in most programming languages to make your application do something.

You can get your code to:

Do something (statements)

```Kotlin
var x = 3
x *= 10

val name = "Cormorant"

println("x is $x.")
```

Do something again and again (loops)

```Kotlin
while (x > 20) {
    x -= 1
    println("x is now $x.")
}

for (i in 1..10) {
    x += 1
    println("x is now $x.")
}
```

Do something under a condition (branching)

```Kotlin
if (x == 20) {
    println("x must be 20.")
} else {
    println("x isn't 20.")
}

if (name.equals("Cormorant")) {
    println("$name Strike.")
}
```

SYNTAX UP CLOSE

here are some general syntax hints and tips for while you're finding your foor in Kotlinville:

* A single-lined comment begins with two forward slashes:

// This is a comment

* Most white space doesn't matter:

x  =  3

* Define a variable using var or valm followed by the variable's name. Use var for variables whose value you want to change, and val for ones whose value will stay the same. You'll learn more about variables in Chapter 2"

var x = 100
val serialNo = "AS498HG"

We'll look at these in more detail pver the next few pages.

## Loop and loop and loop ...

Kotlin has three standard looping constructs: while, do-while and for. For now we'll just focus on while.

The syntax for while loops is relatively simple. So long as some condition is true, you do everything inside the loop block. The loop block is bounded by a pair of curly braces, and whatever you need to repeat needs to be inside that block

NOTE

If you just have one line of code in the loop block, you can omit the curly braces.

The key to a well-behaved while loop is its conditional test. A conditional test is an expression that results in a boolean value - something that is either true or false. As an example, if you say something like "While isIceCreamInTub is true, keep scooping" you have a clear boolean test. There is either ice cream in the tub, or there isn't. But if you say "While Fred, keep scooping", you don't have a real test. You need to change it to something like "While Fred is hungry, keep scooping" in order for it to make sence.

### Simple boolean tests

You can do a simple boolean test by checking the value of a variable using a comparision operator. These include:

- < (less than)

- > (greater than)

- == (equality)

- <= (less than or equal to)

- >= (greater than or equal to)

Notice the difference between the assignment operator (a single equaks sign) and the equals operator (two equals signs).

Here's some example code that uses boolean tests:

```KOTLIN
var x = 4 // Assign 4 to x

while (x > 3) {
  // The loop code will run as x is greater than 4
  println(x)
  x = x - 1
}

var z = 27
while (z == 10) {
  // The loop code will not run as z is 27
  println(z)
  z = z + 6
}
```

## A loopy example

Let's update the code in App.kt with a new version of the main function. We'll update the main function so that it display a message before the loop starts, each time it loops, and when the loop has ended.

Update your version of App.kt so that is matches ours below (our change are in bold)

```KOTLIN
fun main(args: Array<String>) {
  var x = 1
  println("Before the loop. x = $x.")
  while (x < 4) {
    println("In the loop. x = $x.")
    x += 1
  }
  println("After the loop. x = $x.")
}
```

Let's try running the code.

### Test drive

Run the code by going the the Run menu, and selecting the Run "App.kt" command. The following text should appear in the output window at the bottom of the IDE:

```KOTLIN
Before the loop. x = 1
In the loop. x = 1
In the loop. x = 2
In the loop. x = 3
After the loop. x = 4
```

PRINT VS PRINTLN

You've probably noticed us switching between print and println. What's the difference?

println inserts a new line (think of println as print new line) while print keep printing to the same line. If you want each thing to print out on its own line, use println. If you want everything to stick together on the same line, use print.

Now that you've learned how while loops and boolean test work, let's look at if statements.

## Conditional branching

An if test is similar to the boolean test in a while loop except instead of saying "while there's still ice cream ..." you say "if there's still ice cream ..."

So that you can see how this works, here's some code that prints a String if one number is greater than another:

```KOTLIN
fun main(args: Array<String>) {
  val x = 3
  val y = 4
  if (x > y) {
    println("x is greater than y")
  }

  println("This line runs no matter what")
}
```

The above code executes the line that prints "x is greater than y" only if the condition (x is greater than y) is true. Regardless of whether it's true, though, the line that prints "This line runs no matter what" will run. So depending on the values of x and y, either one statement or two will print out.

We can also add an else to the condition, so that we can say something like "if there's still ice cream, keep scooping, else (otherwise) eat the ice cream the buy some more".

Here's an updated version of the above code that includes an else:

```KOTLIN
fun main(args: Array<String>) {
  val x = 3
  val y = 1
  if (x > y) {
    println("x is greater than y")
  } else {
    println("x is not greater than y")
  }
  println("This line runs no matter what")
}
```

In most languages, that's pretty much the end of the story as far as using if is concerned; you use it to execute code if conditions have been met. Kotlin, however, takes things a step futher.

## Using if to return a value

In Kotlin, you can use if as an expression, so that it returns a value. It's like saying "if there's ice cream in the tub, return one value, else return a different value". You can use this form to write code that's more concise.

Let's see how this works by reworking the code you saw on the previous page. Previously, we used the following code to print a String:

When you use if as an expression, you MUST include an else clause.

```KOTLIN
if (x > y) {
  println("x is greater than y")
} else {
  println("x is not greater than y")
}
```

We can rewrite this using an if expression lile so:

```KOTLIN
println(if (x > y) "x is greater than y" else "x is not greater than y")
```

The code
```KOTLIN
if (x > y) "x is greater than y" else "x is not greater than y"
```

is the if expression. In first checks the if's condition: x > y. If this condition is true, the expression returns the String "x is greater than y". Otherwise (else) the condition is false, and the expression returns the String "x í not greater than y" instead.

The code then prints the value of the if expression using println:

```KOTLIN
println(if (x > y) "x is grater than y" else "x is not greater than y")
```

So if x is greater than y, "x is grater than y" get printed. If it's not, "x is not grater than y" gets printed instead.

As you can see, using an if expression in this way has the same effect as the code you saw on the previous page, but it's more concise.

## Update the main function

Let's update the code in App.kt with a new version of the main function that uses an if expression. Replace the code in your version of App.kt so that is matches ours below:

```KOTLIN
fun main(args: Array<String>) {
  val x = 3
  val y = 1
  println(if (x > y) "x is greater than y" else "x is not greater than y")
  println("This line runs no matter what")
}
```

Let's take the code for a test drive.
