# Constants in Objective C
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

# Singleton in Objective C

```objc
#import "NBoxLocationManager.h"

@interface NBoxLocationManager()
@property (nonatomic) CLLocationManager *locationManager;
@end

@implementation NBoxLocationManager

static BOOL initialized = NO;
static NBoxLocationManager *sharedSingleton;

// Designated method by which people should be accessing this singleton.
+ (id)sharedInstance
{
    return sharedSingleton;
}

// initialize is a class method, called for the first time class is loaded.
+ (void)initialize
{
    NSLog(@"NBoxLocationManager initialize %p", self);
    
    if(!initialized) {
        sharedSingleton = [[NBoxLocationManager alloc] init];
        initialized = YES;
    }
}

// "private" init, designed to be called from initialize, and only once.
- (instancetype)init
{
    self = [super init];
    NSLog(@"NBoxLocationManager init %p", self);

    if(initialized) {
        [NSException raise:@"NBoxLocationManager reinitialized" format:@"NBoxLocationManager should be obtained with +initialize"];
    }
    
    self.locationManager = [[CLLocationManager alloc] init];
    
    // ...
    // rest goes here
    // ...
}

```
