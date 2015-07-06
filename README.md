# Getting Started with Cordova

## What?
Cordova (or PhoneGap) is a framework/set of APIs that allows you to create mobile apps using just HTML, CSS and Javascript. This is a guide to getting Cordova set up and creating an app from a pre-existing HTML/CSS/JS project.

## Why?
Phone/tablet apps are as popular as ever, and many people prefer using them to a web app in a mobile browser. Cordova allows you to create apps for these users/clients without learning Java or Swift/Objective-C.

## How?
### Step 1. Installing Cordova
If you don't have node installed, install that first: https://nodejs.org/

Next install cordova: 
``` bash
npm install -g cordova
```

### Step 2. Installing the SDK
#### Android
Go to http://developer.android.com/sdk/installing/index.html

From here you can download Android Studio, which is a full IDE for Android development, or you can download the individual SDK tools, and develop using your favourite editor and the command line (which is what we'll be doing in the rest of this guide).

When you've downloaded the sdk tools, move them to an appropriate location. Then, go into the tools folder and run _android_.

This will open the SDK manager. In here, you will want to make sure you have installed:
* From the tools folder:
 * Android SDK Tools
 * Android SDK Platform-tools
 * Android SDK Build-tools

* From Android X.X ,where X.X is the latest version (5.1.1 as of the time of writing this guide)
 * SDK Platform
 * At least one System Image (e.g. ARM EABI v7a System Image)

These are the minimum requirements for developing an Android app with Cordova. There are other tools you can install, such as the Google Play services, for developing with the Google APIs, but that won't be covered in this guide.

#### iOS
Coming soon...

### Step 3. Making the SDK tools available in your terminal
#### Android
Open your _~/.bash_profile_ file and add the following line, changing 'Users/You/' to the path to your file:
``` bash
export PATH=${PATH}:/Users/You/android-sdk-macosx/tools:/Users/You/android-sdk-macosx/platform-tools
``` 
This will allow you to run the build/emulate/run android commands in your terminal.

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
``` bash
cordova build
```
Or, for specific platforms only:
``` bash
cordova build android
cordova build ios
```

### Step 7. Test the app with an emulator
#### Android
