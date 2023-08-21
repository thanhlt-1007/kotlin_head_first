# CHAPTER 09. collections

## Get Organized

## 1. Arrays can be useful..

```KOTLIN
var array = arrayOf(1, 3, 2)

// Create an array of size 2 initialized will null values.
// It's like saying: arrayOf(null, null)
var nullArray: Array<String?> = arrayOfNulls(2)

// array has space for three items,
// so its size is 3
val size = array.size

// Flips the order of the items in the array
array.reverse()

// array contains 1,
// so this returns true
val isIn = array.contains(1)

// This return as 2 + 3 + 1 = 6
val sum array.sum()

// This returns a Double - in thif case,
// (2 + 3 + 1) / 3 = 2.0
val average = array.average()

// min() returns 1, as this is the lowest value in the array.
// max() returns 3 as this is the highest.
array.min()
array.max()

// Changes the order of the items in array so they go from the lowest value to the highest,
// or from false to true
array.sort()
```

## 2. ... but there are things an array can't handle

### a. You can't change an array's size

### b. Array are mutable, so they can be updated

## 3. When in doubt, fo to the Library

## 4. List, Set and Map

### a. List - when sequence metters

### b. Set - when uniqueness metters

### c. Map - when finding something by key matters

## 5. Fantastic Lists ...

```KOTLIN
// The code creates a List containing String values of "Tea", "Eggs" and "Milk"
// The variable has a type of List<String>,
// so the List contains references to String objects.
val shopping = listOf("Tea", "Eggs", "Milk")
val shopping: List<String>
shopping = listOf("Tea", "Eggs", "Milk")
```

### a. ... and how to use them

```KOTLIN
// It's a good idea to check the size of the List first
// because get() will throw an ArrayIndexOutOfBoundsException
// if it's passed an invalid index.
if (shopping.size > 0) {
  println(shopping.get(0))
  // Prints "Tea"
}
```

```KOTLIN
for (item in shopping) println(item)
```

```KOTLIN
if (shopping.contains("Milk")) {
  println(shopping.indexOf("Milk"))
  // Prints 2
}
```

## 6. Create a MutableList ...

```KOTLIN
// If you pass String values to the mutableListOf() function,
// the compiler infers that you want an object of type MutableList<String> (a MutableList that holds Strings).
val mShopping = mutableListOf("Tea", "Eggs")
```

### a. ... and add values to it

```KOTLIN
mShopping.add("Milk")
```

```KOTLIN
mShopping.add(1, "Milk")
```

## 7. You can remove a value ...

```KOTLIN
if (mShopping.contains("Milk")) {
  mShopping.remove("Milk")
}
```

```KOTLIN
if (mShopping.size > 1) {
  mShopping.removeAt(1)
}
```

### a. ... and replace one value with another

```KOTLIN
if (mShopping.size > 0) {
  mShopping.set(0, "Coffee")
}
```

## 8. You can change the order and make nulk changes ...

```KOTLIN
// Together, these lines sort the MutableList in reverse order.
mShopping.sort()
mShopping.reverse()
mShopping.shuffle()
```

```KOTLIN
val toAdd = listOf("Cookies", "Sugar")
mShopping.addAll(toAdd)
```

```KOTLIN
val toRemove = listOf("Milk", "Sugar")
mShopping.removeAll(toRemove)
```

```KOTLIN
val toRetain = listOf("Milk", "Sugar")
mShopping.retainAll(toRetain)
```

```KOTLIN
// This empty mShopping so its size is 0
mShopping.clear()
```

### a. ... or take a copy of the entire MutableList

```KOTLIN
val shoppingCopy = mShopping.toList()
```

## 9. Create the Collections project

### a. Test drive

## 10. Code Magnets

## 11. Code Magnets Solution

## 12. Lists allow duplicate values

```KOTLIN
// Here, there are three friends named Jim, Sue and Nick,
// but Sue and Nick are listed twice
val friendList = listOf("Jim",
                        "Sue",
                        "Sue",
                        "Nick",
                        "Nick")
friendList.size // 5
```

## 13. How to create a Set

```KOTLIN
// The code creates a Set containing the three String values.
// The values in a Set have no order, and duplicate value aren't allowed
val friendSet = setOf("Jim", "Sue", "Nick")
```

### a. How to use a Set's values

```KOTLIN
// This returns true if friendSet hash a "Fred" value,
// and false if it doesn't
val isFredGoing = friendSet.contains("Fred")
```

```KOTLIN
for (item in friendSet) println(item)
```

