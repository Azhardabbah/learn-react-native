# Learn React Native :: Workshop 06

[![](https://img.shields.io/badge/React%20Native-v0.44-blue.svg)](https://facebook.github.io/react-native/)

> :coffee: This workshop is about **branding**.

## <a name='TOC'>Summary</a>

01. [Objective](#objective)
02. [Setup](#setup)
02. [Pointers](#pointers)
42. [Credits](#credits)

## <a name='objective'>Objective</a>

We’ll add a custom icon and launch screen to the app that you made in the last challenge.

XXX

Replace this lame icon with a better one. And add a custom launch screen too. (A launch screen is the screen that the user sees while the app is starting. By default React Native builds a launch screen that displays the name of your app.)

## <a name='setup'>Setup</a>

Grab the assets included in the asset directory.

## <a name='pointers'>Pointers</a>

### Making an App Icon

- If you have Photoshop: http://appicontemplate.com/ios9/
- If you don’t: https://makeappicon.com/

### Making Launch Screens

- If you have Photoshop: http://appicontemplate.com/iphonescreenshot/
- If you don’t: http://ticons.fokkezb.nl/


### Adding an App Icon

Time to dive into Xcode. If you don’t already have Xcode open, open `ios/_yourprojectname_.xcproject` in Xcode now. There will be a series of icons on the top of the left-most panel. Click to the Project Navigator. This is a sort of directory view of your project.

XXX

Find and click on `Image.xcassets` (this is a directory containing XCode Assets, hence the name). Within the main content panel, you should now see a list of image assets with only one entry: AppIcon. AppIcon is actually a directory where Xcode expects to find your app’s icons.

XXX

When you click on AppIcon, you’ll see a bunch of labeled blank spaces. These are the various sizes needed for an app icon on different Apple devices.

There are two ways to add actual images for you app icon. You can drag-and-drop images onto the blank spaces for AppIcon, or you can add a new directory of properly prepared directory of icons, and tell your app to use that directory as the icon. (Many icon generators will generate this kind of directory for you.)

For this challenge, let’s use the latter technique. Drag and drop `AppIcon.appiconset` from your workshop files into the panel containing AppIcon. Remove the old, empty AppIcon directory.

Now we need to tell our app where to find our new icons. Go to your project’s general settings (which is more difficult than it might sound… see below).

XXX

##### Adding a Launch Screen

In the Project Navigator in Xcode, find and click on `LaunchScreen.xib` (.xib == Xcode Interface Builder in case you’re curious).

XXX

This is your application’s default launch screen. If you’re an Xcode Interface Builder pro, you can create your own custom launch screen right here. If you’re not, you can tell your app just to use an image instead.

Once your launch screen assets are ready, find and click on `Images.xcassets` in the Project Navigator. Click the “+” at the bottom left of the main content panel, and choose to add a new iOS launch image.

XXX

You’ll now see another set of blank spaces just like we saw when we looked at AppIcon. This time we’ll drag our images into this interface. Drag-and-drop your launch screen images onto the blank spaces to populate the directory.

Now browse to your project’s General settings. Under App Icons and Launch Images, click Use Asset Catalog next to Launch Image Source, then choose Images as the image source. Then select LaunchImage. Finally delete the Launch Screen file entry, and remove LaunchScreen.xib.

Restart the simulator, rebuild your project, and you should see your shiny new launch screen.

##### Viewing Launch Screens

To view your app’s launch screen, you may have to quit the app in the Simulator and then restart it. You can do this by double-clicking the simulated phone’s home button (Cmd+Shift+H), and swiping up, up, and away on your app.

## <a name='gogogo'>Go go go!</a>

Install an app icon and a launch screen. When you’re done move on to [workshop #07](https://github.com/majdi/learn-react-native/tree/master/workshop-07) :wink:

## <a name='credits'>Credits</a>

Write & develop with :heart: by [**Majdi Toumi**](http://majditoumi.com) | [**Mhirba**](http://www.mhirba.com).
