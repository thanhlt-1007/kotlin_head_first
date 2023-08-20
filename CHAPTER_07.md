# CHAPTER 07. data classes

## Dealing with Data

## 1. == calls a function named equals

```KOTLIN
// w1 and w2 refer to the same object
val w1 = Wolf()
val w2 = w1
// so w1 == w2 is true
w1 == w2
```

```KOTLIN
// w1 and w2 refer to different objects,
val w1 = Wolf()
val w2 = Wolf()
// so w1 == w2 is false
x1 == x2 // false
```

## 2. equals is inherit from a superclass named Any

```KOTLIN
class MyClass {
  ...
}
```

```KOTLIN
// The compiler secretly makes each class a subclass of Any
class MyClass : Any() {
  ...
}
```

### a. The important of being Any

```KOTLIN
// The compiler spots that each object in the array has a common supertype of Any,
// so it creates an array of type Array<Any>
val myArray = arrayOf(Car(), Guitar(), Giraffe())
```

## 3. The common behavior defined by Any

```KOTLIN
val w1 = Wolf()
val w2 = Wolf()
// equals returns false because w1 and w2 hold references to different object.
println(w1.equals(w2))

vak w1 = Wolf()
val w2 = w1
// equals returns true because w1 and w2 hold references to the same object.
// It's the same as testing w1 == w2
println(w1.equals(w2))
```

```KOTLIN
val w = Wolf()
// 523429237
// This is value of w's hash code
println(w.hashCode())
```

```KOTLIN
val w = Wolf()
// Wolf@1f32e575
println(w.toString())
```

## 4. We might want equals to check whether two objects are equivalent

```KOTLIN
class Recipe(val title: String, val isVegetarian: Boolean) {
  ...
}

val v1 = Recipe("Chicken Bhuna", false)
val v2 = Recipe("Chicken Bhuna", false)
```

## 5. A data class lets you create data objects

```KOTLIN
// The data pregix turns a normal class into a data class
data class Recipe(val title: String, val isVegetarian: Boolean) {
  ...
}
```

### a. How to create objects from a data class

```KOTLIN
// r1 and r2 are considered "equal" as the two Recipe objects hold the same data
val r1 = Recipe("Chicken Bhuna", false)
val r2 = Recipe("Chicken Bhuna", false)
// r1 == r2 is true
r1 == r2
```

## 6. Data classes override their inherited behavior

### a. The equals function compare property values

```KOTLIN
val r1 = Recipe("Chicken Bhuna", false)
val r2 = Recipe("Chicken Bhuna", false)
println(r1.equals(r2)) // true
```

### b. Equal objects return the same hashCode value

```KOTLIN
val r1 = Recipe("Chicken Bhuna", false)
val r2 = Recipe("Chicken Bhuna", false)
println(r1.hashCode()) // 241131113
println(r1.hashCode()) // 241131113
```

### c. toString returns the value of each property

```KOTLIN
val r1 = Recipe("Chicken Bhuna", false)
// Recipe(title=Chicken Bhuna, isVegetarian=false)
println(r1.toString())
```

## 7. Copy data objects using the copy function

```KOTLIN
val r1 = Recipe("Thai Curry", false)
// This copies r1's object,
// changing the value of the isVegerarian property to true
val r2 = r1.copy(isVegetarian = true)
```

## 8. Data classes define componentN functions ...

```KOTLIN
val r = Recipe("Chicken Bhuna", false)
// component1() returns the reference hold by the first property defined in the data class constructor
val title = r.component1()
// this does the same thing as code:
val title = r.title
```

### a. ... that let you destructure data objects

```KOTLIN
val title = r.title
vak vegetarian = r.isVegetarian
// Assigns the value of r's first property to title,
// and the value of its second property to vegetarian.
val (title, vegetarian) = r
// It does the same thing as the code
val title = r.component1()
vak vegetarian = r.component2()
```

## 9. Create Recipes project

### a. Test drive

## 10. Generated functions only use properties defined in the constructor

```KOTLIN
data class Recipe(val title: String, val isVegetarian: Boolean) {
  var mainIngredient = ""
}
```

```KOTLIN
val r1 = Recipe("Thai curry", false)
r1.mainIngredient = "Chicken"

val r2 = Recipe("Thai curry", false)
r2.mainIngredient = "Duck"

// evaluates to true
println(r1 == r2)
```

## 11. Initializing many properties can lead to cumbersome code

```KOTLIN
data class Recipe(val title: String,
                  val mainIngredient: String,
                  val isVegetarian: Boolean,
                  val difficult: String) {
  ...
}

val r = Recipe("Thai curry", "Chicken", "false", "Easy")
```

