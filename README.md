# Getting Started with Cordova

## What?
Cordova (or PhoneGap) is a framework/set of APIs that allows you to create mobile apps using just HTML, CSS, and Javascript. This is a guide to getting Cordova set up and creating an app from a pre-existing HTML/CSS/JS project.

## Why?
Phone/tablet apps are as popular as ever, and many people prefer using them to a web app in a mobile browser. Cordova allows you to create apps for these users/clients without learning Java or Swift/Objective-C.

## How?
### Step 1. Installing Cordova
If you don't have node installed, install that first: https://nodejs.org/

Next install cordova: 
``` bash
npm install -g cordova
```

### Step 2. Installing the SDK (Software Development Kit)
#### Android
Go to http://developer.android.com/sdk/installing/index.html

From here you can download Android Studio, which is a full IDE for Android development, or you can download the individual SDK tools, and develop using your favourite editor and the command line (which is what we'll be doing in the rest of this guide).

When you've downloaded the sdk tools, move them to an appropriate location. Then, go into the tools folder and run _android_.

This will open the SDK manager. In here, you will want to make sure you have installed:
* From the tools folder:
 * Android SDK Tools
 * Android SDK Platform-tools
 * Android SDK Build-tools

* From Android X.X ,where X.X is the latest version (5.1.1 at the time of writing this guide)
 * SDK Platform
 * At least one System Image (e.g. ARM EABI v7a System Image)

These are the minimum requirements for developing an Android app with Cordova. There are other tools you can install, such as the Google Play services, for developing with the Google APIs, but that won't be covered in this guide.

#### iOS
Go to this page: https://developer.apple.com/xcode/downloads/ and download Xcode. With the introduction of Xcode 7, you can test your app on a real iOS device without paying to join the Apple Developer Program. At the time of writing xCode 7 is still in beta, but it's probably in your best interest to use it.

### Step 3. Making the SDK tools available in your terminal
#### Android
Open your _~/.bash_profile_ file and add the following line, changing 'path/to/' to the path to your file:
``` bash
export PATH=${PATH}:/path/to/android-sdk-macosx/tools:/path/to/android-sdk-macosx/platform-tools
``` 
This will allow you to run the build/emulate/run android commands in your terminal.

If you don't have a bash profile, change to your home folder and create one:
``` bash
cd Users/Username
touch .bash_profile
open .bash_profile
```

####iOS
Cordova doesn't have support for building/emulating with Xcode 7 on the command line yet, so you'll have to build within Xcode itself.

### Step 4. Creating the App
Run the following command (with modifications) in the directory you want the project to be in:
``` bash
cordova create hello com.example.hello HelloWorld
```
Where the first argument (_hello_) is the name of the directory, the second (_com.example.hello_) is a reverse domain style identifier for your project, and the third (_HelloWorld_) is the application's display text that will appear on your device. These second two can be changed later in the _config.xml_ file.

After this, you should have a new direcory, containing a www directory, which is where you will put your code. If you've already got the files you need, put the css file into the css folder, the javascript file into the js folder, and the html in the root of the www directory. If you don't already have the files, _get coding!_

### Step 5. Adding Platforms
Run the following commands to add platforms to your project:
``` bash
cordova platform add android
cordova platform add ios
```

### Step 6. Build the App
#### Android
``` bash
cordova build
```
Or, for specific platforms only:
``` bash
cordova build android
```

#### iOS
Start Xcode and open the .xcodeproj version of your app. This will be inside the platforms/ios directory that was created when you added the iOS platform. In Xcode, make sure your project is selected in the left window, and choose _Build_ from the _Product_ menu.

### Step 7. Test the app with an emulator
#### Android
Open the SDK manager, like we did in [Step 2](https://github.com/Danwhy/cordova-getting-started/blob/master/README.md#step-2-installing-the-sdk).

In the Tools menu, open Manage AVDs.

Then, go to Device Definitions, choose the device you want to emulate and click Create AVD.

Give the emulator a name, select a CPU/ABI and a skin, and click OK.

Now, on the command line run:
``` bash 
cordova emulate android --target=nexus5
```
Where _nexus5_ is the name you gave to your AVD. If you have only created one AVD, you can omit the target:
``` bash
cordova emulate android
```

This will open an emulated Android device, on which you can navigate to and start your app.

####iOS
Inside Xcode again, in the _Product_ menu, go to _Destination_ and choose your simulation device. Then click the _play_ button in the top left of Xcode.

This will open an emulated iOS device, with your app running.

### Step 8. Put the App on your Device
#### Android 
You'll need to have the Developer options enabled on your device. If you're on Android 4.2 or above, these options are hidden by default. To access them:
 1. Go to your device's settings
 2. Go to _About Phone/Device_
 3. Find _Build Number_
 4. Tap it seven times
 5. Go back to the previous screen and you should see a Developer options menu

Once you have access to the developer options, turn on USB Debugging.  

Connect your device to your computer by USB and run the following command in your project directory:
``` bash
cordova run android
```

And with that, your app will be installed on your device.

#### iOS
As long as you're using Xcode 7+, this will be quite simple. If not, you need to sign up to Apple's Developer Program. For the purpose of this guide, we'll assume you're using 7.

Connect your device by USB to your computer.

In Xcode, go to the _Products_ menu again and change the destination to your connected iOS device. Press the _play_ button and your app will install on your device.

##### Sources
* http://www.smashingmagazine.com/blog/2014/02/11/four-ways-to-build-a-mobile-app-part3-phonegap/
* http://cordova.apache.org/docs/en/3.1.0/guide_platforms_android_index.md.html#Android%20Platform%20Guide
* http://cordova.apache.org/docs/en/3.1.0/guide_cli_index.md.html#The%20Command-line%20Interface
* http://developer.android.com/sdk/installing/index.html
* http://developer.android.com/tools/device.html
* http://cordova.apache.org/docs/en/3.1.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide

##### Further Reading/Docs
* http://cordova.apache.org/docs/en/3.1.0/index.html
* http://cordova.apache.org/docs/en/5.0.0/guide_platforms_index.md.html#Platform%20Guides
