# CHAPTER 04. classes and objects

## A Bit of Class

## 1. Object types are defined using classes

### a. You can define your own classes

## 2. How to design your own classes

## 3. Let's define a Dog class

```KOTLIN
// class : mean it's a class
// Dog   : the name of the class
// weight: the class properties
// {     : opening brace of the class
// }     : close brace of the class
class Dog(val name: String, var weight: Int, val breed: String) {
  // The bark function
  fun bark() {
    println(if (weight < 20) "Yip!" else "Woof!")
  }
}
```

## 4. How to create a Dog obejct

```KOTLIN
// You create a Dog by passing it arguments for the three properties
var myDog = Dog("Fido", 70, "Mixed")
```

## 5. How to access properties and functions

```KOTLIN
var myDog = Dog("Fido", 70, "Mixed")
// myDog.name is likely saying "go to myDog, and get its name"
println(myDog.name)
// Go to myDog, and set its weight to 75
myDog.weight = 75
// Go to myDog, and call its bark function
myDog.bark()
```

### a. What if the Dog is in a Dog array?

```KOTLIN
// This code creates two Dog objects
// and adds them to an array<Dog> array named dogs.
var dogs = arrayOf(
  Dog("Fido", 70, "Mixed"),
  Dog("Ropper", 10, "Poodle")
)
// The compiler knows that dogs[1] is a Dog object.
// so you can cees the Dog's properties and call its functions.
dogs[1].weight = 15
dogs[1].bark()
```

## 5. Create a Song application

```KOTLIN
// Define title and artist properties
class Song(val title: String, val artist: String) {
  // Add play and stop functions
  fun play() {
    println("Playing the song $title by $artist")
  }

  fun stop() {
    println("Stopped playing $title")
  }
}

fun main(args: Array<String>) {
  // Create three Songs
  val songOne = Song("The Mesopotatamians", "They Might Be giants")
  val songTwo = Song("Going Underground", "The Jam")
  val songThree = Song("Make Me Smile", "Steve Harley")
  // Play songTwo,
  // stop it,
  // then play songThree
  songTwo.play()
  songTwo.stop()
  songThree.play()
}
```

### a. Test drive

## 6. The miracle of object creation

## 7. How objects are created

```KOTLIN
// It looks like we're calling a function named Dog because of the parentheses.
var myDog = Dog("Fido", 70, "Mixed")
```

### a. What the Dog constructor looks like

```KOTLIN
// This code (including the parenthese) is the class constructor.
// Technically, it's called the primary constructor.
class Dog(val name: String, var weight: Int, val breed: String) {
  ...
}
```

## 8. Behind the scenes: calling Dog constructor

## 9. Code Magnets

## 10. Code Magnets Solution

## 11. Going deeper into properties

### a. Behind the scenes of the Dog constructor

```KOTLIN
// The constructor parameters no longer have val and var prefixed,
// so the constructor no longer creates properties for them
class Dog(name_param: String, weight_param: Int, breed_param: String) {
  // The properties are defined in the class body instead.
  val name = name_param
  var weight = weight_param
  val breed = breed_param
}
```

## 12. Flexible property initialization

```KOTLIN
class Dog(val name: String, var weight: Int, val breed: String) {
  // Each Dog object that's created will have an activities property
  // It's initial value will be an array containing a valur of "Walks"
  var activities = arrayOf("Walks")
}
```

```KOTLIN
class Dog(val name: String, var weight: Int, breed_param: String) {
  var activities = arrayOf("Walks")
  // This takes the value of breed_param,
  // makes it uppercase,
  // and assigns it to breed property
  val breed = breed_param.toUpperCase()
}
```

## 13. How to use initializer blocks

```KOTLIN
class Dog(val name: String, var weight: Int, breed_param: String) {
  var activities = arrayOf("Walk!")
  var breed = breed_param.toUpperCase()

  // This is an initializer block.
  // It contains the code that you want to runs when the Dog object is initialized.
  init {
    println("Dog $name has been created.")
  }
}
```

```KOTLIN
// weight: The properties defined in the constructor are created first
class Dog(val name: String, var weight: Int, breed_param: String) {
  // This initializer block runs next
  init {
    println("Dog $name has been created.")
  }

  // These properties are created after the first initializer block has finished.
  var activities = arrayOf("Walks")
  var breed = breed_param.toUpperCase()

  // The second initializer block runs after the properties have been created.
  init {
    println("The breed is $breed.")
  }
}
```

## 14. You MUST initialize your properties

```KOTLIN
class Dog(val name: String, var weight: Int, breed_param: String) {
  var activities = arrayOf("Walks")
  var breed = breed_param.toUpperCase()
  // The temperament property hasn't been initialized,
  // so the code won't compile.
  var temperament: String
  // This initializer the temperament property with an emprt String
  var temperament = ""
}
```

```KOTLIN
// There's no () after the name of the class,
// so the class has no defined constructor.
class Duck {
  fun quack() {
    println("Quack! Quack! Quack!")
  }
}
```

```KOTLIN
// This is an empty constructor: a constructor with no parameters.
// Behind the scenes, whenever you define a class with no constructor,
// the compiler adds an empty constructor to your compiled code
class Duck() {
  fun quack() {
    println("Quack! Quack! Quack!")
  }
}
```

```KOTLIN
// Creates a Duck variable,
// and assigns it a reference to a Dock object
var myDuck = Dock()

// This code won't compile
var myDuck = Duck
```

## 15. How do you validate property values?

```KOTLIN
println(myDog.name)
myDig.weight = 75
// Cripes
myDig.weight = -1
```

### a. The solution: custom getters and setters

## 16. How to write a custom getter

```KOTLIN
class Dog(val name: String, var weight: Int, breed_param: String) {
  var activities = arrayOf("Walks")
  val breed = breed_param.toUpperCase()

  val weightInKgs: Double
    // This code adds a new weightInKgs property with a custom getter.
    // The getter takes the value of the weight parameter, and divides it by 2.2 to get the weight in kilograms.
    get() = weight / 2.2
}
```

## 17. How to write a custom setter

```KOTLIN
class Dog(val name: String, weight_param: Int, breed_param: String) {
  var activities = arrayOf("Walks")
  var breed = breed_para.toUpperCase()

  var weight = weight_param
    // This code add a custom setter to the weight property.
    // The setter means that that value of the weight property will only get updated to a value greater than 0.
    set(value) {
      if (value > 0) field = value

      // Don't do this!
      // You'll get stuck in an endless loop.
      // Use field instead.
    }
}
```

## 18. The full code for the Dogs project

### a. Test drive

## 19. Your Kotlin Toolbox

- Classes let you define your own types.

- A class is a template for an object. One class can create many objects.

- The things an object knows about itseld are its properties. The things an object can do are its function.

- A property is a variable that's local to the class.

- The class keywork defines a class.

- Use the dot operator to access an object's properties and functions.

- A constructor runs you initialize an object.

- You can define a property in the primary constructor by prefixing a parameter with val or var. You can define a property outside the constructor by adding it to the class body.

- Initializer blocks run when an object is initialized.

- You must initialize each property before you use its value.

- Getters and setters let you get and set property values.

- Behind the scenes, the compiler adds a default getter and setter to every property.
