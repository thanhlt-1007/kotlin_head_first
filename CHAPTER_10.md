# CHAPTER 10. generics

## Know Your Ins from Your Outs

## 1. Collections use generics

```KOTLIN
val x: MutableList<String>
```

## 2. How a MutableList is defined

### a. Understanding collection documentation (Or, what's the meaning of "E")

```KOTLIN
// The "E" is a placeholder for the READ type you use when you declare a MutableList.
// MutableList inherits from the List and MutableCollection interfaces.
// Whatever type (the value of "E") you specify for the MutableList is automatically used for the type of the List and MutableCollection.
interface MutableList<E> : List<E>, MutableCollection<E> {
  // Whatever "E" is determine what kind of things you're allowed to add to the MutableList
  fun add(index: Int, element: E) : Unit {
    // More code
  }
}
```

## 3. Using type parameters with MutableList

```KOTLIN
val x: MutableList<String>
```

```KOTLIN
interface MutableList<E> : List<E>, MutableCollection<E> {
  fun add(index: Int, element: E) : Unit {
    // More code
  }
}
```

```KOTLIN
interface MutableList<String> : List<String>, MutableCollection<String> {
  fun add(index: Int, element: String) : Unit {
    // More code
  }
}
```

## 4. Things you can do with a generic class or interface

```KOTLIN
val duckList: MutableList<Duck>
duckList = mutableListOf(Duck("Donald"), Duck("Daisy"), Duck("Daffy"))

val list = mutableListOf("Fee", "Fi", "Fum")
```

```KOTLIN
fun quack(ducks: MutableList<Duck>) {
  // Code to make the Ducks quack
}
```

```KOTLIN
fun getDucks(breed: String) : MutableList<Duck> {
  // Code to get Ducks for the special breed
}
```

## 5. Here's what we're going to do

## 6. Create the Pet class hierachy

```KOTLIN
// Each subtype of Pet has a name (which it inherits from Pet),
// which gets set in the class constructor.
abstract class Pet(var name: String)

class Cat(name: String) : Pet(name)

class Dog(name: String) : Pet(name)

class Fish(name: String) : Pet(name)
```

## 7. Define the Contest class

### a. Declare that Contest uses a generic type

```KOTLIN
// The <T> after the class name tells the compiler that T is a generic type.
class Contest<T> {
  // More code here
}
```

### b. You can restrict T to a specific supertype

```KOTLIN
// T is a generic type that must be a Pet,
// or one of its subtypes.
class Contest<T: Pet> {
  // More code here
}
```

## 8. Add the scores property

```KOTLIN
class Contest<T: Pet> {
  // This defines a MutableMap with T keys,
  // and Int values, where T is the generic type of Pet that the Contest is dealing with
  val scores: MutableMap<T, Int> = mutableMapOf()
  // More code here
}
```

### a. Create the addScore function

```KOTLIN
class Contest<T: Pet> {
  val scores: MutableMap<T, Int> = mutableMapOf()

  fun addScore(t: T, score: Int) {
    // Put the contestant and its score in the MutableMap,
    // so long as the score is greater than or equal to 0.
    if (score >= 0) scores.put(t, score)
  }

  // More code goes here
}
```

## 9. Create the getWinners function

```KOTLIN
fun getWinners() : MutableSet<T> {
  // Get the hightest value from scores/
  val highScore = scores.values.max()
  val winners: MutableSet<T> = mutableSetOf()
  for((t, score) in scores) {
    // Add any contestant with the highest score to a MutableSet
    if (score == highScore) winners.add(t)
  }
  return winners
}
```

## 10. Create some Contest objects

```KOTLIN
// This create a Contest that will accept Cats.
val catContest = Contest<Cat>()
catContest.addScore(Cat(), 50)
catContest.addScore(Cat(), 50)

// getWinners() return a MutableSet<Cat>
// because we've specified that catContest must deal with Cats.
val topCat = catContest.getWinners().first()
```

```KOTLIN
// This compiler prevents you from adding non-Cats to a Contest<Cast>,
// so this line won't compile
catContest.addScore(Dog("Fido", 23))
```

