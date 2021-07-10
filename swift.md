# Swift

## Notas Generales
- In Swift, everything is an object.
- `main.swift` runs when the program runs.
- A variable declared at the top level of a file is a global variable
- A function declared at the top level of a file is a global function
- Executable code can’t go at the top level of a file, only inside a function body curly braces.
- things can see things at their own level and at a higher level containing them
- Namespaces `class Nombre { class SubNombre {} }`
- The top-level namespaces are modules. Your app is a module and hence a namespace, by default is the name of the app
- `import statements`
- Swift itself is defined in a module, Swift module. Your code always implicitly imports the Swift module. 
- 

## NIL

```swift
var variable: String?
if variable != nil {
    print(variable!)
}
```

## Guard
- Performing a function if a condition is false
- The transfer of control statement `return` prevents the rest of the code from executing
```swift
var x = 9
guard x > 10 else {
    // Do error condition 
    return
}
```

## Funciones
- When is a single statement, it is legal to omit the keyword `return` (starting in Swift 5.1).

### Funcion con sin label
```swift
func saludar(_ nombre: String) -> String {
    return "Hola \(nombre)"
}

print(saludar("Ezequiel"))
```

### Funcion con parametros nombrados
```swift
func despedir(param nombre: String)->String{
    return "Hola \(nombre)"
}

print(despedir(param: "Ezequiel"))
```

### Function Signature
```swift
(Int, Int) -> Int
(Int) -> Void = (Int) -> ()
```

### Overloading
- Functions with the same name, including their external parameter names,
- can coexist as long as they have different signatures

```swift
func overloading() -> Void {
    print("Overloading")
}

func overloading() -> Int {
    return 1
}

func overloading(_ param: String = "Hola") -> String {
    return param
}
```

#### Disambiguate
```swift
let prueba : Int = overloading()
let prueba = (overloading as (String) -> String)("Disambiguate")
```

### Variadic Parameters
- The caller can supply many values, separated by comma; receive as an array
- A function can declare a maximum of one variadic parameter
- no way to convert an array into a comma-separated list of arguments

```swift
func variadic(_ params: Int ...) -> [Int] {
    return params
}
print(variadic(1, 2, 3, 4))
```

### Ignored Parameters
- The argument has no name within the function body and cannot be referred to there

```swift
func say(param _:Bool) {}
```

### Modifiable Parameters
- Parameter is a variable declared with `let`.
- You can’t assign to it
- To assign to a parameter declare a `var` local
- If the parameter is an instance of a class, your function can modify it.

```swift
func say(_ s: String) {
    var s = s
}   s = "Hola"
```
#### Alter the value of an argument
- The type of the parameter we intend to modify must be declared `inout`.
- Pass the argument address, by preceding its name with `&`.

```swift
func removeCharacter(_ s: inout String) {

}

var s = "hello"
let result = removeCharacter(&s)
```

### Function in Function
```swift
func padre() {

    func hijo() {

    }

}
```

### Function as Value
- a function’s signature is its type.
- a function is a first-class citizen
- a function can be used wherever a value can be used
- A function can be assigned to a variable
- a function can be passed as an argument in a function call
- a function can be returned as the result of a function

```swift
func doThis( _ f: () -> () ) {
    f()
}
```

#### Type Aliases
```swift
typealias VoidVoidFunction = () -> ()

func dothis(_ f: VoidVoidFunction) {
    f()
}
```

### Anonymous Functions
```swift
{
    (finished: Bool) -> () in
        print("finished: \(finished)")
}
```

#### Anonymous Functions Inline
```swift
ejemplo(funcion: {
    () -> () in
        print("Hola")
})
```

#### Anonymous Abbreviated Syntax

```swift
ejemplo(funcion: {
    () in
    print("Hola")
})

ejemplo(funcion: {
    print("Hola")
})
```

#### Omission of the calling parentheses
```swift
func ejemplo(_ f: () -> ()) {
    f()
}   
ejemplo { 
    print("Howdy")
}
```

