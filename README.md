# esim-binary-sdk-ios
An iOS eSIM Framework that allow downloading and installing a carrier eSIM.

# Supported Platforms
* iOS 12.1+ (An iPhone XS, XS Max, XR, or later model running iOS 12.1 or later)

# Features
* Indicates if the device is able to download eSIM or not (Boolean).
* Validating ability to download.
* Prepares the profile.
* Initiates the download process.
* Provides progress status.
* Returns Status of a given profile.
* Download progress percentage.
* Progress bar UI element.

# Installation

## Carthage

[Carthage](https://github.com/Carthage/Carthage) is a decentralized dependency manager that builds your dependencies and provides you with binary frameworks. To integrate iOS eSIM Framework into your Xcode project using Carthage, specify it in your Cartfile:

### GitHub Repository

GitHub repositories (both GitHub.com and GitHub Enterprise) are specified with the github keyword:

```Swift
github "amdocs-iot-mobile/esim-binary-sdk-ios" ~> 1.0
```

### Binary only framework

Compiled binary .framework are specified with the binary keyword and as an https:// URL, a file:// URL, or a relative or an absolute path with no scheme, that returns a binary project specification:

```Swift
binary "https://de.streamezzo.com/esim/Files/sdk/ios/esim_sdk_ios.json"
```

### Binary Project Specification

A binary project specification can be used to list the locations and versions of compiled frameworks. This data must be available via https and could be served from a static file or dynamically.

* The JSON specification file name should have the same name as the framework and not be named Carthage.json, (example: MyFramework.json).
* The JSON structure is a top-level dictionary with the key-value pairs of version / location.
* The version must be a semantic version. Git branches, tags and commits are not valid.
* The location must be an https url.

#### Example binary project specification

```Json
{
	"1.0.0": "https://de.streamezzo.com/esim/Files/sdk/ios/esim_sdk_ios.framework.zip"
}
```
