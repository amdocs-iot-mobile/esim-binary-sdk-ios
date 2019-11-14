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

# Getting Started
The GitHub repository has an example app that should demonstrate of all the supported features of the SDK. Please check the example for more detailed code samples. The following samples will demonstrate all functionalities.

# Installation

## Carthage

[Carthage](https://github.com/Carthage/Carthage) is a decentralized dependency manager that builds your dependencies and provides you with binary frameworks. To integrate iOS eSIM Framework into your Xcode project using Carthage, specify it in your Cartfile:

```Swift
github "amdocs-iot-mobile/esim-binary-sdk-ios" ~> 1.0
```

## LPA (Local Profile Assistant)

The first step is to create a new instance of the LPA manager class.

```Swift
  let lpa = LpaManager()
```

If we want to know if the device support eSIM or not, we should call isESimSupported function.

```Swift
  if (lpa.isESimSupported()) {
    print("> eSIM supported")
  } else {
    print("> eSIM not supported")
  }
```

Initiates the download subscription process.

```Swift
  lpa.downloadSubscription(activationCode: "code") { result in
    
    print(result.rawValue)
    
    switch result {
      
      case .fail:
        print("- fail")
      case .success:
        print("- success")
      case .unknown:
        print("- unknown")
      default:
        print("- default")
        }
  }
```

## Orchestrator

The first step is to create a new instance of the Orchestrator class.

```Swift
  let orchestratorManager = OrchestratorManager(baseUrl: "url")
```

Sign in with given credentials

```Swift
  orchestratorManager.signIn(userName: "userName", password: "password") { (orchestratorResponse) in
    
    switch orchestratorResponse.successCode {
      
      case ResponseCode.SUCCESS_CODE_SUCCESS:
        print("signIn success: ", orchestratorResponse.successCode)
      default:
        print("signIn failure: ", orchestratorResponse.successCode)
        print("signIn error: ", orchestratorResponse.error ?? "N/A")
        }
  }
```

Check if the profile is ready to be download or not

```Swift
  
  orchestratorManager.isIccidReady(iccid: "iccid", completion: { (isIccidReadyResponse) in
    
    if let iccidReady = isIccidReadyResponse.iccidReady {
      print("- isIccidReady: \(iccidReady)")
    }
  })
```

Download the given profile

```Swift

  orchestratorManager.submitOrder(completion: { (orchestratorResponse) in
  
    switch orchestratorResponse.successCode {
    
      case ResponseCode.SUCCESS_CODE_SUCCESS:
        print("- submitOrder SUCCESS")
      default:
        print("- submitOrder FAILURE")
      }
  })
```
