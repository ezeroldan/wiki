# Swift UI

## WWDC videos

### 2021
- [ ] [Add rich graphics to your SwiftUI app](https://developer.apple.com/videos/play/wwdc2021-10021)
- [ ] [Craft search experiences in SwiftUI](https://developer.apple.com/videos/play/wwdc2021-10176)
- [ ] [Meet async/await in Swift](https://developer.apple.com/videos/play/wwdc2021-10132)
- [ ] [What's new in SwiftUI](https://developer.apple.com/videos/play/wwdc2021-10018)
- [ ] [Demystify SwiftUI](https://developer.apple.com/videos/play/wwdc2021-10022)
- [ ] [Discover concurrency in SwiftUI](https://developer.apple.com/videos/play/wwdc2021-10019)
- [ ] [Explore the SF Symbols 3 app](https://developer.apple.com/videos/play/wwdc2021-10288)
- [ ] [SF Symbols in SwiftUI](https://developer.apple.com/videos/play/wwdc2021-10349)
- [ ] [SwiftUI Accessibility: Beyond the basics](https://developer.apple.com/videos/play/wwdc2021-10119)
- [ ] [Direct and reflect focus in SwiftUI](https://developer.apple.com/videos/play/wwdc2021-10023)
- [ ] [Localize your SwiftUI app](https://developer.apple.com/videos/play/wwdc2021-10220)

### 2020
- [ ] [Build SwiftUI apps for tvOS](https://developer.apple.com/videos/play/wwdc2020/10042/)
- [ ] [Build complications in SwiftUI](https://developer.apple.com/videos/play/wwdc2020/10048/)
- [ ] [Introduction to SwiftUI](https://developer.apple.com/videos/play/wwdc2020/10119/)
- [ ] [What's new in SwiftUI](https://developer.apple.com/videos/play/wwdc2020/10041/)
- [ ] [App essentials in SwiftUI](https://developer.apple.com/videos/play/wwdc2020/10037/)
- [Visually edit SwiftUI views](https://developer.apple.com/videos/play/wwdc2020/10185/)
- [ ] [Build a SwiftUI view in Swift Playgrounds](https://developer.apple.com/videos/play/wwdc2020/10643/)
- [ ] [Build document-based apps in SwiftUI](https://developer.apple.com/videos/play/wwdc2020/10039/)
- [ ] [Stacks, Grids, and Outlines in SwiftUI](https://developer.apple.com/videos/play/wwdc2020/10031/)
- [ ] [Build SwiftUI views for widgets](https://developer.apple.com/videos/play/wwdc2020/10033/)
- [ ] [Data Essentials in SwiftUI](https://developer.apple.com/videos/play/wwdc2020/10040/)
- [ ] [Structure your app for SwiftUI previews](https://developer.apple.com/videos/play/wwdc2020/10149/)

### 2019
- [x] [Introducing SwiftUI: Building Your First App](https://developer.apple.com/videos/play/wwdc2019/204/)
- [x] [SwiftUI Essentials](https://developer.apple.com/videos/play/wwdc2019/216)
- [ ] [Data Flow Through SwiftUI](https://developer.apple.com/videos/play/wwdc2019/226)
- [ ] [Building Custom Views with SwiftUI](https://developer.apple.com/videos/play/wwdc2019/237)
- [ ] [Integrating SwiftUI](https://developer.apple.com/videos/play/wwdc2019/231)
- [ ] [Accessibility in SwiftUI](https://developer.apple.com/videos/play/wwdc2019/238)
- [ ] [SwiftUI On All Devices](https://developer.apple.com/videos/play/wwdc2019/240)
- [ ] [SwiftUI on watchOS](https://developer.apple.com/videos/play/wwdc2019/219)
- [ ] [Mastering Xcode Previews](https://developer.apple.com/videos/play/wwdc2019/233)

## Apuntes
- Modifiers es retorna una nueva instancia
- El roden de los modifiers tiene importancia 
- Todos los componentes extieden del protocol View

## View

```swift
//struct es como una clase que dinamicamente 
//genera el constructor para sus propiedades
struct ContentView: View {

    //Esto es una propiedad llamada body de tipo opaque return (some) View
    var body: some View { //Esta es una propiedad computada que se procesa al hacer get de la misma
        //Al existir una sola linea de codigo es lo mismo que ponerle return
        Text("Mi Primera App")
            .padding(.all, 20) //El .all hace referencia a una constante statica del type del argumento (Edge.Set.all)
    }
}
```

```swift
public protocol View {
    associatedtype Body : View
    var body: Body { get }
}
```

### Text
```swift
Text("Hello World")
```

### Label
```swift
Label("SwiftUI CheatSheet 2.0", systemImage: "up.icloud")
```

### Link
```swift
Link("Click me",destination: URL(string: "your_url")!)
```

### TextEditor
```swift
TextEditor(text: $currentText)
    .onChange(of: clearText) { value in
        if clearText {
            currentText = ""
        }
    }
```

### Map
```swift
Map(mapRect:interactionModes:showsUserLocation: userTrackingMode:
```

### Image
```swift
Image("hello_world") //image name is hello_world
Image(systemName: "cloud.heavyrain.fill")
```

### Shape

```swift
Rectangle()
    .fill(Color.red)
    .frame(width: 200, height: 200)
```

```swift
Circle()
    .fill(Color.blue)
    .frame(width: 50, height: 50)
```

### ProgressView
```swift
ProgressView("Text", value: 10, total: 100)
```

### Layout

#### Background

```swift
Text("Hello World")
    .font(.largeTitle)
    .background(
        Image("hello_world")
            .resizable()
            .frame(width: 100, height: 100)
    )
```

```swift
Text("Hello World")
    .background(
        LinearGradient(
            gradient: Gradient(colors: [.white, .red, .black]), 
            startPoint: .leading, 
            endPoint: .trailing
        ),
        cornerRadius: 0
    )
```

#### Stacks

```swift
VStack {
    Text("Hello")
    Text("World")
}
```

```swift
VStack(alignment: .leading, spacing: 20) {
    Text("Hello")
    Divider()
    Text("World")
}
```

```swift
HStack {
    Text("Hello")
    Text("World")
}
```

```swift
ZStack() {
    Image("hello_world")
    Text("Hello World")
        .font(.largeTitle)
        .background(Color.black)
        .foregroundColor(.white)
}
```

```swift
  ScrollView(.horizontal) {
           LazyVStack(spacing: 10) {
                ForEach(0..<1000) { index in
                    Text("\(index)")
                            .frame(width: 100, height: 200)
                            .border(Color.gray.opacity(0.5), width: 0.5)
                            .background(Color.blue)
                            .cornerRadius(6)
                }
            }
            .padding(.leading, 10)
        }
```

```swift
  ScrollView(.horizontal) {
            LazyHStack(spacing: 10) {
                ForEach(0..<1000) { index in
                    Text("\(index)")
                            .frame(width: 100, height: 200)
                            .border(Color.gray.opacity(0.5), width: 0.5)
                            .background(Color.blue)
                            .cornerRadius(6)
                }
            }
            .padding(.leading, 10)
        }
```

```swift
struct ContentView: View {
    
    let colors: [Color] = [.red, .green, .yellow, .blue]
    
    var columns: [GridItem] =
        Array(repeating: .init(.flexible(), alignment: .center), count: 3)
    
    var body: some View {
        ScrollView {
            LazyVGrid(columns: columns, spacing: 10) {
                ForEach(0...100, id: \.self) { index in
                    Text("Tab \(index)")
                        .frame(width: 110, height: 200)
                        .background(colors[index % colors.count])
                    .cornerRadius(8)
                }
            }
        }
    }
}
```

```swift
struct ContentView: View {
    
    let colors: [Color] = [.red, .green, .yellow, .blue]
    
    var columns: [GridItem] =
        Array(repeating: .init(.flexible(), alignment: .center), count: 3)
    
    var body: some View {
        ScrollView {
            LazyHGrid(columns: columns, spacing: 10) {
                ForEach(0...100, id: \.self) { index in
                    Text("Tab \(index)")
                        .frame(width: 110, height: 200)
                        .background(colors[index % colors.count])
                    .cornerRadius(8)
                }
            }
        }
    }
}
```

### Input

#### Toggle
```swift
@State var isShowing = true //state

Toggle(isOn: $isShowing) {
    Text("Hello World")
}.padding()
```

#### Button
```swift
Button(
    action: {
        // do something
    },
    label: { Text("Click Me") }
)
```

#####  ButtonStyle
```swift
struct NeumorphicButtonStyle: ButtonStyle {
    var bgColor: Color

    func makeBody(configuration: Self.Configuration) -> some View {
        configuration.label
            .padding(20)
            .background(
                ZStack {
                    RoundedRectangle(cornerRadius: 10, style: .continuous)
                        .shadow(color: .white, radius: configuration.isPressed ? 7: 10, x: configuration.isPressed ? -5: -15, y: configuration.isPressed ? -5: -15)
                        .shadow(color: .black, radius: configuration.isPressed ? 7: 10, x: configuration.isPressed ? 5: 15, y: configuration.isPressed ? 5: 15)
                        .blendMode(.overlay)
                    RoundedRectangle(cornerRadius: 10, style: .continuous)
                        .fill(bgColor)                    
                }
        )
            .scaleEffect(configuration.isPressed ? 0.95: 1)
            .foregroundColor(.primary)
            .animation(.spring())
    }
}

Button("Neumorphic", action: {

}).buttonStyle(NeumorphicButtonStyle(bgColor: .neuBackground))
```

#### TextField
```swift
@State var fullName: String = "Joe" //create State

TextField($fullName) // passing it to bind
    .textFieldStyle(.roundedBorder) // adds border
```

#### Slider
```swift
@State var value: Double = 0 // create State
    
Slider(value: $value, from: -100, through: 100, by: 1)
```

#### DatePicker
```swift
@State var selectedDate = Date()
DatePicker(
    $selectedDate,
    maximumDate: Date(),
    displayedComponents: .date
)
```

#### Picker
```swift
@State var favoriteColor = 0
var colors = ["Red", "Green", "Blue"]

Picker("Favorite Color", selection: $favoriteColor) {
    ForEach(0 ..< colors.count) { index in
        Text(self.colors[index])
            .tag(index)
    }
}
.pickerStyle(SegmentedPickerStyle())
```

#### Stepper
```swift
@State var count:Int = 0

Stepper(
    onIncrement: { self.count += 1 }, 
    onDecrement: { self.count -= 1 }, 
    label: { Text("Count is \(count)") }
)
```

#### Tap
```swift
Text("Tap me!")
    .onTapGesture {
        print("Tapped!")
    }


Text("Tap")
    .gesture(
        TapGesture()
            .onEnded { _ in
                // do something
            }
    )

Text("Drag Me")
    .gesture(
        DragGesture(minimumDistance: 50)
            .onEnded { _ in
                // do something
            }
    )

Text("Long Press")
    .gesture(
        LongPressGesture(minimumDuration: 2)
            .onEnded { _ in
                // do something
            }
    )
```

### List
```swift
List {
    Text("Hello world")
    Text("Hello world")
    Text("Hello world")
}

let names = ["Thanos", "Iron man", "Ant man"]
List(names, id: \.self) { name in
    Text(name)
}
```

### Containers
```swift
NavigationView {
    Text("Hello")
        .navigationBarTitle(Text("World"), displayMode: .inline)
}

NavigationView {
    Text("Hello")
        .navigationBarTitle(Text("World"), displayMode: .inline)
        .navigationBarItems(
            trailing:
                Button(
                    action: { print("Going to Setting") },
                    label: { Text("Setting") }
                )
        )
}
```

```swift
@State private var selection = 0

TabView(selection: $selection) {
    Text("View A")
        .font(.title)
        .tabItemLabel(Text("View A")
            .font(.caption))
        .tag(0)
    Text("View B")
        .font(.title)
        .tabItemLabel(Text("View B")
            .font(.caption))
        .tag(1)
    Text("View C")
        .font(.title)
        .tabItemLabel(Text("View C")
            .font(.caption))
        .tag(2)
}
```

#### Group
```swift
VStack {
    Group {
        Text("Hello")
        Text("Hello")
        Text("Hello")
    }
    Group {
        Text("Hello")
        Text("Hello")
    }
}
```

### Alert
```swift
Alert(
    title: Text("Title"), 
    message: Text("message"), 
    dismissButton: .default(Text("Ok!"))
)

ActionSheet(
    title: Text("Title"), 
    message: Text("Message"), 
    buttons: [
        .default(Text("Ok!"), action: { print("hello") })
    ]
)
```

### Navigation
```swift
NavigationView {
    NavigationLink(destination: SecondView()) {
        Text("Show")
    }.navigationBarTitle(Text("First View"))
}
```

## API JSON

```swift
struct ContentView : View {
    @state private var data

    private func loadData() {
        guard let url = URL(string: "URL")
            return
        }

        URLSession.shared.dataTask(with: url) { data, reseponse, error in
            guard let data = data else { return }
            if let decodedData = try? JSONDecoder().decode(MODEL.self, from: data) {
                DispatchQueue.main.async {

                }
            }
        }.resume()
    }

}
```

## ForEach
```swift
struct IdentifiableGameResult: Identifiable {
    var id = UUID()
    var score: Int
}

struct ContentView: View {
    let results = [
        IdentifiableGameResult(score: 8),
        IdentifiableGameResult(score: 5),
        IdentifiableGameResult(score: 10)
    ]

    var body: some View {
        VStack {
            ForEach(results) { result in
                Text("Result: \(result.score)")
            }
        }
    }
}
```

## Animation

### withAnimation
```swift
Button("Click") {
    withAnimation(.default) {
        self.isAnimated.toggle()
    }
}
```