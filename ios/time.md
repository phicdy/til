# Current time

## Swift3

https://developer.apple.com/reference/dispatch/dispatchtime

```swift
let now = DispatchTime.now()
```

## Objective-C

# Wait and execute

## Swift3

```swift
let time = DispatchTime.now() + 10
DispatchQueue.main.asyncAfter(deadlne: time) {
    // some code
}
```

## Objective-C

```objective-c
dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(10 * NSEC_PER_SEC)), 
    dispatch_get_main_queue(), ^{
        // some code
    }
);
```
