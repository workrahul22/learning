```kotlin
fun main() {
    println("Hello, World!")
}
```

### Variables
1. val -> Constant
2. var -> Variables

```
    val name = "scala"
    var a = "abcd"
```

### Data Types

1. INTEGER (Byte, Short, Int, Long)
2. FLOATING POINT (Float, Double)
3. BOOLEAN (True, False)
4. CHARACTER (Char, String)

   ```kotlin
       var name:String = "scala"
   ```

Quick Facts
1. Kotlin does not need ; to end statement
2. Kotlin is null safe
3. Kotlin is 100% Java interoperable
4. Kotlin has no primitives (but optimizes their object counterpart for the JVM, if possible)
5. Kotlin classes have properties, not fields
6. Kotlin offers data classes with auto generated equals/hashCode methods and field accessors.
7. Kotling only has runtime exceptions, no checked exceptions.
8. Kotlin has no new keywords, creating objects is done just calling the constructor like another method.
9. kotlin supports (limited) operator overloading. For example accessing a value of a map can be written like val a = someMap["key"]
10. kotlin can not only be compiled by byte code for the JVM, but also in javascript

### Class
```kotlin
    class Lamp {
        private var isOn: Boolean = false

        fun turnOn() {
            isOn = true
        }

        fun turnOff() {
            isOn = false
        }
    }
```

### Visibility Modifiers
1. Private
2. Public
3. Protected
4. Internal -> Only accessible inside the module

### Object
```
    val t1 = Lamp()
    t1.turnOn()
```

### Inheritance
```kotlin
    class AuthLog: Log {
        constructor(data: String): super(data) {
        }
    }
```

### Getters and Setters

Getters and setters are optional and are auto generated if you do not create them in your program

### Lateinit -> Late Initialization

### Open Class
By using the open annotation on a class, compiler allows you to derive new classes from it.

### Confition
```kotlin
    if() {}
    else if() {}
    else () {}
```

```kotlin
    when(number) {
        0 -> print("0")
        1 -> print("1")
    }
```

### Loops
```kotlin
    while() {}
```

```
    do {
    } while(-)    
```

```
    for(item in collection) {}
    for(i in 1..5) {}
```

### Primary Constructor
```
    class Person(var name: String, var age: Int) {
        fun canVote(age: Int) {
            if(age < 18) {
                print("can not vote")
            } else {
                print("can vote")
            }
        }
    }

    var obj1 = Person(name="Rahul", age: 22)
    obj1.canVote(age: 22)
```

```
    class Person(fName: String, personAge: Int) {
        val firstName: String
        var age: Int
        init {
            firstName = fName.capitalize()
            age = personAge
            print("First Name = $firstName")
            println("age = $age")
        }
    }

```

### Secondary Constructor

```
    class Log {
        constructor(data: String) {}
        constructor(data: String, numberOfData: Int) {}
```

### Function
```
    fun methodName(parameter1, paramer2): ReturnType {

    }

    fun sum(a: Int, b: Int) = a + b
```

### Function Overloading
1. Name is same not the signature
2. Number of parameter can be different
3. Type of parameter can be different

### Arrays

```
    var arr = arrayof("one", "two", "three")
    arr.set(0,5)
    arr.get(0)
```
