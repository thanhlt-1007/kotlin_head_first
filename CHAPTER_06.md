# CHAPTER 06. abstract classes and interfaces

## Serious Polymorphism

## 1. The Animal class hierarchy revisited

## 2. Some classes shouldn't be instantiated

### a. Declare a class as abstract to stop it from being instantiated

```KOTLIN
// Prefix class with "abstract" to make it an abstract class.
abstract class Animal {
  ...
}
```

```KOTLIN
var animal: Animal
animal = Wolf()
animal = Animal() // You can't create Animal objects.
```

## 3. Abstract or concrete?

## 4. An abstract class can have abstract properties and fucntions

### a. We can mark three properties as abstract

```KOTLIN
abstract class Animal {
  // Here, we've marked the image, food and habitat properties as abstract
  abstract val image: String
  abstract val food: String
  abstract val habitat: String
}
```

## 5. The Animal class has two abstract functions

```KOTLIN
abstract class Animal {
  ...
  abstract fun makeNoise()

  abstract fun eat()

  open fun roam() {
    println("The Animal is roaming")
  }

  fun sleep() {
    println("The Animal is sleeping")
  }
}
```

## 6. How to implement an abstract class

```KOTLIN
class Hippo : Animal() {
  override val image = "hippo.jpg"
  override val food = "grass"
  override val habitat = "water"

  override fun makeNoise() {
    println("Grunt! Grunt!")
  }

  override fun eat() {
    println("The Hippo is eaating $food")
  }
}
```

## 7. You MUST implement all abstract properties and functions

## 8.Let's update the Animals project

### a. Test drive

## 9. Independent classes can have common behavior

## 10. An interface lets you define common behavior OUTSIDE a superclass hierachy

## 11. Let's define the Roamable interface

### a. Interface functions can be abstract or concrete

```KOTLIN
// "interface" means it's an interface
// "Roamable" the name of the interface
// { opening brace of the interface
// } closing brace of the interface
interface Roamable {
  // the roam function
  fun roam()
}
```

### a. Interface functions can be abstract or concrete

```KOTLIN
interface Roamable {
  // This is how you define an abstract function in an interface.
  fun roam()
}
```

```KOTLIN
interface Roamable {
  // To add a concrete function to an interface,
  // simply give it a body
  fun roam() {
    println("The Roamable is roaming")
  }
}
```

## 12. How to define interface properties

```KOTLIN
interface Roamable {
  // Just á with abstract functions,
  // there's no need to prefix an abstract property with the abstract keyword.
  val velocity: Int
}
```

```KOTLIN
interface Roamable {
  val velocity: Int
      // This returns a value ò 20 whenever the property is accessed.
      // But you can still override the property in any class that implements the interface.
      get() = 20
}
```

```KOTLIN
interface Roamable {
  var velocity: Int
      get() = 20
      set(value) {
        // If you try to write code like this in an interface,
        // it won't compile.
        // This is because you can't use the "field" keyword in an interface
        // so you can't update the underlying value of the property
        field = value
      }
}
```

```KOTLIN
interface Roamable {
  var velocity: Int
      get() = 20
      set(value) {
        // This code compiles because you're not using the field keywork
        // But it won't update the underlying value of the property.
        println("Unable to update velocity")
      }
}
```

## 13. Declare that a class implements as interface ...

```KOTLIN
// This is like saying "The Vehicle class implements the Roamable interface"
class Vehicle : Roamable {
  ...
}
```

### a. ... then override its properties and functions

```KOTLIN
class Vehicle : Roamable {
  // This code overrides the roam() function that the Vehicle class interits from the Roamable interface.
  override fun roam() {
    println("The Vehicle is roaming")
  }
}
```

## 14. How to implement multiple interfaces

```KOTLIN
// Class X implements the A and B interfaces.
class X : A, B {
  ...
}
```

```KOTLIN
// Class Y inherits from class C,
// and implements interface A.
class Y : C(), A {
  ...
}
```

```KOTLIN
interface A {
  fun myFunction() { println("from A") }
}

interface B {
  fun myFunction() { println("from B") }
}

class X : A, B {
  override fun myFunction() {
    // This code calls the version of myFunction defined in A,
    // then the version defined in B.
    // It then runs code that's specific to class X.

    super<A>.myFunction()
    super<B>.myFunction()
    // Extra code specific to class X
  }
}
```

## 15. How do you know whether the make a class, a subclass, an abstract class, or an interface?

## 16. Update the Animals project

### a. Test drive

## 17. Interfaces let you polymorphism

