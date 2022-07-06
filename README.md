# SwiftNotes
### Arrays
- `arrayName.append(newElement: Type)`: adds single element to array
- `arrayName.append(contentsOf: Sequence)`: adds another array at the end of arrayName

### Programmatic UI

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
