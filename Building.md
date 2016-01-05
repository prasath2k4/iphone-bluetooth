# Building the project #

# Requirements #
Mac OS X 10.6.x, XCode that came with iPhone SDK for iOS 4.x


# Steps #

  * Check out the complete project
  * Disable iOS SDK code signing requirement:
    * `sudo vim /Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS4.2.sdk/SDKSettings.plist`
    * `<key>``CODE_SIGNING_REQUIRED``</key>``<string>``NO``</string>`
  * Ensure a self-signed certificate named 'ssc' (or change the post-build script to use ldid pseudo-signing or use your dev certificate and remove the post-build script):
    * http://docs.info.apple.com/article.html?path=Mac/10.6/en/8916.html
    * Name: **ssc**
    * Certificate Type: Code signing
    * Make sure to click 'Always Allow' when Keychain Access dialog appears on the first invocation of codesign.

  * Setting up MiG server header and stub generation
    * `sudo cp "REPLACE_WITH_SVN_ROOT/iphone-bluetooth/btGpsServer/MIG xcode patches/MiG.xcspec" "/Developer/Platforms/iPhoneOS.platform/Developer/Library/Xcode/Plug-ins/iPhoneOS Build System Support.xcplugin/Contents/Resources/MiG.xcspec"`
    * Restart XCode, now btGpsServer project properties should show four items in 'Mig - BuildOptions' category.

  * To build the main deb:
    * `cd "REPLACE_WITH_SVN_ROOT/iphone-bluetooth/build-all"`
    * `./build.sh`
    * enter the pass for sudo when prompted (needed to chown binaries before running dpkg)

  * To build the Problem Reporter:
    * `cd "REPLACE_WITH_SVN_ROOT/iphone-bluetooth/ReportingUI"`
    * `./build.sh`
    * enter the pass for sudo when prompted (needed to chown binaries before running dpkg)