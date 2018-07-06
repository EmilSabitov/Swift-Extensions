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



### UIColor


### UIView


### UIViewController


### Dictonary


### Array


### UIImage


### Float


### String

### Data


### UIDevice


### Bundle


### UIStackView
