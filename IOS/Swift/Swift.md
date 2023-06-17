```swift
    print("Hello , world!")
```

#### In swift, this line of code is a complete program. You don't need to import a separate library for functionality like input/output or string hadnling.

#### Code written at global scope is used as the entry point for the program., So you don't need a main() function. You also don't need to write semicolons at the end of every statement.
```swift
    var myVaraiable = 42 // use var for varaible
    myVaraiable = 50
    let myConstant = 42 // use let for constant
    let explicityDouble: Double = 70
```

#### A constant or avriable must have the same type as the value you want to assign to it. However, you don't always have to write type explicitly. Providing a value when you create a constant or variable lets the compiler infer its type. In the example above, the compiler infers that myVaraiable is an integer because its initial value is an integer.

#### Values are never implicitly converted to another type. If you need to convert a value to a different type, explicitly make an instance of the desired type.
```swift
    let label = "The width is "
    let width = 94
    let widthLable = label + String(width)
    let widthLable = "\(label) \(width)" // Another way of writing the above code
```

#### Use three double quotation marks (""") for strings that take up multiple lines. Indentation at start of each quoted line is removed, as long as it matches the indentation of the closing quotation marks. For example
```swift
    let quotation = """
        Event though thers's whitespace to the left,
        the actual lines aren't indented.
            Excepth fot this line.
        Double quotes (") can appear without being escaped.

        I still have \(apple + orange) pieces of fruit.
        """
```

#### Create arrays and dictionaries using brackets ([]). Array automatically grow as you add elements.
```swift
    var fruits = ["strawberries", "limes", "tangerines"]
    fruits[1] = "grapes
    fruits.append("blueberries")
    print(fruits)

    var occupations = [
        "Malcolm": "Captain",
        "Kaylee": "Mechanic",
    ]
    occupations["Jayne"] = "Public Relations"
```

#### you also use brackets to write an empty array or dictionary. For an array, write [], and for a dictionary, write [:]. If you're assigning an empty array or dictionary to a new variable, or another place where there isn't any type information. You need to specify the type.
```swift
    let emptyArray: [String] = []
    let emptyDictionary: [String: Float] = [:]
```

#### Controle Flow
```swift
    let individualScores = [75, 43, 103, 87, 12]
    var teamScore = 0
    for score in individualScores {
        if score > 50 {
            teamScore += 3
        } else {
            teamScore += 1
        }
    }
    print(":celebration:")
    print(teamScore)
```

#### You can write if or switch after the equal sign of an assignment ar after return, to choose a value based on the condition.
```swift
    let scoreDecoration = if teamScore > 10 {
        "abcd"
    } else {
        ""
    }
```

#### You can use if and let together to work with values that might be missing. These values are represented as optionals. An optional value either contains a value or contains nil to indicate that a value is missing. Write a question mark (?) after the type of a value to mwrk the value as optional.
```swift
    var optionalString: String? = "Hello"
    print(optionalString == nil)

    var optionalName: String? = "John Appleseed"
    var greeting = "Hello~"
    if let name = optionalName {
        greeting = "Hello, \(name)"
    }
```

#### Another way to handle optional value is to provide a default value using the ?? operator. If the optional value is missing the default value is used instead.
```swift
    let nickname: String? = nil
    let fullName: String = "John Appleseed"
    let informalGreeting = "Hi \(nickname ?? fullNAme)"
```

#### You can use a shorter spelling to unwrap a value, using the same name for the unwrapped value.
```swift
    if let nickname {
        pring("Hey, \(nickname)") // Doesn't pring anything, because nickname is nil.
    }
```

#### Switches support any kind of data and wide variety of comparison operations -- they aren't limited to integers and tests for equality.
```swift
    let vegetable = "red papper"
    switch vagetable {
        case "celery":
            print("Add some raisins and make ants on a log.")
        case "cucumber, "watercress":
            print("That would make a good team sandwich.")
        case let x where x.hasSuffix("pepper"):
            print("Is it a spicy \(x)?")
        default:
            print(Everything tastes good in soup.")
    }
```
#### Notice how let can be used in a pattern to assign the value that matched the pattern to a constant.
#### after executing the code inside a switch case that matched, the program exists from the switch statement. Execution doesn't continue to the next case, so you don't need to explicitly break out of the switch at the end of each case's code.

