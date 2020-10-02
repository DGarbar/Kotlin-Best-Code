# Kotlin-Best-Code

#### Types

`var` - mutable
`val` - immutable

## Collections

#### List

```kotlin
`Array<>` - mutable
`List<>` - immutable
```

```kotlin
val cars = listOf<String>("BMW", "Honda", "Mercedes")
cars[0] = "Reno" // Compile time error: No set method providing array access


for ((index, value) in l.withIndex()) {
    println("The element at $index is $value")
}
```

#### Map

```kotlin
val marathon = mutableMapOf(1 to "John Doe", 2 to "Marty McFly", 3 to "Marie Curie")

marathon.remove(1, "John Doe...") // Only if value is ==

for ((key, value) in marathon) {
    println(value)
}
```

## Strings

### Character

To get the int value that the character actually represents you can use one of these methods:
```kotlin
val charValue = '2'
val intValue1 = charValue.toString().toInt() // 2
val intValue2 = Character.getNumericValue(charValue) // 2
```

#### String templates

```kotlin
val language = "Kotlin"
println("$language has ${language.length} letters in the name")
```

## Class

Data class
```kotlin
data class Complex(var real: Double = 0.0, var image: Double = 0.0)
```

Primary constructor
```kotlin
class Size constructor(width: Int, height: Int) {
    val width: Int = width
    val height: Int = height
    val area: Int = width * height
}
```

#### Get/Set

```kotlin
class Client {
    var name = "Unknown"
        get() {
            return field
        }
        set(value) {
            field = value
        }
}
```


#### Extension functions

```kotlin
fun String.repeated(): String = this + this

"ha".repeated()
```

#### Singleton (object)

```kotlin
object PlayingField {}
```

#### Companion (companion)
It is like a nested object, but more related to the class. 
Only one companion object is available for each class.

```kotlin
class Deck {
    companion object {  // can have NAMe
        val size = 10
        val height = 2
        fun volume(bottom: Int, height: Int) = bottom * height
    }

    val square = size * size             //100
    val volume = volume(square, height)  //200
}

Deck.Companion.volume(1,1)
Deck.volume(1,1)

```

## Objects

You should compare by `==` not `equals()`

#### Copy

```kotlin
fun main() {
    val bob = Client("Bob", 29, "Male")
    val john = bob.copy(name = "John")
    println(bob)
    println(john)
}
```

## Nulls

```kotlin
var name: String? = "Kotlin"
name?.length ?: -1 // getLengh or -1 if null
```

There is an easy way to invoke an NPE: the !! operator. 
```kotlin
var name: String? = "Kotlin"
print(name!!.length)  // This operator is used to stop the program when null is met.
```

## Functions

```kotlin
fun isPositive(number: Int): Boolean {
    return number > 0
}
```

```kotlin
fun sum(a: Int, b: Int): Int = a + b
```
==
```kotlin
fun sum(a: Int, b: Int) = a + b // Int
```
## Arrays

#### You can split array elements in the variables

```kotlin
intArrayOf creates IntArray;
charArrayOf creates CharArray;
doubleArrayOf creates DoubleArray;
```

```kotlin
val (year, month, day) = readLine()!!.split('-')
println("$month/$day/$year")
```

#### Init Array 

```kotlin
val input = Array<String>(3) { scanner.nextLine() }
```

## Loops

#### For

```kotlin
for (element in array) {
    // body of loop
}
```

```kotlin
for (index in 1..5) {
    println("$index: ${daysOfWeek[index]}")
}
```

```kotlin
for ((index, value) in array.withIndex()) {
    println("the element at $index is $value")
}
```

```kotlin
for (index in 1 until daysOfWeek.lastIndex) {
    println("$index: ${daysOfWeek[index]}")
}
```

```kotlin
for (index in daysOfWeek.lastIndex downTo 0 step 2) {
    println("$index: ${daysOfWeek[index]}")
}
```

```kotlin
for (index in 1..5) {
    println("$index: ${daysOfWeek[index]}")
}
```

#### Labels 

```kotlin
loop@ for (i in 1..3) {
    for (j in 1..3) {
        for (k in 1..3) {
            if (k == 2) continue@loop
            println("i = $i, j = $j, k = $k")
        }
    }
}
```

The output result:

i = 1, j = 1, k = 1
i = 2, j = 1, k = 1
i = 3, j = 1, k = 1

#### Usefull methods

```kotlin
 numbers.sumBy { Character.getNumericValue(it) }
```

## Functionality

#### Not switch but when

```kotlin
val test = when {
        input.isEmpty() -> input
        input.startsWith('i') -> input.drop(1).toInt() + 1
        else -> input
    }
    println(test)
```

or use with variables but for other purpose


```kotlin
when (input) {
        "" -> println(input)
        "f" ->  println("pay respect")
        "kek" -> println("yeeh boy")
        else -> input
    }
```

```kotlin
    println(when (c) {
        a + b -> "$c equals $a plus $b"
        a - b -> "$c equals $a minus $b"
        a * b -> "$c equals $a times $b"
        else -> "We do not know how to calculate $c"
    })
```


#### `If` also return value

```kotlin
println(if (a == b) {
        "a equal b"
    } else if (a > b) {
        "a is greater than b"
    } else {
        "a is less than b"
    })
```

#### Destrucuting	

```kotlin	
data class User(val name: String, val age: Int, val isAdmin: Boolean)	
val anonim = User("Anonim", 999, false)	
```	

Without DATA class	
```kotlin	
class User(val name: String, val age: Int, val isAdmin: Boolean){	
    operator fun component1(): String = name	
    operator fun component2(): Int = age	
    operator fun component3(): Boolean = isAdmin	
}	
// now we can use default destructuring syntax	
fun checkIsAdmin(suspiciousUser: User) {	
    // desctructuring	
    val (name, age, isAdmin) = suspiciousUser	
    if (isAdmin)	
        println("Have a nice day!")	
    else	
        println("Sorry, you should not be here.")	
}	
```	


```kotlin	
fun processAnalytics(usersData: Array<User>) {	
    for ((_, age, isAdmin) in usersData) {	
        if (!isAdmin)	
            sendAnalyticsToCompany("name", age)	
    }	
}	
```
