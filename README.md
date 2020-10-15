# ActiveconnectiOS-Framework
[Activeconnect](https://activeconnect.io) is a system that enables authentication without using passwords.
This framework can be used to integrate Activeconnect into iOS applications.
An overview of the Activeconnect system can be found [here](https://activeconnect.readthedocs.io/en/latest).

## Installation
The easiest way to integrate Activeconnect into your application is to use [CocoaPods](https://cocoapods.org).
To integrate ActiveconnectiOS into your xCode project using CocoaPods, specify it in your `podfile`.
```
pod 'ActiveconnectiOS', '~>0.1.0'
```

## Getting Started
### Create an Activeconnect account and Application
The first stage in inetgrating Activeconnect into your applicaton is to create an Activeconnect Application as described [here](https://activeconnect.readthedocs.io/en/latest/getting_started.html).
**Save the application id and application secret for your Activeconnec Application you will need them to communicate with Activeconnect.**

### Add the ActiveconnectiOS framework to your project
To integrate ActiveconnectiOS into your xCode project using CocoaPods, specify it in your `podfile`.
```
pod 'ActiveconnectiOS', '~>0.1.0'
```

### Enable PushNotifications
Activeconnect uses PushNotifications to notify users of Authentication Requests.
Add the [Push Notifications](https://developer.apple.com/documentation/usernotifications) entitlement to your application.

### Configure Activeconnect Notifications Credentials
In order to send Push Notifications to your application you need to configure your Activeconnect.
- Download the APNS certificates for your application.
- Import the certificate and private key into KeyChain (both development and production keys).
- Export the certificate and private key from KeyChain as .p12 files.
- Open the [Activeconnect Console](https://activeconnect.activeapi.ninja/applications).
- Select you application and click the **Details** button.
- In the details page click the settings icon and select **Notification Settings**.
- On the Notifications Settings page click the **Edit** button for iOS.
- On the **Apple iOS Notification Settings** page select **Custom iOS** app from the dropdown.
- Update the credentials with your APNS certificate and Private Key.
- Repeat the process for APNS Sandbox using your development credentials.
Activeconnect will now route your users authentication requests to your iOS application.

### Applications Entitlements
Activeconnect use Camera and Bluetooth services on your user's mobile device.
You must add the following entries to your application's `info.plist`.
```
NSBluetoothAlwaysUsageDescription [YOUR APPLICATION NAME] uses Bluetooth to verify proximity. We do not send or colllect any personal information.
NSBluetoothPeripheralUsageDescription [YOUR APPLICATION NAME] uses Bluetooth to verify proximity. We do not send or colllect any personal information.
NSCameraUsageDescription [YOUR APPLICATION NAME] uses the camera to capture images required for facial recognition.
NSFaceIDUsageDescription [YOUR APPLICATION NAME] uses FaceID to verify that you can unlock your phone.
NSPhotoLibraryUsageDescription [YOUR APPLICATION NAME] will not use any of your stored images.
```
### Background Modes
Add the Background Modes entitlement to your application in xCode.
Enable the following modes:
- Acts as a Bluetooth LE accessory
- Remote Notifications

