# Install

## Mac

http://stackoverflow.com/questions/26242156/install-wireshark-on-macos-x-via-brew

```bash
brew install wireshark --with-qt5
```

# Launch

## Mac

```bash
cd /usr/local/Cellar/wireshark/2.2.5/Wireshark.app/Contents/MacOS
sudo ./Wireshark
```

# Monitor iPhone's packets

At first, you connect the iPhone and get UUID from iTunes.

```bash
rvictl -s <UUID>
Starting device <UUID> [SUCCEEDED] with interface xxxx # xxxx is interface
```

And then launch Wireshark and select the interface
