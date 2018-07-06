# Swift Extensions


### Date

**Getting end and start of a day**
```swift
func endOfDay() -> Date {
var cal = Calendar.current
cal.timeZone = TimeZone(abbreviation: "UTC")!
var components = cal.dateComponents([.year, .month, .day, .hour, .minute, .second], from: self )

components.hour = 23
components.minute = 59
components.second = 59

return cal.date(from: components)!
}
```

```swift
func startOfDay() -> Date 
{
var cal = Calendar.current
cal.timeZone = TimeZone(abbreviation: "UTC")!
var components = cal.dateComponents([.year, .month, .day, .hour, .minute, .second], from: self )
components.hour = 0
components.minute = 0
components.second = 0
return cal.date(from: components)!
}
```

**Get unix timestamp in miliseconds from Date**

```swift
func toMillis() -> Int64! {
return Int64(self.timeIntervalSince1970 * 1000)
}
```

**Calculate number of days between two Dates**

```swift
func daysBetweenDates(startDate: Date, endDate: Date) -> Int {
let calendar = Calendar.current
let components = calendar.dateComponents([Calendar.Component.day], from: startDate, to: endDate)
return components.day!
}
```

**Adding days / months / years to Date**
You can add negative number value to subtract value
```swift
func add(days:Int) -> Date {
return Calendar.current.date(byAdding: .day, value: days, to: Date())!
}
func add(months:Int) -> Date {
return Calendar.current.date(byAdding: .month, value: months, to: Date())!
}
func add(years:Int) -> Date {
return Calendar.current.date(byAdding: .year, value: years, to: Date())!
}
```

**Get date string with user format**
```swift
func toUserFormatString(format: String = "dd-MM-yyyy HH:mm") -> String
{
let formatter = DateFormatter()
formatter.dateFormat = format
return formatter.string(from: self)

}
```
### UIColor

**Get UIColor from HEX string (with and without # (sharp))**
```swift
func hexStringToUIColor (hex:String) -> UIColor {
var cString:String = hex.trimmingCharacters(in: .whitespacesAndNewlines).uppercased()

if (cString.hasPrefix("#")) {
cString.remove(at: cString.startIndex)
}

if ((cString.characters.count) != 6) {
return UIColor.gray
}

var rgbValue:UInt32 = 0
Scanner(string: cString).scanHexInt32(&rgbValue)

return UIColor(
red: CGFloat((rgbValue & 0xFF0000) >> 16) / 255.0,
green: CGFloat((rgbValue & 0x00FF00) >> 8) / 255.0,
blue: CGFloat(rgbValue & 0x0000FF) / 255.0,
alpha: CGFloat(1.0)
)
}

```

### UIView

**Get most parent viewController of current view**
```
var parentViewController: UIViewController? {
var parentResponder: UIResponder? = self
while parentResponder != nil {
parentResponder = parentResponder!.next
if parentResponder is UIViewController {
return parentResponder as! UIViewController!
}
}
return nil
}
```

### UIViewController

#### Working with keyboards ####

Hide keyboard when user tapped around of element
```swift
func hideKeyboardWhenTappedAround() {
let tap: UITapGestureRecognizer = UITapGestureRecognizer(target: self, action: #selector(UIViewController.dismissKeyboard))
tap.cancelsTouchesInView = false
view.addGestureRecognizer(tap)
}
```
Dismiss keyboard
```swift
@objc func dismissKeyboard() {
view.endEditing(true)
}
```

### Dictonary


### Array


### UIImage


### Float
If you need get clean value of Float number like 1 from 1.0 and 2.3 from 2.3
```
var cleanValue: String
{
return self.truncatingRemainder(dividingBy: 1) == 0 ? String(format: "%.0f", self) : String(self)
}
```

### String
You can combine string with custom divider (like a StringBuilder in normal languages)
```
func combineString(from: [String], divider: String = "\n") -> String {
var allText: String = "";
for t in from {
allText.append(t)
allText.append(divider)
}
return allText

}
```

### Data


### UIDevice


### Bundle


### UIStackView
