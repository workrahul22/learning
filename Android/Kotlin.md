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

## Condition
```
    val name = if(condition) {
        body1
    } else {
        body2
    }

    val name = when() {
        condition1 -> body1
        condition2 -> body2
        else -> body3
    }

    when(parameter) {
        in rangeStart..rangeEnd -> body1
        condition2 -> body2
    }
```

## Nullable Variable
```
    var favouriteActor: String? = "Rahul"
    favouriteActor = null
```

### Elvis Operator
```
    var name = nullableVariable?.methodProperty? : defaultValue
    favouriteActor?.length ?: 0
```

### Not Nullable Assertion
```
    favouriteActor!!.length
```

### Getter Setter
```
    var speakerVolume = 2
        get() = field
        set(value) {
            field = value
        }
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

### The override keyword informs the kotlin runtime to execute the code enclosed in the method defined in the subclass

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

```
    import kotlin.properties.ReadOnlyProperty
import kotlin.reflect.KProperty

open class SmartDevice(val name: String, val category: String) {
    
    var deviceStatus = "online"
    	protected set
    
    open val deviceType = "unknown"
    
    open fun turnOn() {
        deviceStatus = "on"
    }
    
    open fun turnOff() {
        deviceStatus = "off"
    }
    
    fun printDeviceInfo() {
        println("Device name : $name category : $category type $deviceType")
    }
}

class SmartTvDevice(deviceName: String, deviceCategory: String) : 
SmartDevice(name = deviceName, category = deviceCategory) {
    
    override val deviceType = "Smart TV"
    
    private var speakerVolume by RangeRegulator(initialValue = 2, minValue = 0, maxValue = 100)
    
    private var channelNumber by RangeRegulator(initialValue = 1, minValue = 0, maxValue = 200)
    
    fun increaseSpeakerVolume() {
        speakerVolume++
        println("Speaker volume increased to $speakerVolume")
    }
    
    fun decreaseSpeakerVolume() {
        speakerVolume--
        println("Speaker volume decreased to $speakerVolume")
    }
    
    fun nextChannel() {
        channelNumber++
        println("Channel number increased to $channelNumber")
    }
    
    fun previouChannel() {
    	channelNumber--
        println("Channel number decreased to $channelNumber")
    }
    
    override fun turnOn() {
        super.turnOn()
        println("$name is turned on. Speaker volume is set to $speakerVolume and channel number is " + 
                "set to $channelNumber.")
    }
    
    override fun turnOff() {
        super.turnOff()
        println("$name turned off")
    }
}

class SmartLightDevice(deviceName: String, deviceCategory: String) : 
SmartDevice(name = deviceName, category = deviceCategory) {
	override val deviceType = "Smart Light"
    
    private val brightnessLevel by RangeRegulator(initialValue = 0, minValue = 0, maxValue = 100)
    
    fun increaseBrightness() {
        brightnessLevel++
        println("Brightness increased to $brightnessLevel.")
    }
    
    fun decreaseBrightness() {
    	brightnessLevel--
        println("Brightness decreased to $brightnessLevel.")
    }
    
    override fun turnOn() {
        super.turnOn()
        brightnessLevel = 2
        println("$name turned on. The brightness level is $brightnessLevel.")
    }
    
    override fun turnOff() {
        super.turnOff()
        brightnessLevel = 0
        println("Smart Light turned off")
    }
}


class SmartHome(val smartTvDevice: SmartTvDevice, val smartLightDevice: SmartLightDevice) {
    
    var deviceTurnOnCount = 0
    	private set
    
    fun turnOnTv() {
        deviceTurnOnCount++
        smartTvDevice.turnOn()
    }
    
    fun turnOffTv() {
        deviceTurnOnCount--
        smartTvDevice.turnOff()
    }
    
    fun increaseTvVolume() {
        if(smartTvDevice.deviceStatus == "on") {
            smartTvDevice.increaseSpeakerVolume()
        }
    }
    
    fun decreaseTvVolume() {
        if(smartTvDevice.deviceStatus == "on") {
            smartTvDevice.decreaseSpeakerVolume()
        }
    }
     
    fun changeTvChannelToNext() {
        if(smartTvDevice.deviceStatus == "on") {
        	smartTvDevice.nextChannel()
        }
    }
    
     fun changeTvChannelToPrevious() {
        if(smartTvDevice.deviceStatus == "on") {
        	smartTvDevice.previousChannel()
        }
    }
    
    fun turnOnLight() {
        deviceTurnOnCount++
        smartLightDevice.turnOn()
    }
    
    fun printSmartTvInfo() {
    	smartTvDevice.printDeviceInfo() 
    }
    
    fun printSmartLightInfo() {
        smartLightDevice.printDeviceInfo()
    }
    
    fun turnOffLight() {
        deviceTurnOnCount--
        smartLightDevice.turnOff()
    }
    
    fun increaseLightBrightness() {
        if(smartLightDevice.deviceStatus == "on") {
        	smartLightDevice.increaseBrightness()
        }
    }
    
     fun decreaseLightBrightness() {
        if(smartLightDevice.deviceStatus == "on") {
        	smartLightDevice.decreaseBrightness()
        }
    }
    
    fun turnOffAllDevice() {
        turnOffTv()
        deviceTurnOnCount--;
        turnOffLight()
        deviceTurnOnCount--;
    }
}

class RangeRegulator(initialValue: Int, private val minValue: Int, private val maxValue: Int) : 
ReadWriteProperty<Any?, Int> {
    
    var fieldData = initialValue
    
    override fun getValue(thisRef: Any?, property: KProperty<*>): Int {
        return fieldData
    }
    
    override fun setValue(thisRef: Any?, property: KProperty<*>, value: Int): Int {
        if(value in minValue..maxValue) {
            fieldData = value
        }
    }
}

fun main() {
    var smartDevice: SmartDevice = SmartTvDevice("Android Tv", "Entertainment")
    smartDevice.turnOn()
    
    smartDevice = SmartLightDevice("Google Light", "Utility")
    smartDevice.turnOn()
    
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

### Function And Lambda Expression

you can store function in a variable
pass them to other functions as argument
Return them from other functions

```
    fun main() {
        val trickFunction = ::trick
    }

    fun trick() {
        println("No treats")
    }    
```

```
    val trick = {
        println("No Treat")
    }

    fun main() {
        val trickFunction = trick
        trickFunction()
    }
```

```
    val treat: (Int) -> String = {
    }

    Val treat: () -> Unit = {
    }
```

```
    fun trickOrTreat(isTrick: Boolean, extraTreat: ((Int) -> String)? : () -> Unit {
        if(isTrick) {
            return trick
        }else {
            if(extraTreat != null) {
                return treat
            }
        }
```

```
    repeat(4) {
        treatFunction()
    }
```

