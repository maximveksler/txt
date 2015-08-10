# print class

```swift
print(_stdlib_getDemangledTypeName(textScroll)) 
// Swift.ImplicitlyUnwrappedOptional<NSScrollView>

print(textScroll.dynamicType) 
// ImplicitlyUnwrappedOptional<NSScrollView>
```

# Add text to NSScrollView

```swift
    @IBOutlet weak var textScroll: NSScrollView!
    
let text = textScroll.documentView!.textStorage!!
let attr = NSAttributedString(string: "Hello World")

text.appendAttributedString(attr)
```