#### You use for-in to iteragte over items in the dictionary by providing a pair of names to use for each key-value pair. Dictionaries are an unordered collection, so their keys and values are iterated over in an arbitrary order.
```swift
    let interestingNumbers = [
        "Prime": [2,3,5,7,11,13],
        "Fibonacci": [1,1,2,3,5,8],
        "Square": [1,4,9,16,25]
    ]
    var largest = 0
    for(_, numbers) in interestingNumbers {
        for number in numbers {
            if number > largest {
                largest = number
            }
        }
    }
    print(largest)
```
#### Replace the _ with a variable name, and keep track of which kind of number was largest.

#### While Loop
```swift
    var n = 2
    while n < 100 {
        n *= 2
    }
    print(n)
```

#### Do while loop
```swift
    var m = 2
    repeat {
        m *= 2
    } while m < 100
    print(m)
```

```swift
    var total = 0
    for i in 0..<4 {
        total += i
    }
    print(total)
```
#### use ..< to make a range that omits its upper value, and use ... to make a range that includes both values.

## Functions and Closures
``` swift
    func greet(person: String, day: String) -> String {
        return "Hello \(person), today is \(day)."
    }
    greet(person: "Bob", day: "Tuesday")
```

#### By default, functions use their parameter name as labels for their arguments. Write a custom argument label before the parameter name, or write _ to use no argument label
```swift
    func greet(_ person: String, on day: String) -> String {
        return "Hello \(person), today is \(day)."
    }
    greet("John", on: "Wednesday")
```

#### Use a tuple to make a compound value -- for example, to return multiple values from a function. The elements of the tuple can be referred to either by name of by number.
```swift
    func calculateStatistics(scores: [Int]) -> (min: Int, max: Int, sum: Int) {
        var min = scores[0];
        var max = scores[0];
        var sum = 0

        for scores in scores {
            if score > max {
                max = score
            } else if score < min {
                min = score
            }
            sum += score
        }
        return (min, max, sum)
    }

    let statistics = calculateStatistics(scores: [5,3,100,3,9])
    print(statistics.sum)
    print(statistics.2)
```

#### Nested Functions have access to variables that where declared in the outer function. You can use nested functions to organize the code in a function that's long or complex.
```swift
    func returnFifteen() -> Int {
        var y = 10
        func add() {
            y += 5
        }
        add()
        return y
    }
    returnFifteen()
```

#### Functions are a first-class type. This means that a function can return another function as its value.
```swift
    func makeIncrementer() -> ((Int) -> Int) {
        func addOne(number: Int) -> Int {
            return 1 + number
        }
        return addOne
    }
    var increment = makeIncrementer()
    increment(7);
```

#### A function can take another function as one of its arguments.
```swift
    func hasAnyMatches(list: [Int], condition: (Int) -> Bool) -> Bool {
        for item in list {
            if condition(item) {
                return true
            }
        }
        return false
    }

    func lessThanTen(number: Int) -> Bool {
        return number < 10
    }

    var numbers = [20, 19, 7, 2]
    hasAnyMatches(list: numbers, condition: lessThanTen)
```

#### Functions are actually a special case of closures: block of code that can be called later. The code in a closure has access to things like variables and functions that were available in the scope where the closure was created, even if the closure is in a different scope when it's executed -- you swa an example of this already with nested functions. You can write closure without a name by surrounding code with braces ({}). Use in to separate the arguments and return type from the body
```swift
    numbers.map({ (number: Int) -> Int in
        let result = 3 * number
        return result
    })
```
```swift
    let mappedNumbers = numbers.map({ number in 3*number})
    print(mappedNumbers)
```

### You can refer to parameters by number instead of by name - this approach is especially useful in very short closures. A closure passed as the last argument to a function can appear immediately after the parentheses. When a closure is the only argument to a function, you can omit the parentheses entirely.
```swift
    let sortedNumbers = numbers.sorted { $0 > $1 }
```

### Objects And Classed

```swift
    class Shape {
        var numberOfSides = 0

        func simpleDescription() -> String {
            return "A shape with \(numberOfSides) sides."
        }
    }
    var shape = Shape()
    shape.numberOfSides = 7
    var shapeDescription = shape.simpleDescription()
```