### a. Default parameter values to the rescue!

```KOTLIN
data class Recipe(val title: String,
                  val mainIngredient: String,
                  val isVegetarian: Boolean = false,  // isVegetarian has a default value of false.
                  val difficult: String = "Easy")     // difficult has a default value of "Easy".
```

## 12. How to use a constructor default's value

### a. Passing values in order of declaration

```KOTLIN
// We've not specified values for the isVegetarian and difficulty property values,
// so the object uses their default values.
val r = Recipe("Spaghetti Bolognese", "Beef")
```

```KOTLIN
// Assigns isVegetarian a value of true, and uses the default value for the difficulty property.
val r = Recipe("Spaghetti Bolognese", "Beef", "Tofu", true)
```

```KOTLIN
// This code won't compile, as the compiler expects the third argument to be a Boolean
val r = Recipe("Spaghetti Bolognese", "Beef", "Moderate")
```

### b. Using named arguments

```KOTLIN
// This specifies the name of each property,
// and the value it should have.
val r = Recipe(title = "Spaghetti Bolognese", mainIngredient = "Beef")
```

```KOTLIN
// With named arguments, the order in which you specify the value of each property doesn't matter.
val r = Recipe(mainIngredient = "Beef", title = "Spaghetti Bolognese")
```

## 13. Functions can use default values too

```KOTLIN
fun findRecipes(title: String
                ingredient: String,
                isVegetarian: Boolean,
                difficulty: String) : Array<Recipe> {
  // Code to find recipes
}
```

```KOTLIN
val recipes = findRecipes("Thai curry", "", false, "")
```

```KOTLIN
// This is the same function as the one above,
// but this time, we've give each parameter a default value.
fun findRecipes(title: String = ""
                ingredient: String = "",
                isVegetarian: Boolean = false,
                difficulty: String = "") : Array<Recipe> {
  // Code to find recipes
}
```

```KOTLIN
// Both of these call the finRecipes function,
// using a value of "Thai curry" for the title argument
val recipes = findRecipes("Thai curry")
val recipes = findRecipes(title = "Thai curry")
```

## 14. Overloading a function

```KOTLIN
fun addNUmbers(a: Int, b: Int) : Int {
  return a + b
}
```

```KOTLIN
// This is an overloaded version of the same function that uses Doubles instead of Ints
fun addNumbers(a: Double, b: Double) : Double {
  return a + b
}
```

### a. Dos and don'ts for function overloading:

## 14. Let's update the Recipes project

```KOTLIN
// Assign default values to the isVegetarian and difficulty properties.
data class Recipe(val title: String,
                  val mainIngredient: Boolean = false,
                  val isVegetarian: Boolean = false,
                  val difficulty: String = "Easy") {

}

// This is an example of a class with secondary constructor,
// just so that you can see one in action
class Mushroom(val size: Int,
               val isMagic: Boolean) {
  constructor(isMagicParam: Boolean) : this(0, isMagicParam) {
    // Code that runs when the secondary constructor is called
  }
}

// These are overloaded functions
fun addNumbers(a: Int, b: Int) : Int {
  return a + b
}

fun addNumbers(a: Double, b: Double) : Double {
  return a + b
}
```

## 15. The code continued ...

### a. Test drive

## 16. Your Kotlin Toolbox

BULLET POINTS

- The behavior of the == operator is determineed by the implementation of the equals function.

- Every class inherits an equals, hashCode and toString function from the Any class because every class is a subclass of Any. These functions can be overriden.

- The equals function tells you if two objects are considered "equals". By default, it returns true if it's used to test the same underlying object, and false if it's used to test separate objects.

- The === operator lets you check whether two variables refer to the same underlying object irrespective of the object's type.

- A data class lets you create objects whose main purpose is to store data. It automatically overrides the equals, hashCode and toString functions, and includes cope and componentN functions.

- The data class equals function checks for equality by looking at each object's property values. If two data objects hold the same data, the equals functions returns true.

- The copy function lets you create a new copy of a data object, alerting some of its properties. The original remains intact.

- componentN functions let you destructure data obejcts into their component property values.

- A data class generate its functions by considering the properties defined in its primary constructor.

- Constructors and functions can have default parameter values. You can call a constructor or function by passing parameter values in order of declaration or by using named arguments.

- Classes can have secondary constructors.

- An overloaded function is a different function that happens to have the same function name. An overload function must have different arguments, but may have a different return type.

RULES FOR DATA CLASS

- There must be a primary constructor.

- The primary constructor must define one or more parameters.

- Each parameter must be marked as val or var.

- Data classes must not be open or abstract.
