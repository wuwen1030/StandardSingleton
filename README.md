# StandardSingleton
A standard singleton macro.
```
#define SINGLETON_INTERFACE(className,singletonName) +(className *)singletonName;

#define SINGLETON_IMPLEMENTION(className,singletonName)\
\
static className *_##singletonName = nil;\
\
+ (className *)singletonName\
{\
    static dispatch_once_t onceToken;\
    dispatch_once(&onceToken, ^{\
        _##singletonName = [[super allocWithZone:NULL] init];\
    });\
    return _##singletonName;\
}\
\
+ (id)allocWithZone:(struct _NSZone *)zone\
{\
    return [self singletonName];\
}\
\
+ (id)copyWithZone:(struct _NSZone *)zone\
{\
    return [self singletonName];\
}\

```