#### This version of the Shape class is missing somthing important: an initializer to set up the class when an instance is created. Use init to create one.
```swift
    class NamedShape {
        var numberOfSides: Int = 0
        var name: String

        init(name: String) {
            self.name = name
        }

        func simpleDescription() -> String {
            return "A shape with \(numberOfSides) sides."
        }
    }
```
#### Notice how self is used to distinguish the name property from the name argument to the initializer. 

#### Use deinit to create a deinitializer if you need to perform some cleanup before the object is deallocated.
#### Subclasses include their superclass name after their class name, separeted by a colon. There's no requirement for classes to subclass any standard root class, so you can include or omit a superclass as needed.

### Mmethods on a subclass that override the superclass's implementation are marked with override - overriding a method by accident, without override, is detected by the compiler as an error. The compiler also detects methods with override that don't actually override any method in the superclass.
```swift
    class Square: NamedShape {
        var sideLength: Double

        init(sideLength: Double, name: String) {
            self.sideLength = sideLength
            super.init(name: name)
            numberOfSides = 4
        }

        func area() -> Double {
            return sideLength * sideLength
        }

        override func simpleDescription() -> String {
            return "A square with sides of length \(sideLength)."
        }
    }

    let test = Square(sideLength: 5.2, name: "my first square")
    test.area()
    test.simpleDescription()
```

#### in addition to simple properties that are stored, properties can have a getter and a setter.
```swift
    class EquilateralTrangle: NamedShape {
        var sideLength: Double = 0.0

        init(sideLength: Double, name: String) {
            self.sideLength = sideLength
            super.init(name: name)
            numberOfSides = 3
        }

        var paimeter: Double {
            get {
                return 3.0 * sideLength
            }
            set {
                sideLength = newValue / 3.0
            }
        }

        override func simpleDescription() -> String {
            return "An equilateral triangle with sides of length \(sideLength)."
        }
    }

    var triangle = Equi;ateralTriangle(sideLength: 3.1, name: "a triangle")
    print(triangle.parimeter)
    triangle.parimeter = 9.9
    print(triangle.sideLength)
```

### If you don't need to compute the property but still need to provide code that's run before and after setting a new value use willSet and didSet. For example the class below ensures that the side length of its triangle is always the same as the side length of its square.
```swift
    class TriangleAndSquare {
        var triangle: EquilateralTriangle {
            willSet {
                square.sideLength = newValue.sideLength
            }
        }
        var square: Square {
            willSet {
                triangle.sideLength = newValue.sideLength
            }
        }

        init(side: Double, name: String) {
            square = Square(sideLength: size, name: name)
            triangle = EquilateralTriangle(sideLength: size, name: name)
        }
    }

    var triangleAndSquare = TriangleAndSquare(size: 10, name: "another test shape")
    print(triangleAndSquare.square.sideLength)
    print(triangleAndSquare.triangle.sideLength)
    triangleAndSquare.square = Square(sideLength: 50, name: "larger square")
    print(triangleAndSquare.triangle.sideLength)
```

### Enumerations and Structures
```swift
    enum Rank: Int {
        case ace = 1
        case two, three, four, five, six, seven, eight, nine, ten
        case jack, queen, king

        func simpleDescription() -> String {
            switch self {
                case .ace:
                    return "ace"
                case .jack:
                    return "jack"
                case .queen:
                    return "queen"
                case .king:
                    return "king"
                default:
                    return String(self.rawValue)
            }
        }
    }
    let ace = Rank.ace
    let aceRawValue = ace.rawValue
```


### Concurrency: Use async to mark a function that runs asynchronously
```swift
    func fetchUserID(from server: String) async -> Int {
        if server == "primary" {
            return 97
        }
        return 501
    }
```

### You mark a call to an asynchronous function by writing await in front of it.
```swift
    func fetchUsername(from server: String) async -> String {
        let userID = await fetchUserID(from: server)
        if userID = 501 {
            return "John Appleseed"
        }
        return "Guest"
    }
```

### Use async let to call an asynchronus function. letting it run in parallel with other asynchronous code. When you use the value it returns. write await 
```swift
    func connectUser(to server: String) async {
        async let userID = fetchUserID(from: server)
        async let username = fetchUsername(from: server)
        let greeting = await "Hello \(username), user ID \(userID)"
        print(greeting)
    }
```

### Use Task to call asynchronous function from synchronous code. without waiting for them to return.
```swift
    Task {
        await conectUser(to: "primary")
    }
```

### Protocols and Extensions



