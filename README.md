###### Constants in Objective C
Declaring constants in Objective C (like public static string in java)

In .h 
```
@interface NBoxLocationManager : NSObject
FOUNDATION_EXPORT NSString *const NBoxLocationUpdateNotification;
@end
```

In .m 
```
#import "NBoxLocationManager.h"

@implementation NBoxLocationManager
NSString *const NBoxLocationUpdateNotification = @"NBoxLocationUpdateNotification";
@end
```