#### Omission of the keyword return
```swift
func msg() -> String {
    return "Howdy"
}

func ejemplo(_ f: ()->String ) {
    let s = f()
    print(s)
}

ejemplo {
    msg() // meaning: return greeting()
}
```

#### Define-and-Call
```swift
{
    print("Hola")
}()
```

### Generic functions
- Generic placeholders are defined with either `T` (for type) or `E` (for element)
- Multiple generic types separated with commas `func testGeneric<T,E>(a: T, b: E)`

```swift
func swapGeneric<T> (a: inout T, b: inout T) { 
    let tmp = a
    a = b
    b = tmp
}
```

### Closures
PENDIENTE

## Computed Variables
- The variable must be declared with `var`
- The type is followed immediately by curly braces.
- The getter function must return a value of the same type as the variable.
- There doesn’t have to be a setter. If the setter is omitted, this becomes a read-only variable. This is the computed variable equivalent of a let variable: attempting to assign to it is a compile error.

```swift
var now : String { 

    get { 
        return Date().description 
    }

    set { 
        print(newValue) 
    }
}

var now : String { 

     get {
        print(val) 
    }

}


var now : String { 
    return "Hola"
}

```

## Enum
```swift
enum Filter {
    case albums
    case playlists
    case podcasts
    case books
}
```

```swift
enum Filter : String {
    case albums = "Albums"
    case playlists = "Playlists"
    case podcasts = "Podcasts"
    case books = "Audiobooks"
}

Filter.albums.rawValue
```

```swift
enum SFSymbols {
    static let location = "mappin.and.ellipse"
}
```

```swift
let variable = Filter.albums
switch variable {
    case .albums:
    case .playlists:
}
```

## Struct & Class

**struct**
- A structure is a value type, while a class is a reference type
- When we pass structures, we are passing copies of them and not the originals
- A structure cannot inherit from other types, while a class can
- Structures cannot have custom deinitializers, while a class can
- Structure creates an initializer that lets us populate the stored properties

**class**
- When we pass an instance of a class, we are passing a reference to the original instance of the class

**Access controls**
- `private class`, `private struct`, `private var`, `private func`
- `public class`, `public struct`, `public var`, `public func`
- `internal class`, `internal struct`, `internal var`

```swift
struct/class MyStructClass {

    //Stored properties
    let c = 5
    var v = ""

    private

    var salaryWeek: Double { 

        //Computed properties
        get { }
        set(value) { }

        //Property observers
        willSet(value) { }
        didSet { }
    }
}

var myStruct = MyStructClass(v: "Hello")
```

**Inheritance**

```swift
class Parant {

    var description: String {
        return "Base class"
    }

    func funcion() {}

    //Preventing overrides
    final func funcion() {}
}

class Child: Parant {

    override var description: String {
        return "\(super.description) I am a Child class."
    }

    override func funcion() {}
}
```

## Protocols
- Protocols define a blueprint of methods, properties, and other requirements for a class or a structure
- Son como las interfaces en PHP

```swift
protocol MyProtocol {
    //Property requirements
    var firstName: String { get set }
    var readOnly: String { get }

    //Method requirements
    func funcion() -> String

}

struct MyStruct: MyProtocol, AnotherProtocol { }

struct MyClass: MySuperClass, MyProtocol, AnotherProtocol { }
```

## Extensions
- Add new properties, methods, initializers, and subscripts
- Make an existing type conform to a protocol without modifying the source code for the type
- Extensions cannot override the existing functionality

```swift
extension String { // string es una clase
    func reverse() -> String {
        var reverse = ""
        for letter in self {
            reverse = "\(letter)" + reverse
        }
        return reverse
    }
}

var myString = "Learning Swift is fun" 
myString.reverse()
```

## Property wrappers
- Introduced in Swift 5.1 with SE-0258

```swift
@propertyWrapper
struct Trimmed {
    
    private var str: String = ""

    var wrappedValue: String {
        get { str }
        set { str = newValue.trimmingCharacters(in: .whitespacesAndNewlines) }
    }

    init(wrappedValue: String) {
        self.wrappedValue = wrappedValue
    }

}

@Trimmed var firstName = ""
```