## 14. How a Set checks for duplicates

## 15. Hash code and equality

### a. Equality using the === operator

### b. Equality using the == operator

## 16. Rules for overriding hashCode and equals

## 17. How to use a MutableSet

```KOTLIN
val mFriendSet = mutableSetOf("Jim", "Sue")
mFriendSet.add("Nick")
mFriendSet.remove("Nick")
```

```KOTLIN
// addAll() adds the values held in another Set
val toAdd = setOf("Joe", "Mia")
mFriendSet.addAll(toAdd)
```

```KOTLIN
mFriendSet.clear()
```

## 18. You can copy a MutableSet

```KOTLIN
val friendSetCopy = mFriendSet.toSet()
val friendList = mFriendSet.toList()
val shoppingSet = mShopping.toSet()
```

## 19. Update the Collections project

### a. Test drive

## 20. Time for Map

### a. How to create a Map

```KOTLIN
val r1 = Recipe("Chicken Soup")
val r2 = Recipe("Quinoa Salad")
val r3 = Recipe("Thai Curry")

// Each entry takes the form Key to Value.
// The keys are normally Strings,
// as in this example
val recipeMap = mapOf("Recipe1" tp r1, "Recipe2" to r2, "Recipe3" to e3)
```

```KOTLIN
val recipeMap: Map<String, Recipe>
```

## 21. How to use a Map

```KOTLIN
recipeMap.containsKey("Recipe1")
```

```KOTLIN
val recipeToCheck = Recipe("Chicken Soup")
if (recipeMap.containsValue(recipeToCheck)) {
  // Code that runs if the Map contains the value
}
```

```KOTLIN
if (recipeMap.containsKey("Recipe1")) {
  // If recipeMap doesn't contain a "Recipe1" key,
  // this line will throw an exception.
  val recipe = recipeMap.getValue("Recipe1")
  // Code to use the Recipe object
}
```

```KOTLIN
for((key, value) in recipeMap) {
  println("Key is $key, value is $value")
}
```

## 22. Create a MutableMap

```KOTLIN
var r1 = Recipe("Chicken Soup")
var r1 = Recipe("Quinoa Salad")

val mRecipeMap = mutableMapOf("Recipe1" to r1, "Recipe2" to r2)
```

### a. Put entries in a MutableMap

```KOTLIN
val r3 = Recipe("Thai curry")
// Specify the key first,
// then the value
mRecipeMap.put("Recipe3", r3)
```

```KOTLIN
val r4 = Recipe("Jambalaya")
val r5 = Recipe("Sausage Rolls")
val recipesToAdd = mapOf("Recipe4" to r4, "Recipe5" to r5)
mRecipeMap.putAll(recipesToAdd)
```

## 23. You can remove entries from a MutableMap

```KOTLIN
// Remove the entry with a key of "Recipe2"
mRecipeMap.remove("Recipe2")
```

```KOTLIN
val recipeToRemove = Recipe("Quinoa Salad")
// Remove the entry with a key of "Recipe2",
// but only if its a value is a Quinoa Salad
mRecipeMap.remove("Recipe2", recipeToRemove)
```

```KOTLIN
mRecipeMap.clear()
```

## 24. You can copy Maps to MutableMaps

```KOTLIN
val recipeMapCopy = mRecipeMap.toMap()
val recipeList = mRecipeMap.toList()
```

```KOTLIN
val recipeEntries = mRecipeMap.entries
```

## 25. The full code for the Collections project

### a. Test drive

## 26. Your Kotlin Toolbox

BULLET POINTS

- Create an array initialized with null values using the arrayOfNuls function.

- Useful array functions include: sort, reverse, contains, min, max, sum, average.

- The Kotlin Standard Library contains pre-built classes and functions grouped into packages.

- A List is a collection that knows and cares about index position. It can contain duplicate values.

- A Set is an unordered collection that doesn't allow suplicate values.

- A Map is a collection that uses key/value is pairs. It can contain duplicate values, but not duplicate keys.

- List, Set and Map are immutable. MutableList, MutableSet and MutableMap are mutable subtypes of these collections.

- Create a List using listOf function.

- Create a MutableList using mutableListOf.

- Create a Set using the setOf function.

- Create a MutableSet using mutableSetOf.

- A Set checks for suplicates by first looking for matching hash code values. It then uses the === and == operators to check for referential or object equality.

- Create a Map using the mapOf function, passing in key / value pairs.

- Create a MutableMap using mutableMapOf.
