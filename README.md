# android-imaging-utils
A simple library that makes it easier to use the camera and do image processing via opencv.

# Installation
1 - Add this to the allProjects repositories:
```gradle
    maven { url 'https://jitpack.io' }
```
2 - Add this as an app dependency:
```gradle
    compile 'com.github.ravindu1024:android-imaging-utils:v1.0.0-alpha3'
```

# Features
- OpenCV integration
- Helper classes for Camera and Video Recording

# Usage
1 - Open Camera
```java
CameraController.connect(CameraController.CameraType.Default, 90);

CameraController.PreviewSize p = CameraController.getBestPreviewSize(640, 480); //get the best preview matching the aspect ratio

CameraController.setPreviewCallback(...);

CameraController.startPreview(previewTexture, p);
```
2 - Close/Disconnect Camera
```java
CameraController.disconnect();
```
3 - Start Video Recording
```java
VideoRecorder.startRecording(saveFilePath, rotation, maxRecordLengthMillis, camCoderProfile);
```
4 - Stop Recording
```java
VideoRecorder.stopRecording();
```

# Supported ABIs
- armeabi
- armeabi-v7a
- arm64-v8a
- mips
- x86

# Binary Size
The library size will be around 40MB with opencv 3.3.0 so if you need to keep the apk size small, include the following in your app gradle file, in the android tag
```gradle
splits {
        abi {
            enable true

            reset()

            include "x86", "armeabi-v7a"
            universalApk false
        }
    }
```
This creates 2 apk files - one for arm and one for x86 platforms.
