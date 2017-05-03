遅延実行

## Swift 3.0

```swift
DispatchQueue.main.asyncAfter(deadline: .now() + 1.0) {
}
```

## Objective-C

```objective-c
dispatch_after(dispatch_time(DISPATCH_TIME_NOW, 1.0 * NSEC_PER_SEC), dispatch_get_main_queue(), ^{
});
```
