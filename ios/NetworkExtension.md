# Network Extension

The Network Extension framework exposes APIs that give you the ability to customize the networking features of iOS and OS X.

https://developer.apple.com/reference/networkextension
https://developer.apple.com/library/content/samplecode/SimpleTunnel/Introduction/Intro.html

# Setup

1. Register apple developer program
2. Open https://developer.apple.com/account/ios/identifier/bundle
3. Select Identifiers => App IDs
4. Click edit button, check the network-extension checkbox
5. Download provisioning profile and set on XCode

## Note

* Since November 10th 2016, we dont need entitlement from apple to use network-extension
* If we use NEHotspotHelper class, go to https://developer.apple.com/contact/network-extension/

# NEPacketTunnelProvider

* The NEPacketTunnelProvider class gives its subclasses access to a virtual network interface via the packetFlow property.
* Subclass of NETunnelProvider

https://developer.apple.com/reference/networkextension/nepackettunnelprovider

## Settings

1. Create a new App Extension target in the project
2. Create a subclass of NEPacketTunnelProvider
3. Set the NSExtensionPrincipalClass key in the the extension's Info.plist to the name of your subclass.
4. Set the NSExtensionPointIdentifier key in the extension's Info.plist to com.apple.networkextension.packet-tunnel.

```xml
<key>NSExtension</key>
<dict>
    <key>NSExtensionPointIdentifier</key>
    <string>com.apple.networkextension.packet-tunnel</string>
    <key>NSExtensionPrincipalClass</key>
    <string>MyCustomPacketTunnelProvider</string>
</dict>
```

# NETunnelProviderManager

Configure and control VPN connections provided by a Tunnel Provider app extension.

https://developer.apple.com/reference/networkextension/netunnelprovidermanager

This class inherits NEVPNMager and can use custom VPN protocol.

## Settings

### Swift 3.0

```swift
let manager = NETunnelProviderManager()
let protocol = NETunnelProviderProtocol()
manager.protocolConfiguration = protocol
manager.isEnabled = true
manager.localizedDescription = "My VPN"

// On Demand Rule https://developer.apple.com/reference/networkextension/neondemandrule
let rule = NEOnDemandRuleConnect.init()
//let rule = NEOnDemandRuleDisconnect.init()
//let rule = NEOnDemandRuleEvaluateConnect.init()
//let rule = NEOnDemandRuleIgnore.init()
rule.interfaceTypeMatch = NEOnDemandRuleInterfaceType.any
rule.dnsSearchDomainMatch = "domain"
rule.dnsServerAddressMatch = "addres"
rule.ssidMatch = "ssid"
var url = URL.init(string: "http://www.google.com")
rule.probeUrl = url
manager.onDemandRules = [rule]
manager.onDemandEnabled = true
```

### Objective-C

```objective-c
NETunnelProviderManager *manager = [[NETunnelProviderManager alloc] init];
NETunnelProviderProtocol *protocol = [[NETunnelProviderProtocol alloc] init];
manager.protocolConfiguration = protocol;
manager.isEnabled = YES;
manager.localizedDescription = @"My VPN";

// On Demand Rule https://developer.apple.com/reference/networkextension/neondemandrule
NEOnDemandRuleConnect *rule = [NEOnDemandRuleConnect new]
//NEOnDemandRuleDisconnect *rule = [NEOnDemandRuleDisconnect new];
//NEOnDemandRuleEvaluateConnect *rule = [NEOnDemandRuleEvaluateConnect new];
//NEOnDemandRuleIgnore *rule = [NEOnDemandRuleIgnore new];
rule.interfaceTypeMatch = NEOnDemandRuleInterfaceTypeAny;
rule.dnsSearchDomainMatch = @"domain";
rule.dnsServerAddressMatch = @"addres";
rule.ssidMatch = @"ssid";
NSURL *url = [[NSURL alloc] initWithString:@"http://www.google.com"];
rule.probeUrl = url;
NSMutableArray *ruleArray = [NSMutableArray array];
[ruleArray addObject: rule];
manager.onDemandRules = ruleArray;
manager.onDemandEnabled = YES;
```

## Save setting

https://developer.apple.com/reference/networkextension/nevpnmanager/1405985-savetopreferences

### Swift 3.0

```swift
let manager = NETunnelProviderManager()
manager.saveToPreferences { (error) -> Void in
}
```

### Objective-C

```objective-c
NETunnelProviderManager *manager = [[NETunnelProviderManager alloc] init];
[manager saveToPreferencesWithCompletionHandler:^(NSError * _Nullable error) {
}];
```

# NETunnelProviderProtocol

* NETunnelProviderProtocol contains configuration parameters for a network tunnel.
* Subclass of NEVPNProtocol

https://developer.apple.com/reference/networkextension/netunnelproviderprotocol

## Setting

### Swift 3.0

```swift
// Identifier setting
let protocol = NETunnelProviderProtocol()
protocol.providerBundleIdentifier = "myidentifier"

// Key-value settings for yourself
// This setting can be obtained in NETunnelProvider.protocolConfiguration.providerConfiguration
var configurations = [String: Any]()
configurations["forMe"] = "someValue"
protocol.providerConfiguration = configurations

// NEVPNProtocol settings
// https://developer.apple.com/reference/networkextension/nevpnprotocol?language=objc
protocol.serverAddress = @"xxx.x.x.x";
protocol.username = @"user";
protocol.disconnectOnSleep = YES;
```

### Objective-C

```objective-c
// Identifier setting
NETunnelProviderProtocol *protocol = [[NETunnelProviderProtocol alloc] init];
protocol.providerBundleIdentifier = @"myidentifier";

// Key-value settings for yourself
// This setting can be obtained in NETunnelProvider.protocolConfiguration.providerConfiguration
NSDictionary *configurations = [[NSDictionary alloc] init];
[configurations setValue:@"someValue" forKey:@"forMe"];
protocol.providerConfiguration = configurations;

// NEVPNProtocol settings
// https://developer.apple.com/reference/networkextension/nevpnprotocol?language=objc
protocol.serverAddress = @"xxx.x.x.x";
protocol.username = @"user";
protocol.disconnectOnSleep = YES;
```
