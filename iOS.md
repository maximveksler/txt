# Screen Sizes and resolutions
![Size of Screen](https://raw.githubusercontent.com/maximveksler/null/master/iOS/Sizes%20Of%20Screen.png)

# Add text to NSScrollView

```swift
@IBOutlet weak var textScroll: NSScrollView!
    
let text = textScroll.documentView!.textStorage!!
let attr = NSAttributedString(string: "Hello World")

text.appendAttributedString(attr)
```