```KOTLIN
val petContest = Contest<Pet>()
// As a Contest<Pet> deals with Pets,
// contestants can be any subtype of Pet
petContest.addScore(Cat("Fuzz Lightyear"), 50)
petContest.addScore(Fish("Finny MbGraw"), 56)
```

## a. The compiler can infer the generic type

## 11. Create the Generics project

### a. Test drive

## 12. The Retailer hierarchy

## 13. Define the Retailer interface

```KOTLIN
interface Retailer<T> {
  fun sellf(): T
}
```

```KOTLIN
// The CatRetailer class implements the Retailer interface so that it deals with Cats.
// This means that the sell() function must return a Cat.
class CatRetailer : Retailer<Cat> {
  override fun sell() : Cat {
    println("Sell Cat")
    return Cat("")
  }
}

// DogRetailer replaces Retailer's generic type with Dog, so its sell() function must return a Dog.
class DogRetailer : Retailer<Dog> {
  override fun sell() : Dog {
    println("Sell Dog")
    return Dog("")
  }
}

class CatRetailer : Retailer<Cat> {
  // This code won't compile
  // because CatRetailer's sell() function must return a Cat,
  // and a Dog is not a type of Cat
  override fun self(): Dog = Dog("")
}
```

## 14. We can create CatRetailer, DogRetailer and FishRetailer objects ...

```KOTLIN
val catRetailer1 = CatRetailer()
val catRetailer2: CatRetailer = CatRetailer()
```

### a. ... but what about polymorphism

```KOTLIN
// These lines are legal
// because DogRetailer implements Retailer<Dog>,
// and CatRetailer implements Retailer<Cat>.
val dogRetailer: Retailer<Dog> = DogRetailer()
val catRetailer: Retailer<Cat> = CatRetailer()
```

```KOTLIN
// This won't compile,
// even though CatRetailer is a Retailer<Cat>,
// and Cat is a subtype of Pet.
val petRetailer: Retailer<Pet> = CatRetailer()
```

## 15. Use out to make a generic type convariant

```KOTLIN
// Here's the out prefix
interface Retailer<out T> {
  fun sell() : T
}
```

```KOTLIN
// The out prefix in Retailer interface means that we can now assign a Retailer<Cat> to a Retailer<Pet> variable.
val petRetailer: Retailer<Pet> = CatRetailer()
```

### a. Collections are defined using convariant types

```KOTLIN
public interface List<out E> ... { ... }
```

```KOTLIN
val catList: List<Cat> = listOf(Cat(""), Cat(""))
val petList: List<Pet> = catList
```

## 16. Update the Generics project

### a. Test drive

## 17. We need a Vet class

```KOTLIN
class Vet<T: Pet> {
  fun treat(t: T) {
    println("Treat Pet ${t.name}")
  }
}
```

### a. Assign a Vet to a Contest

```KOTLIN
class Contest<T: Pet>(var vet: Vet) {
  val scores: MutableMap<T, Int> = mutableMapOf()

  fun addScore(t: T, score: Int = 0) {
    if (score >= 0) scores.put(t, score)
  }

  fun getWinners() :MutableSet<T> {
    val winners: MutableSet<T> = mutableSetOf()
    val highScore = scores.values.max()
    for((t, score) in scores) {
      if (score == highScore) winners.add(t)
    }
    return winners
  }
}
```

## 18. Create Vet objects

```KOTLIN
val catVet = Vet<Cat>()
val fishVet = Vet<Fish>()
val petVet = Vet<Pet>()
```

```KOTLIN
// A Vet<Cat> and a Vet<Pet> can both treat Cats
catVet.treat(Cat("Fuzz Lightyear"))
petVet.treat(Cat("Katsu"))
// A Vet<Pet> can treats a Fish
petVet.treat(Fish("Finny McGraw"))
// This line won't compile, as a Vet<Cat> can't treat a Fish.
catVet.treat(Fish("Finny McGraw"))
```

### a. Pass a Vet to the Contest constructor

```KOTLIN
val catContest = Contest<Cat>(catVet)
val petContest = Contest<Pet>(petVet)

// Even though a Vet<Pet> can trat Cats,
// a Contest<Cat> won't accept a Vet<Pet>,
// so this line won't compile
val catContest = Contest<Cat>(petVet)
```

## 19. Use in to make a generic type contravariant
