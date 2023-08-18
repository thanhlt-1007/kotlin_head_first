# CHAPTER 05. subclasses and superclasses

## Using Your Inheritance

## 1. Inheritance helps you avoid duplicate code

### a. An inheritance example

## 2. What we're going to do

## 3. Design an animal class ingeritance structure

## 4. Use inheritance to avoid duplicate code in subclasses

## 5. What should the subclasses override?

### a. The animals have different property values

### b. ... and different function implementations

## 6. We can group some of the animals

## 7. Add Canine and Feline classes

## 8. Use IS-A to test your class hierarchy

### a. Use HAS-A to test for other relationships

## 9. The IS-A test works anywhere in the inheritance tree

## 10. We'll create some Kotlin animals

```KOTLIN
class Animal {
  // The Animal class has properties named image, food, habitat and hunger.
  val image = ""
  val food = ""
  val habitat = ""
  var hunger = 10

  fun makeNoise() {
    println("The Animal is making a noise")
  }

  fun eat() {
    println("The Animal is eating")
  }

  fun roam() {
    println("The Animal is roaming")
  }

  fun sleep() {
    println("The Animal is sleeping")
  }
}
```

## 11. Declare the superclass and its properties and functions as open

```KOTLIN
// We want to use the class as a superclass, so we need to declare it open
open class Animal {
  // We want to override the image, food and habitat properties,
  // so we've prefixed each one with open
  open val image = ""
  open val food = ""
  open val habitat = ""
  var hunger = 10

  // We've declared the makeNoise, eat and roam functions as open because we'll override them in our subclasses
  open fun makeNoise() {
    println("The Animal is making a noise")
  }

  open fun eat() {
    println("The Animal is eating")
  }

  open fun roam() {
    println("The Animal is roaming")
  }

  open fun sleep() {
    println("The Animal is sleeping")
  }
}
```

## 12. How a subclass inherits from a super class

```KOTLIN
// This is like saying "class Hippo is a subtype of class Animal".
// We'll add the Hippo class to our code a few pages ahead.
class Hippo : Animal() {
  // Hippo code goes here
}
```

```KOTLIN
// The Car constructor defines two properties: make and model.
class Car(val make: String, val model: String) {
  // Code for the Car class
}

// The ConvertibleCar constructor has two parameters: make_param and model_param.
// It passes the values of these parameters to the Car constructor,
// which initialize the make and model properties.
class ConvertibleCar(make_param: String, model_param: String) : Car(make_param, model_param) {
  // Code for the ConvertibleCar class
}
```

## 13. How (and when) to override properties

```KOTLIN
class Hippo : Animal() {
  // This overrides the image, food and habitat properties from the Animal class
  override val image = "hippo.jpg"
  override val food = "grass"
  override val habitat = "water"
}
```

```KOTLIN
open class Animal {
  // Here, image is defined using var,
  // and initialized with ""
  var image = ""
}

class Hippo : Animal() {
  init {
    // We're using the Hippo's initializer block to assign a new value to the image property.
    // In this case, there was no need to override the property.
    image = "hippo.jpg"
  }
}
```

## 14. Overriding properties lets you do more than assign default values

## 15. How to override fuinctions

```KOTLIN
class Hoppo : Animal() {
  override val image = "hippo.jpg"
  override val food = "grass"
  override val habitat = "water"

  override fun makeNoise() {
    println("Grunt! Grunt!")
  }

  override fun eat() {
    println("The Hippo is eating $food")
  }
}
```

### a. The rules for overriing functions

## 16. An override function or property stays open ...

```KOTLIN
open class Vehicle {
  open fun lowerTemperature() {
    // The Vehicle class define an open lowerTemperature() function
    println("Turn down temperature")
  }
}

open class Car : Vehicle() {
  override fun lowerTemperature() {
    // The lowerTemperature() function remain open the Car subclass, even though we're going overriding it ...
    println("Turn on air conditioning")
  }
}

class ConvertibleCar : Car() {
  override fun lowerTemterature() {
    // ... which mean that we can override it again in the ConvertibleCar class.
    println("Open roof")
  }
}
```

### a. ... until it's declared final