```KOTLIN
// This line create an array of Roamable objects
vak roamables = arratOf(Hippo(),
                        Wolf(),
                        Vehicle())
for (roamable in roamables) {
  // As the roamable array holds Roamable objects,
  // this means that the item variable is of type Roamable.
  roamable.roam()
}
```

### a. Access uncommon behavior by checking an object's type

```KOTLIN
val animal: Animal = Wolf()
if (animal is Wolf) {
  // The compiler knows that the object is a Wolf,
  // so call its eat() function.
  animal.eat()
}
```

```KOTLIN
val roamables = arrayOf(Hippo(),
                        Wolf(),
                        Vehicle())
for (item in roamables) {
  item.roam()
  if (item is Animal) {
    // If the item is an Animal,
    // the compiler knows it can call the item's eat() function
    item.eat()
  }
}
```

## 18. Where to use the is operator

### a. As the condition for an if

```KOTLIN
val str = if (animal is Wolf) "Wolf" else "not Wolf"
```

### b. In condition using && and ||

```KOTLIN
// The right side of the if condition only runs if roamable is an Animal so we can access its hunger property.
if (roamable is Animal && roamable.hunger < 5> {
  // Code to deal with a hungry Animal
})
```

```KOTLIN
// Remember the right side of an || condition only tuns if the left side is false.
// Therefore, the right side can only run if roamable is an Animal
if (roamable !is Animal || roamable.hunger >= 5) {
  // Code to deal with a non-Animal,
  // or with a non-hungry Animal
}
```

### c. In a while loop

```KOTLIN
while (animal is Wolf) {
  // Code that runs while the Animal is a Wolf
}
```

## 19. Use when to compare a value against a bunch of options

```KOTLIN
// Check the value of variable x
when (x)
  // when x is 0, run this code
  0 -> println("x is zero")
  // Run this code when x is 1 or 2
  1, 2 -> println("x is 1 or 2")
  // When statement can have an else clause
  else -> {
    // Run this block of code when x is some other value.
    println("x is neither 0, 1 nor 2")
    println("x is some other value")
  }
```

```KOTLIN
// Check the value of roamable
when (roamble) {
  is Wolf -> {
    // Wolf-specific code
  }
  is Hippo -> {
    // Hippo-specific code
  }
  is Animal -> {
    // This code will only run if roamable is a type of Animal that's not Wolf or Hippo.
    // Code that runs if roamable is some other Animal
  }
}
```

## 20. The is operator usually performs a smart cast

```KOTLIN
if (item is Wolf) {
  // item is smart case to a Wolf for the duration of this code block
  item.eat()
  item.makeNoise()
}
```

```KOTLIN
class MyRoamable {
  var r: Roamable = Wolf()

  fun myFunction() {
    if (r is Wolf) {
      // The compiler can't smart case the Roamable property r to a Wolf.
      // This is because the compiler can't gurantee that some other code won't update the property in between checking its type and its usage.
      // The code therefore won't compile.
      r.eat()
    }
  }
}
```

## 21. Use as to perform an explicit cast

```KOTLIN
// This code explicitly casts the object to a Wolf so that you can call its Wolf functions.
var wolf = r as Wolf
wolf.eat()
```

```KOTLIN
// If r is a Wolf,
// cast it as a Wolf and call its eat() function.
if (r is Wolf) {
  var wolf = r as Wolf
  wolf.eat()
}
```

## 22. Update the Animals project

### a. Test drive

## 23. Your Kotlin toolbox

BULLET POINTS

- An abstract class can't be instantiated. It can contain both abstract and non-abstract properties and functions.

- Any class that contains an abstract property or function must be declared abstract.

- A class that's not abstract is called concrete.

- You implement abstract properties and functions by overriding them.

- All abstract properties and functions must be overridden in any concrete subclasses.

- An interface lets you define common behavior outside a superclass hierarchy so that independent classes can still benefit from polymorphism.

- Interfaces can have abstract or non-abstract functions.

- Interfaces properties can be abstract, or they can have getters and setters. They can't be initialized, and they don't have access to a backing field.

- A class can implement multiple interfaces.

- If a subclass inherits from a superclass (or implements an interface) named A, you can use the code:

  ```KOTLIN
  super<A>.myFunction()
  ```

to call the implementation of myFunction that's defined in A.

- If a variable holds a reference to an object, you can use the is operator to check the type of the underlying object.

- The is operator performs a smart case when the compiler can guarantee that the underlying object can't have changed between the type check and its usage.

- The as operator lets you perform an explicit cast.

- A when operator lets you perform an explicit cast.

- A when expression lets you compare a variable against an exhaustive set of different options.
