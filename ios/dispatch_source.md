# Create

* Dispatch source monitors low-level system objects and automatically submit a handler block to a dispatch queue in response to events

https://developer.apple.com/reference/dispatch/1385630-dispatch_source_create?language=objc
https://developer.apple.com/reference/dispatch/dispatch_source_type_constants

```objective-c
dispatch_source_t source = dispatch_source_create(DISPATCH_SOURCE_TYPE_TIMER, 0, 0, dispatch_get_main_queue());
dispatch_source_set_event_handler(source, ^{
});
dispatch_resume(source)
```

