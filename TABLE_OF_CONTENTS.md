# TABLE OF CONTENTS (THE REAL THING)

## How to use this book: Intro

Your brain on Kotlin.

Here you are trying to learn something, while here your brain is, doing you a favor by making sure the learning the learning doesn't stick. Your brain's thinking, "Better leave room for more important things, like which wild animals to avoid and whether naked snowboarding is a a bad iddea." So how do you trick your brain into thinking that your life depends on knowing how to code in Kotlin?

- "Who is this book for"

- "We know what you're thinking"

- "We know what your brain is thinking"

- "Metacognition: thinking about thinking"

- "Here's what WE did:"

- "Read me"

- "The technical review team"

- "Acknowledgments"

## Chapter 1

Kotlin is making waves.

From its first release, Kotlin has impressed programmers with its friendly syntaxm conciseness, flexibility and power. In this book, we'll teach you how to build your own Kotlin applications, and we'll start by getting you to build a basic application and run it. Along the way. you'll be introduced to some of Kotlin's basic syntax, such as statements, loops and conditional branching. Your journey has just begun ...

- "Welcome to Kotlinville"

- "You can use Kotlin nearly everywhere"

- "What we'll do in this chapter"

- "Install IntelliJ IDEA (Community Edition)"

- "Let's build a basic application"

- "You've just created your first Kotlin project"

- "Add a new Kotlin file to the project"

- "Anatomy of the main function"

- "Add the main function to App.kt"

- "Test drive"

- "What can you say in the main function"

- "Loop and loop and loop ..."

- "A loopy example"

- "Conditional branching"

- "Using if to return a value"

- "Update the main function"

- "Using the Kotlin interactive shell"

- "You can add multi-line code snippets to the REPL"

- "Puzzle Mixed Messages"

- "Your Kotlin Toolbox"

## Chapter 2

There's one thing all code depends on - variables.

So in this chapter, we're going to look under the hood, and show you how Kotlin variables really work. You'll discover Kotlin's basic types, such as Ints, Floats and Booleans, and learn how the Kotlin compiler can cleverly infer a variable's type from the value it's given. You'll find out how to use String templates to construct complex Strings with very little code, and you'll learn how to create arrays to hold multiple values. Finally, you'll discover why objects are so important to life in Kotlinville.

- "Your code needs variables"

- "What happens when you declare a variable"

- "The variable holds a reference to the object"

- "Kotlin's basic types"

- "How to explicitly declare a variable's type"

- "Use the right value for the variable's type"

- "Assigning a value to another variable"

- "We need to convert the value"

- "What happens when you convert a value"

- "Watch out for overspill"

- "Store multiple values in an array"

- "Create the PhraseOMatic.kt"

- "The compiler infers the array's type from its values"

- "var means the variable can point to a different array"

- "val means the variable points to the same array forever..."

- "Puzzle Mixed References"

- "Your Kotlin Toolbox"

## Chapter 3

It's time to take it up a notch, and learn about functions.

So far, all the code you've written has been inside your appliaction's main function. But if you want to write code that's better organized and easier to maintain, you need to know how to split your code into separate functions. In thif chapter, you'll learn how to write functions an interact with your application bu building a game. You'll discover how to write compact single expression functions. Along the way you'll find out how to interate through ranges and collections using the powerful for loop.

- "Let's build a game: Rock, Paper, Scissors"

- "A high-level design of the game"

- "Get the game to choosen an option"

- "How your create functions"

- "You can send more than one thing to a function"

- "You can get things back from a function"

- "Functions with single-expression bodies"

- "Add the getGameChoice function to Game.kt"

- "The getUserChoice function"

- "How for loops work"

- "Ask the user for their choice"

- "Puzzle Mixed Messages"

- "We need to validate the user's input"

- "Add the getUserChoice function to Game.kt"

- "Add the printResult function to Game.kt"

- "Your Kotlin Toolbox"

## Chapter 4

It's time we looked beyond Kotlin's basic types.

Sooner or later, you're going to want to use something more than Kotlin's basic types. And that's where classes come in. Classes are templates that allow you to create your own types of objects, and define their properties and functions. Here, you'll learn how to design and define classes, and how to use them to create new types of objects. You'll meet constructor, initializer blocks, getter and setters, and you'll discover how they can be used to protect your properties. Finally, you'll learn how data hiding is built into all Kotlin code, saving you time, effort and a multitude of keystrokes.

- "Object types are defined using classes"

- "How to design your own classes"

- "Let's define a Dog class"