```KOTLIN
open class Car : Vehicle() {
  // Declaring the function as final in the Car class means that it can no loger be overriden in any of Car's subclasses
  final override fun lowerTemperature() {
    println("Turn on air conditioning")
  }
}
```

## 17. And the Hippo class to the Animals project

```KOTLIN
class Animal {
  open val image = ""
  open val food = ""
  open val habitat = ""
  var hunger = 10

  open fun makeNoise() {
    println("The Animal is making a noise")
  }

  open fun eat() {
    println("The Animal is eating")
  }

  open fun roam() {
    println("The Animal is roaming")
  }

  fun sleep() {
    println("The Animal is sleeping")
  }
}

class Hippo : Animal() {
  override val image = "hippo.jpg"
  override val food = "grass"
  override val habitat = "water"

  override fun makeNoise() {
    println("Grunt! Grunt!")
  }

  override fun eat() {
    println("The Hippo is eating $food")
  }
}
```

## 18. Code Magnets

## 19. Code Magnets Solution

## 20. Add the Canine and Wolf classes

```KOTLIN
open class Animal {
  ...
}

open class Hippo : Animal() {
  ...
}

open class Canine : Animal() {
  override fun roam() {
    println("The Canine is roaming")
  }
}

class Wolf : Canine() {
  override val image = "wolf.jpg"
  override val food = "meat"
  override val habitat = "forests"

  override fun makeNoise() {
    println("Hoooo0wl!")
  }

  override fun eat() {
    println("The Wolf is eating $food")
  }
}
```

## 21. Which function is called?

## 22. Inheritance guarantees that all subclasses have the functions and properties defined in the superclass

### a. Any place where you can use a superclass, you can use one of its subclass instead

```KOTLIN
var animal: Animal = Wolf()
```

## 23. When you call a function on the variable, it's the object's version that responds

```KOTLIN
var animal: Animal = Wolf()
// get's to respond in a Wolf-like way.
animal.eat()
```

```KOTLIN
// The compiler spots that these are all types of Animal,
// so it creates an array of type Array<Animal>
val animals = arrayOf(Hippo(),
                      Wolf(),
                      Lion(),
                      Cheetah(),
                      Lynx(),
                      Fox())

// This loops throigh the animals,
// and calls the roam() and eat() functions of each one.
// Each animal responds a way that's appropriate to its type.
for (animal in animals) {
  animal.roam()
  animal.eat()
}
```

## 24. You can use a supertype for a function's parameters and return type

```KOTLIN
class Vet() {
  fun giveShot(animal: Animal) {
    // Code to do something medical to the Animal that it won't like
    animal.makeNoise()
  }
}
```

```KOTLIN
val vet = Vet()
val wolf = Wolf()
val hippo = Hippo()

// Wolf and Hippo are both types of Animal
// so you can pass Wolf and Hippo objects as arguments to the giveShot function.
vet.giveSHot(wolf)
vet.giveShot(hippo)
```

## 25. The updated Animals code

### a. Test drive

## 26. Your Kotlin Toolbox

BULLET POINTS

- A superclass contains common properties and functions that are inherited by one or more subclasses.

- A subclass can include extra properties and functions that aren't in the superclass, and can override the things in inherits.

- Use the IS-A test to verify that your inheritance is valid. If X is a subclass of Y, then X IS-A Y must make sense.

- The IS-A relationships works in only one direction. A Hippo is an Animal, but not all Animals are Hippos.

- If class B is a subclass of class A, and class C is a subclass of class B, class C passes the IS-A test for both B and A.

- Before you can use a class as a superclass, you must declare it open. You must also declare any properties and functions you want to override as open.

- Use : to specify a subclass's superclass.

- If the superclass has a primary constructor, then you must call it in the subclass header.

- Override properties and functions in the subclass by prefixing them with override. When you override a property, its type must be compatible with that if the superclass property. When you override a function, its parameter list must stay them same, and its return type must be compatible with that of the super class.

- Overridden functions and properties stay open until they're declared final.

- When a function is overriden in a subclass, and that function is invoked on an instamce of the subclass, the overridden version of the function is called.

- Inheritance guarantees that all subclasses have the functions and properties defined in the superclass.

- You can use a subclass in any place where the superclass type in expected.

- Polymorphism means "many forms". It allows different subclasses to have different implementations of the same function.
