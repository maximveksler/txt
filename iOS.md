# Screen Sizes and resolutions

# Add text to NSScrollView

```swift
    @IBOutlet weak var textScroll: NSScrollView!
    
let text = textScroll.documentView!.textStorage!!
let attr = NSAttributedString(string: "Hello World")

text.appendAttributedString(attr)
```
