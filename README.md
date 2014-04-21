###### Constants in Objective C
Declaring constants in Objective C (like public static string in java)

In .h 
```objc
@interface NBoxLocationManager : NSObject
FOUNDATION_EXPORT NSString *const NBoxLocationUpdateNotification;
@end
```

In .m 
```objc
#import "NBoxLocationManager.h"

@implementation NBoxLocationManager
NSString *const NBoxLocationUpdateNotification = @"NBoxLocationUpdateNotification";
@end
```