- "How to create a Dog object"

- "How to access properties and functions"

- "Create a Songs application"

- "The miracle of object creation"

- "How objects are created"

- "Behind the scenes: calling the Dog constructor"

- "Going deeper into properties"

- "Flexible property initialization"

- "How to use initialize blocks"

- "You MUST initialize your properties"

- "How do you validate propertu values"

- "How to write a custom getter"

- "How to write a custom setter"

- "The full code for the Dogs project"

- "Your Kotlin Toolbox"

## Chapter 5

Ever found yourself thinking that an object's type would be perfect if you could just change a few thing?

Well, that's one of the advantages of inheritance. Here, you'll learn how to create subclasses, and inherit the properties and functions of a superclass. You'll discover hơ to override functions and properties to make your classes behave the way you want, and you'll find out wjen this is (and isn't) appropriate. Finally, you'll see how inheritance helps you avoid duplicated code, and how to improve your flexibility with polymorphism.

- "Inheritance helps you aboild duplicate code"

- "What we're going to do"

- "Design an animal class inheritance structure"

- "Use inheritance to avoid duplcate code in subclasses"

- "What should the subclasses override?"

- "We can group some of the animals"

- "Add Canine and Feline classes"

- "Use IS-A to test your class hierarchy"

- "The IS-A test works anywhere in the inheritance tree"

- "We'll create some Kotlin animals"

- "Declare the superclass and its properties and functions as open"

- "How a subclass ingerits from a superclass"

- "How (and when) to override properties"

- "Overriding properties lets you do more than assign default values"

- "How to override functions"

- "An overriden function or property stays open..."

- "Add the Hippo class to the Animals project"

- "Add the Canine and Wolf classes"

- "Which function us called?"

- "When you call a supertype for a function's parameters and return type"

- "The updated Animals code"

- "Your Kotlin Toolbox"

## Chapter 6

A superclass inheritance hierarchy is just the beginning.

If you want to fully exploit polymorphism, you need to design using abstract classes and interfaces. In this chapter, you'll discover how to use abstract classes to control which classes in your hierachy can add can't be instantiated. You'll see how they can force concrete subclasses to provide their implementations. You'll find out how to use interfaces to share behavior between independent classes. And along the way, you'll learn the ins and outs of is, as, and when.

- "The Animal class hierarchy revisited"

- "Some classes shouldn't be instantiated"

- "Abstract or concrete?"

- "An abstract class can have abstract properties and functions"

- "The Animal class has two abstract functions"

- "How to implement an abstract class"

- "You MUST implement all abstract properties and functions"

- "Let's update the Animal project"

- "Independent classes can have common behavior"

- "An interface lets you define common behavior OUTSIDE a super class hierarchy"

- "Let's define the Roamable interface"

- "How to define interface properties"

- "Declare that a class implements an interface..."

- "How to implement multiple interfaces"

- "How do you know whether to make a class, a subclass. an abstract class, or an interface?"

- "Update the Animals project"

- "Interfaces let you use polymorphism"

- "Where to use the is operator"

- "Use when to compare a variable against a bunch of options"

- "The is operator usually performs a smart cast"

- "Use as perform an explicit cast"

- "Update the Animals project"

- "Your Kotlin Toolbox"

## Chapter 7

Nobody wants to spend their life reinventing the wheel.

Most applications include classes whose main purpose is to store data, so to make your coding life easier, the Kotlin developers came up with the concept of a data class. Here, you'll learn how data classes enable you to write code that's cleaner and more concise than you ever dreamed was possible. You'll explore the data class utility functions, and discover how to destructure a data object into its component parts. Along the way, you';; find out how default parameter values can make your code more flexible, and we'll introduce you to Any, the mother of all superclasses.

- "== calls a function named equals"

- "equals is inherited from a superclass named Any"

- "The common behavior defined by ANy"

- "We might want equals to check whether two objects are quivalent"

- "A data class lets you create data object"

- "Data classes override their inherited behavior"

- "Copy data objects using the copy function"

- "Data classes define component functions..."

- "Create the Recipes project"

- "Puzzle Mixed Messages"

- "Generated functions only use properties defined in the constructor"

- "Initializing many properties can lead to combersome code"

- "How to use a constructor's default values"

- "Functions can use default values too"

- "Overloading a function"

- "Let's update the Recipes project"

- "The code continued..."

- "Your Kotlin Toolbox"

## Chapter 8

Everybody wants to write code that's safe.

And the greate news is that Kotlin was designed with code-safety as its heart. We'll start by showing you how Kotlin's use nullable types means that you'll hardly ever experience a NullPointerException during your entire stay in Kotlinville. You'll discover how to make a safe calls, and how Kotlin's Elvis operator stops you being all shook up. And when we're done with nulls, you'll find out how to throw and catch exceptions like a pro.

- "How do you remove object references from variables"

- "Remove an object reference using null"

- "You can use a nullable type everywhere you can use a non-nullable type"

- "How to create an array of nullable types"

- "How to access a nullable type's functions and properties"

- "Keep things safe with safe calls"

- "You can chain safe calls together"

- "The story continues..."

- "You can use safe calls to assign values..."

- "Use let to run code if values are not null"

- "Using let with array items"

- "Instead of using an if expression..."

- "The !! operator deliberately throws a NullPointerException"

- "Create the Null Values project"

- "The code continued..."

- "An exception is thrown in exceptional circumstances"

- "Catch exceptions using a try/catch"

- "Use finally for the things you want to do no matter what"

- "An exception is an object of type Exception"

- "You can explicitly throw exceptions"

- "try and throw are bpth expressions"

- "Your Kotlin Toolbox"

## Chapter 9

Ever wanted something more flexible than an array?

Kotlin comes with a bunch of useful collections that give you more flexibility and greater control over how you store and manage groups of objects. Want to keep a resizeable list that you can keep adding to? Want to sort, shuffle or reverse its contents? Want to find something by name? Or do what something what will automatically weed out duplicates without lifting a finger? If you want any or these things, or more, keep reading. It's all here...

- "Arrays can be useful..."

- "...but there are things an array can't handle"

- "When in doubt, go to the Library"

- "List, Set and Map"

- "Fantastic Lists..."

- "Create a MutableList..."

- "You can remove a value..."

- "You can change the order and make bulk changes..."

- "Create the Collections project"

- "Lists allow duplicate values"

- "How to create a Set"

- "Update the Collections project"

- "Time for a Map"

- "How to use a Map"

- "Create a MutableMap"

- "You can remove entries from a MutableMap"

- "You can copy Maps and MutableMaps"

- "The full code for the Collections project"

- "Puzzle Mixed Messages"

- "Your Kotlin Toolbox"

## Chapter 10

Everybody likes code that's consistent.

And one way of writing consistent code that's less prone to problems is to use generics. In this chapter, we'll look at how Kotlin's collection classes use generics to stop you from putting a Cabbage into a List<Seagull>. You'll discover when and how to write your own generic classes, interfaces and functions, and how to restrict a generic type to a specific supertype. Finally, you'll find out how to use covariance and contravariance, putting YOU in control of your generic types' behavior.

- "Collections use generics"

- "How a MutableList is defined"

- "Using type parameters with MutableList"

- "Things you can do with a generic class or interface"

- "Here's what we're going to do"

- "Create the Pet class hierarchy"

- "Define the Contest class"

- "Add the scores property"

- "Create the getWinners function"

- "Create some Contents objects"

- "Create the Generics project"

- "The Retailer hierarchy"

- "Define the Retailer interface"

- "We can create CatRetailer, DogRetailer and FishRetailer objects..."

- "Use out to make generic type covaraint"

- "Update the Generics project"

- "We need a Vet class"

- "Create Vets objects"

- "Use in to make a generic type contravariant"

- "A generic type can be locally contravariant"

- "Update the Generics project"

- "Your Kotlin Toolbox"

## Chapter 11

Want to write code that's even more powerful and flexible?

If so, then you need lambdas. A lambda - or lambda expression is a block of code that you can pass around just like an pbject. Here, you'll discover how to define a lambda, assign it to a variable, and then execute its code. You'll learn about function types, and how these can help you write higher-order functions that use lambdas for their parameter or return values. And along the way, you'll find out how a little syntactic sugar can make your coding life sweeter.

- "Introducing lambdas"

- "What lambda code looks like"

- "You can assign a lambda to a variable"

- "Lambda expression have a type"

- "The compiler can infer lambda parameter types"

- "Use the right lambda for the variable's type"

- "Create the Lambdas project"

- "You can pass a lambda to a function"

- "Invoke the lambda in the function body"

- "What happens when you call the function"

- "You can move the lambda OUTSIDE the ()'s..."

- "Update the Lambdas project"

- "A function can return a lambda"

- "Write a function that receives ANH returns lambdas"

- "How to use the combine function"

- "Use typealias to provide a different name for an existing type"

- "Update the Lambdas project"

- "Your Kotlin Toolbox"
