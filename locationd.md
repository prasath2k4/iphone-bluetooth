Installing locationd-injection lib

```
plutil -key EnvironmentVariables -dict /System/Library/LaunchDaemons/com.apple.locationd.plist
plutil -key EnvironmentVariables -key DYLD_INSERT_LIBRARIES -string /usr/lib/locationd-inject.dylib /System/Library/LaunchDaemons/com.apple.locationd.plist

launchctl unload /System/Library/LaunchDaemons/com.apple.locationd.plist
launchctl load /System/Library/LaunchDaemons/com.apple.locationd.plist
```