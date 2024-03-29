# SwiftNotes 📱
### Arrays
- `arrayName.append(newElement: Type)`: adds single element to array
- `arrayName.append(contentsOf: Sequence)`: adds another array at the end of arrayName
- `arrayName.first(where: { CONDITION })`: takes first element in array that satisfies the condition
  - Ex: `let firstNegative = arrayOfNumbers.first(where: { $0 < 0 })`

### Closures
- Basically anonymous functions
- Code before `in` is like a function's parameters, code after is like a function's body
  - Can ignore `in` and `() -> ()` if there's no parameters (remove everything before `in`)
- `$0` refers to 1st parameter, `$1` refers to 2nd parameter, and so on 
- Swift can infer type
- Returning closures
  - `func returnClosure() -> ((Int, Int) -> Int) { return {$0 + $1} }`
  - Call: `let varName = returnClosure()`, and then `varName(5,5)`
- Trailing closure
  - If closure is last parameter in a func being called, can close off func like this: `funcName(int: 100) { $0 * 2 }`

### Functions
- Functions can have [default parameters](https://www.hackingwithswift.com/sixty/5/6/default-parameters)

### Lazy
- Only uses value set for var when it's needed

### Programmatic UI
- Auto Layout ([cheat sheet](https://www.hackingwithswift.com/articles/140/the-auto-layout-cheat-sheet))
  - Anchors: efficient to pass them as array to activate/deactivate (`NSLayoutConstraint.activate([...])` or `NSLayoutConstraint.deactivate([...])`
    - Ex: `leadingAnchor`, `trailingAnchor`, `topAnchor`, `bottomAnchor`
  - For `trailingAnchor` and `bottomAnchor`, constant needs to be -ve
    - Ex: `viewName.bottomAnchor.constraint(equalTo: parentView.bottomAnchor, constant: -10)`
- [Content Hugging Priorities and Compression Resistance Priorities](https://medium.com/@dineshk1389/content-hugging-and-compression-resistance-in-ios-35a0e8f19118)

### SwiftUI
- Drag and drop, live preview, cross platform (iOS/macOS/watchOS)
- VHZ Stacks
- Easy to extract views and reuse code (like instantiating objects)

### Optionals (?) • Force Unwrapping (!) • Optional Binding (`if let`) • Nil Coalescing Operator (??)
- Optional: variable that holds either a value or no value (nil)
  - Ex: `let myOptional: String?`, `myOptional` can either be a string value or nil
- Force unwrapping: use `!` when confident that the variable will never be nil
  - Ex: `let text: String = myOptional!`, used because `myOptional` will never be nil
- Optional Binding: checks to see variable is nil, then procedes if it's not
  - Ex: `if let safeOptional = myOptional {...}`, `myOptional` is the variable you want to check, and `safeOptional` is the temporary variable you use inside the if-block if it is indeed not nil
- Nil Coalescing Operator: defaults to value after `??` if variable before it is nil
  - Ex: `let text: String = myOptional ?? "Default Value"`, `text` will be `myOptional` if it's not nil, otherwise if `myOptional` is nil then `text` will be "Default Value"

### Guard let vs If let
- `guard let` focuses on ideal path where variable is non-nil
  - Common at start of methods to verify conditions are correct upfront
  - Use `if let` if you just want to unwrap some optionals, use `guard let` if you’re specifically checking that conditions are correct before continuing
  - Variable in `if let` isn't in scope of subsequent `else` statement, need `guard let` for that (used after `else` in `guard let`)

### as • as? • as!

### Tuple
- Data structure that holds a group of values (can be different types)
- Ex: `let product = (name: "MacBook", price: 1099.99)`, to get "MacBook" you do `product.0`/`product.name` and to get 1099.99 you do `product.1`/`product.price`

### Map • FlatMap • CompactMap
- Map: method that can transform a sequence of elements
  - Ex: `let strings = ["one", "two", "three"]`, `let ints = strings.map { $0.count }` would return `[3,3,5]`
  - Can also use `mapValues()` for dictionaries to transform dictionary values (returns a dictionary)

### Protocols
- `ListDiffable` provides methods needed to compare the identity and equality of 2 objects (need to `import IGListKit`) 

### UITableView
- Search for Table View in Objects library
  - Made up of Table View Cells (Prototype Cells)
  - Need identifier
  - `UITableViewDataSource` protocol
  - `UITableViewDelegate`for when user taps on UITableView
- To improve UI
  - Create new Cocoa Touch class (subclass of UITableViewCell, also create XIB file)
  - Use this for Table View Cells' design

### UILabel

### Delegates

### Model-View-Controller (MVC)
- Model: stores data, View: displays data, Controller: responds to user + manipulates model
- User uses controller, controller manipulates model, model sends data to view, view renders itself to user
- Advantages
  - Well-known, separate responsibilities are clear, data flow is clear
- Disadvantages
  - Controller ends up being huge, blurred separation of concerns, hard to test, leads to small views/models

### Model-View-Presenter (MVP)
- Model stores data that'll be displayed to user, View stores passive UI elements that forward user interaction, Presenter reads data from model + displays it in views

### Model-View-ViewModel (MVVM)
- [Stack Overflow](https://stackoverflow.com/questions/5421874/basic-concepts-of-mvvm-what-should-a-viewmodel-do) definition


### Coordinator
- [Swift Coordinator Design Pattern (iOS, Xcode 12, 2022) - iOS Design Patterns](https://www.youtube.com/watch?v=SAZzcKvOvAE)

### In-App Purchases
- 30% transaction fee
- Tip: make app free to download and give user 80% of full functionality of app, then use paywall (in-app purchases) for advanced functionality like removing ads/premium features/etc.
- Need Apple Developer program and physical device to simulate in-app purchases
- App Store Connect
  - Sandbox testers
- Capabilities --> In-App Purchase --> ON
- `import StoreKit`
  - `SKPaymentQueue.canMakePayments()` returns a boolean
  - `SKMutablePayment()` NSObject
  - `SKPaymentTransactionObserver` protocol
  - `SKPaymentTransactionState` --> purchasing, purchased, failed, restored, deferred
  - UserDefaults are wiped clean if user gets new phone/updates iOS/etc., so a restore button is needed to check if a user has already purchased
  
### CoreML
- Allows you to load a pre-trained model and make predictions (no training, static, not encrypted)
- ML: Teaching a machine how to do something by training it over and over again
  - Model is fed training data
- Supervised (loads of images with labels, like regression/classification) vs unsupervised (unlabelled, like clustering)
- Reinforcement learning: +ve and -ve rewards, like maximizing chess win chances by examining win probability after each move

### ARKit
- SceneKit (3D), SpriteKit (2D), Metal
- art.scnassets folder has cool spaceship

### Design Tools
- [Flat UI Colors 2](https://flatuicolors.com/)
- [HEX to UIColor](https://www.uicolor.io/)
- [Google Fonts](https://fonts.google.com/)
- [SF Symbols](https://developer.apple.com/sf-symbols/)

### Open Source Libraries
- [IGListKit](https://github.com/Instagram/IGListKit)
- [Alamofire](https://github.com/Alamofire/Alamofire)
- [Lottie](https://github.com/airbnb/lottie-ios)
- [Sourcery](https://github.com/krzysztofzablocki/Sourcery)
- [SwiftLint](https://github.com/realm/SwiftLint)

### Developer Tools
- [Tuple - Pair Programming](https://tuple.app/pair-programming-guide/antipatterns)

### To Do
- Filter
- Reduce
