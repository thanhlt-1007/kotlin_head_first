# CHAPTER 08. nulls and exceptions

## Safe and Sound

## 1. How do you remove object references from variables

```KOTLIN
// As you're assigning a Wolf object to a variable,
// the compiler infers that the variable's type should also be Wolf
var w = Wolf()

// Remove the reference to this Wolf object
// ... and assign a reference to this one instead
w = Wolf()
```

## 2. Remove and object reference using null

```KOTLIN
w = null
```

### a. Why have nullable type?

```KOTLIN
// w is a Wolf?,
// which means it can hold references to Wolf objects,
// and null
var w: Wolf? = Wolf()

// Setting w to null removes the reference to the Wolf object.
w = null
```

## 3. You can use a nullable type everywhere you can use a non-nullable type

```KOTLIN
var src: String? = "Pizza"
```

```KOTLIN
// This is different to saying
// var str: String? = ""
// "" is a String object that contains no characters,
// whereas null is not a String object
var src: String? = null
```

```KOTLIN
fun printInt(x: Int?) {
  println(x)
}
```

```KOTLIN
// The function must return a value that's a Long or null
fun result() : Long? {
  // Code to calculated and return Long?
}
```

## 4. How to create an array of nullable types

```KOTLIN
var myArray: Array<String?> = arrayOf("Hi", "Hello")
var myArray = arrayOf("Hi", "Hello", null)
```

## 5. How to access a nullable type's functions and properties

```KOTLIN
var w: Wolf? = Wolf()

if (w != null) {
  // The compiler knows that w is not null,
  // so you can call the eat() function.
  w.eat()
}

if (w != null && w.hunger < 5) {
  // The right side of the && is only executed if the left side is true,
  // so here, the compiler knows that w can't be null,
  // and it allows you to call w.eat()
  w.eat()
}
```

```KOTLIN
class MyWolf {
  var w: Wolf? = Wolf()

  fun myFunction() {
    if (w != null) {
      // This won't compile because the compiler can't guarantee that some other code won't update the w property in between checking it's not null,
      // and its usage
      w.eat()
    }
  }
}
```

## 6. Keep things safe with safe calls

```KOTLIN
var w: Wolf? = Wolf()
// The ?. means that eat() is only called if w is not null.
w?.eat()
w?.hunger
```

## 7. You can chain safe calls together

```KOTLIN
class MyWolf {
  var w: Wolf? = Wolf()
}

var myWolf: MyWolf? = MyWolf()
// If myWolf is not null,
// and w is not null,
// get hunger.
// Otherwise, use null.
myWolf?.w?.hunger
```

### a. What happens when a safe call chain gets evaluated

## 8. The story continues

## 9. You can use safe calls to assign values ...

```KOTLIN
var x = w?.hunger
```
### a. ... and assign values to safe calls

```KOTLIN
// If w is not null,
// w?.hungger = 6
// sets w's hunger property to 6.
w?.hunger = 6
```

```KOTLIN
myWolf?.w?.hunger = 2
```

## 10. Use let to run code if values are not null

```KOTLIN
if (w != null) {
  println(w.hunger)
}
```

```KOTLIN
w?.let {
  // If w is not null, let's print its hunger
  // You can use "it" to directly access the Wolf's functions and properties.
  println(it.hunger)
}
```

## 11. Using let with an array items

```KOTLIN
var array = arrayOf("Hi", "Hello", null)
for (item in array) {
  item?.let {
    // This line only runs for non-null items in the array
    println(it)
  }
}
```

### a. Using let to streamline expressions

```KOTLIN
fun getAlphaWolf() : Wolf? {
  return Wolf()
}
```

```KOTLIN
var alpha = getAlphaWolf()
if (alpha != null) {
  alpha.eat()
}
```

```KOTLIN
// Using let is more concise.
// It's also safe, so you can use it in all situations.
getAlphaWolf()?.let {
  it.eat()
}
```

## 12. Instead of using an if expression...

```KOTLIN
if (w != null) w.hunger else -1
```

### a. .. you can use the safer Elvis operator

```KOTLIN
w?.hunger ?: -1
```

## 13. The !! operator deliberately throws a NullPointerException

```KOTLIN
// Here, the !! makes the assertion that w is not null.
var x = w!!.hunger
```

## 14. Create the Null Values project

