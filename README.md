- Step 1: Setting up the development environment

https://reactnative.dev/docs/environment-setup

- Step 2: Create Project
+ Open terminal 
+ cd to Root folder that included project
+ Run code in terminal:
npx react-native init testmeup --version 0.70

- Step 3: Run project
+ Go to project by command:
cd testmeup
Run in IOS: npx react-native run-ios
Run in Android: npx react-native run-android
+ The project setup correctly if you see “Welcome To React Native” screen. If you can’t see this screen, please check again step 1 and create again project to test.


- Step 4: Install dependencies

+ npm install @react-native-async-storage/async-storage@1.17.11
+ npm install react-native-barcode-mask@1.2.4
+ npm install react-native-camera@4.2.1
+ npm install react-native-gesture-handler@2.8.0
+ npm install @react-navigation/native@6.1.1
+ npm install @react-navigation/native-stack@6.9.7
+ npm i deprecated-react-native-prop-types@2.2.0
+ npm install react-native-screens@3.18.2
+ npm install react-native-safe-area-context@4.4.1

- Step 5: Fix for React Native Camera

- Go to node_modules/react-native-camera/src/RNCamera.js and 
Replace code

import {
  findNodeHandle,
  Platform,
  NativeModules,
  ViewPropTypes,
  requireNativeComponent,
  View,
  ActivityIndicator,
  Text,
  StyleSheet,
  PermissionsAndroid,
} from 'react-native';

To

import {
  findNodeHandle,
  Platform,
  NativeModules,
  requireNativeComponent,
  View,
  ActivityIndicator,
  Text,
  StyleSheet,
  PermissionsAndroid,
} from 'react-native';

import { ViewPropTypes } from 'deprecated-react-native-prop-types';

- Develop environment in MacOs - IOS

- Go to testmeup/ios/testmeup/Info.plist and add bellow code. Note insert before </dict>

	<key>NSCameraUsageDescription</key>
    <string>${PRODUCT_NAME} Camera Usage</string>

    <key>NSBluetoothPeripheralUsageDescription</key>
    <string>${PRODUCT_NAME} BluetoothPeripheral</string>

    <key>NSCalendarsUsageDescription</key>
    <string>${PRODUCT_NAME} Calendar Usage</string>

    <key>NSContactsUsageDescription</key>
    <string>${PRODUCT_NAME} Contact fetch</string>

    <key>NSHealthShareUsageDescription</key>
    <string>${PRODUCT_NAME} Health Description</string>

    <key>NSHealthUpdateUsageDescription</key>
    <string>${PRODUCT_NAME} Health Updates</string>

    <key>NSHomeKitUsageDescription</key>
    <string>${PRODUCT_NAME} HomeKit Usage</string>

    <key>NSLocationAlwaysUsageDescription</key>
    <string>${PRODUCT_NAME} Use location always</string>

    <key>NSLocationUsageDescription</key>
    <string>${PRODUCT_NAME} Location Updates</string>

    <key>NSLocationWhenInUseUsageDescription</key>
    <string>${PRODUCT_NAME} WhenInUse Location</string>

    <key>NSAppleMusicUsageDescription</key>
    <string>${PRODUCT_NAME} Music Usage</string>

    <key>NSMicrophoneUsageDescription</key>
    <string>${PRODUCT_NAME} Microphone Usage</string>

    <key>NSMotionUsageDescription</key>
    <string>${PRODUCT_NAME} Motion Usage</string>

    <key>kTCCServiceMediaLibrary</key>
    <string>${PRODUCT_NAME} MediaLibrary Usage</string>

    <key>NSPhotoLibraryUsageDescription</key>
    <string>${PRODUCT_NAME} PhotoLibrary Usage</string>

    <key>NSRemindersUsageDescription</key>
    <string>${PRODUCT_NAME} Reminder Usage</string>

    <key>NSSiriUsageDescription</key>
    <string>${PRODUCT_NAME} Siri Usage</string>

    <key>NSSpeechRecognitionUsageDescription</key>
    <string>${PRODUCT_NAME} Speech Recognition Usage</string>

    <key>NSVideoSubscriberAccountUsageDescription</key>
    <string>${PRODUCT_NAME} Video Subscribe Usage</string>

- Install pod by:
+ cd ios
+ pod install


- Develop environment in MacOs - Android

+ Install Android Studio 

+ Add permissions to your app android/app/src/main/AndroidManifest.xml file:

	<!-- Required -->
    <uses-permission android:name="android.permission.CAMERA" />

    <!-- Include this only if you are planning to use the camera roll -->
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />

    <!-- Include this only if you are planning to use the microphone for video recording -->
    <uses-permission android:name="android.permission.RECORD_AUDIO"/>


+ Insert the following lines in android/app/build.gradle:
android {
  ...
  defaultConfig {
    ...
    missingDimensionStrategy 'react-native-camera', 'general' // <--- insert this line
  }
}

Note: You have to one Android Studio before run above command also choose simulator output in Android Studio.


Step 6: Copy App.js and ‘src’ folder from ‘Code’ folder in package to ‘testmeup’ folder

- Run app in IOS
+ cd root/testmeup
+ npx react-native run-ios

- Run app in Android
+ cd root/testmeup
+ npx react-native run-android

Step 7: For first login app:
Please login app then logout and login again.
