# dispatch_once

* Executes a block object once and only once for the lifetime of an application.
* Objective-C only

https://developer.apple.com/reference/dispatch/1447169-dispatch_once

```objective-c
static dispatch_once_t onceToken;
dispatch_once(&onceToken, ^{
    // some code that will be executed only once
});
```