```KOTLIN
class Wolf {
  var hunger = 10
  val food = "meat"

  fun eat() {
    println("The Wolf is eating $food")
  }
}

class MyWolf {
  var wolf: Wolf? = Wolf()

  fun myFunction() {
    wolf?.eat()
  }
}

fun getAlphaWolf() : Wolf? {
  return Wolf()
}
```

## 15. The code continued ...

```KOTLIN
fun main() {
  var w: Wolf? = Wolf()

  if (w != null) {
    w.eat()
  }

  var x = w?.hunger
  println("The value of x is $x")

  var y = w?.hunger ?: -1
  // Use the elvis operator to set y to the value of hunger if w is not null.
  // If w is null, it sets y to -1.
  println("The value of y is $y")

  val myWolf = MyWolf()
  myWolf?.wolf?.hunger = 8
  println("The value of myWolf?.wolf?.hunger is ${myWolf?.wolf?.hunger}")

  var myArray = arrayOf("Hi", "Hello", null)
  for (item in myArray) {
    item?.let { println(it) }
  }

  getAlphaWolf()?.let { it.eat() }

  w = null
  // This will thrown a NullPointerException as w is null.
  w!!.hunger
}
```

### a. Test drive

## 16. An exception is thrown in exceptional circumstances

### a. You can catch exceptions that are thrown

## 17. Catch exceptions using a try / catch

```KOTLIN
fun myFunction(str: String) {
  try {
    // Here's the try ...
    val x = str.toString()
    println(x)
  } catch (e: NumberFormatException) {
    // ... and here's the catch
    println("Bummer")
  }

  println("myFunction has ended")
}
```

## 18. Use finally for the things you want to do no matter what

```KOTLIN
try {
  turnOvenOn()
  x.bake()
} catch(e: BakingException) {
  println("Baking experiment failed")
} finally {
  // We always want to call turnOvenOff(),
  // so it belongs in the finally block.
  turnOvenOff()
}
```

## 19. An exception is an object of type Exception

```KOTLIN
try {
  // Do risky thing
} catch(e: Exception) {
  // printStackTrace() is a function that's available to all exceptions running on the JVM.
  // If you can't recover from an exception,
  // use printStackTrace() to help you track down the cause of the problem.
  e.printStackTrace()
  // Other code that runs when you get an exception
}
```

```KOTLIN
class AnimalException : Exception() {}
```

## 20. You can explicitly throw exceptions

```KOTLIN
fun setWorkRatePercentage(x: Int) {
  if (x !in 0..100) {
    // This throws an IllegalArgumentException if x is not in the range 0..100
    throw IllegalArgumentException("Percentage not in range 0..100: $x")
  }
  // More code that runs if the argument is invalid
}
```

```KOTLIN
try {
  setWorkRatePercentage(110)
} catch(e: IllegalArgumentException) {
  // The setWorkRatePercentage() function can't make anyone work at 100%,
  // so the caller has to deal with the problem.
  // Code to handle the exception
}
```

## 21. try and throw are both expressions.

## a. How to use try as an expression

```KOTLIN
// This is like saying Try to assign str.toInt() to result,
// but if you can't,
// set result to null.
val result = try { str.toInt() } catch(e: Exception) { null }
```

## b. How to use throw as an expression

```KOTLIN
var h = w?.hunger ?: throw AnimalExecption()
```

## 22. Code Magnets

## 23. Code Magnets Solution

## 24 Your Kotlin Toolbox

BULLET POINTS

- null is a value that means a variable doesn't hold a reference to an object. The variable exists, but it doesn't refer to anything.

- A nullable type can hold null values in addtional ti ots base type. You define a type as nullable by adding a ? to the end of it.

- To access a nullable variable's properties and functions, you must first check that it's not null.

- If the compiler can't guarantee that a variable is not null in between a null-check and its usage, you must access properties and functions using the safe call operator ?.

- You can chain safe calls together.

- To execute code if (and only if) a value is not null, use ?. let

- The Elvis operator ?: is safe alternative to an if expression.

- The not null assert operator !! throws a NullPointerException if the subject of your assertion is null.

- An exception is a warning that occurs in exceptional situations. It's an object of type Exception.

- Use throw to throw an exception.

- Catch an exception using try / catch / finally.

- try and throw are expressions.

- Use a safe case (as?) to avoid getting ClassCastException.
