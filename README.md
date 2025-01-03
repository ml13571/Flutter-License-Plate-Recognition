# Flutter-License-Plate-Recognition

## Overview

This repo demonstrates `ANPR/ALPR(Automatic Number/License Plate Recognition)` engine with high accuracy based on SOTA(State-Of-The-Art) deep learning techniques. </br>
`ANPR/ALPR` was implemented on Flutter framework for both `Android` and `iOS`.

`LPR` solutions utilizes AI and ML to greatly surpass legacy solutions. Now, users can receive a vehicle's plate number in real-time.

The `ALPR` or `LPR` implementation consists of the following steps: `vehicle image capture`, `preprocessing`, `vehicle detection`, `number plate extraction`, `charater segmentation` and `Optical Character Recognition(OCR)`. </br>

The `ALPR` system works in these strides, the initial step is the location of the vehicle and capturing a vehicle image of front or back perspective of the vehicle, the second step is the localization of Number Plate and then extraction of vehicle Number Plate is an image. The final stride uses image segmentation strategy, for the segmentation a few techniques neural network, mathematical morphology, color analysis and histogram analysis. Segmentation is for individual character recognition. Optical Character Recognition (OCR) is one of the strategies to perceive the every character with the assistance of database stored for separate alphanumeric character.

## Screenshots
<p float="left">
  <img src="https://github.com/user-attachments/assets/d19998a8-9b94-47dd-86f5-a206e430d4cf" width=200/>
  <img src="https://github.com/user-attachments/assets/34be1181-fe83-4be0-b955-7c174961410b" width=200/>
  <img src="https://github.com/user-attachments/assets/4d17e31e-d1e0-492a-98bd-c34ed68c3a6a" width=200/>
</p>

<p float="left">
  <img src="https://github.com/user-attachments/assets/dc819a46-cdc7-4459-aca1-f94da8e1a14e" width=200/>
  <img src="https://github.com/user-attachments/assets/84f89d18-9c34-465e-a855-8c2b4467ce69" width=200/>
  <img src="https://github.com/user-attachments/assets/23645cc7-2f79-4deb-becd-2d88cb32c983" width=200/>
</p>

## SDK License
- The code line below shows how to update SDK with the `license key`: https://github.com/jackiewangCV/Flutter-License-Plate-Recognition/blob/401c3bdfde56a716d5a33e3878eaca9a4c4c3081/lib/main.dart#L69-L78

## How To Run
### 1. Flutter Setup
  Make sure you have `Flutter` installed. </br>
  This repo has been built with Flutter version `3.22.3`.</br> 
  If you don't get `Flutter` installed, please follow the instructions provided in the official `Flutter` documentation [here](https://docs.flutter.dev/get-started/install).</br>
  
### 2. Placing Library File
  Please contact us to get our `SDK library` file(`libttvalpr.aar`) and put it on the suitable SDK folder(folder `android/libttvalpr`).</br> 
  
### 3. Running the App
  Try to build this repo to make sure that SDK works fine by linking real `Android` phone, not `simulator`. Once it works fine, you are ready to integrate our SDK to your project.</br>
  Run the following commands:</br>
  ```bash
  flutter pub upgrade
  flutter run
  ```  
  If you plan to run the iOS app, please refer to the following [link](https://docs.flutter.dev/deployment/ios) for detailed instructions.</br>
  
## About SDK

### 1. Set up
#### 1.1 Setting Up ALPR SDK
  > Android
  - Please contact us to get our `SDK library` file(`libttvalpr.aar`) and paste it to SDK folder(folder `android/libttvalpr`).
    And then copy the SDK(folder `libttvalpr`) to the folder `android` in your project.
  - Add SDK to the project in `settings.gradle`.
  ```dart
  include ':libttvalpr'
  ```
#### 1.2 Setting Up ALPR SDK Plugin
  - Copy the folder `alprsdk_plugin` to the `root` folder of your project.</br>
  - Add the dependency in your `pubspec.yaml` file.
  ```dart
    alprsdk_plugin:
      path: ./alprsdk_plugin
  ```
  - Import the `alprsdk_plugin` package.
  ```dart
    import 'package:alprsdk_plugin/alprsdk_plugin.dart';
  ```
### 2 API Usages
#### 2.1 ALPRsdk Plugin
  - Activate the `AlprsdkPlugin` by calling the `setActivation` method:
  ```dart
    final _alprsdkPlugin = AlprsdkPlugin();
    ...
     await _alprsdkPlugin
            .setActivation(
                "o3AfDW+0LAb55qW354xp9ef/Twg1WumIcKaBQLydx+o7+8nuZSo4aL4vVGro3mNCLvo8C2OPNDjZ"
                "/8k+bvgbf8+QszGqG5ubjZOaREXO0Iw8pSepERy4HrWrS6I9ObjuttMUIRHBFNjIsT3RKH57mNv6"
                "1IXxewXlIA2oe5Vak/zaddoKKKcSW+iWJWqIa1MxGn8PpUD1riQS9RrO/cwZsiAJU+5+ekkkyP3C"
                "7eNZGzFfpmkLM55p2F98IMqWHjaMmX0klsNlxE/bdSJD8c2cS/+9DGLqiWb2FHz8FpR6sXjc+eGM"
                "bNtBd0YxqfAy+oeTVdPyw0E17lj+Hilw4L4C6Q==")
            .then((value) => facepluginState = value ?? -1);
  ```
  - Initialize the `AlprsdkPlugin`:
  ```dart
  await _alprsdkPlugin
            .init()
            .then((value) => alprpluginState = value ?? -1)
  ```
  - Extract plates using the `extractFaces` method:
  ```dart
  final plates = await _alprsdkPlugin.extractFaces(path: image.path)
  ```
