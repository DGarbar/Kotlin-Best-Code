# Kotlin-Best-Code

#### Types

`var` - mutable
`val` - immutable

`Array<>` - mutable
`List<>` - immutable


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

## Objects

You should compare by **==** not `equals()`


## Functions

Simlpe 

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
val (year, month, day) = readLine()!!.split('-')
println("$month/$day/$year")
```

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
