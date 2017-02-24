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

# NETunnelProviderManager

Configure and control VPN connections provided by a Tunnel Provider app extension.

https://developer.apple.com/reference/networkextension/netunnelprovidermanager

This class inherits NEVPNMager and can use custom VPN protocol.

## Save setting

https://developer.apple.com/reference/networkextension/nevpnmanager/1405985-savetopreferences

```swift
let manager = NETunnelProviderManager()
manager.saveToPreferences { (error) -> Void in
}
```

# NEPacketTunnelProvider

The NEPacketTunnelProvider class gives its subclasses access to a virtual network interface via the packetFlow property.

https://developer.apple.com/reference/networkextension/nepackettunnelprovider

## Setting

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
