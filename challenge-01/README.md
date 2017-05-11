# Learn React Native :: Workshop 01

[![](https://img.shields.io/badge/React%20Native-v0.44-blue.svg)](https://facebook.github.io/react-native/)

> :coffee: This workshop is about **getting started**

## <a name='TOC'>Summary</a>

01. [Objective](#objective)
02. [Setup](#setup)
03. [Pointers](#pointers)
04. [Go go go!](#gogogo)
42. [Credits](#credits)

## <a name='overview'>Overview</a>

The goal of this challenge it to initialize your first React Native app, and get it running in the iOS simulator.

## <a name='setup'>Setup</a>

Remember the core React Native dependencies we mentioned earlier:
- OS X
- Xcode 7.0 or newer
- Node.js 4.0 or newer
- Watchman

Once these dependencies have been successfully installed, you’re ready to begin this challenge.

## <a name='pointers'>Pointers</a>

### Project Initialization

##### What to Do Today

Download the `srcs.zip` file. Go into the unzipped directory (should be named `FirstApp`) and run `npm rebuild`.

##### What You Would Usually Do (But Not Today)

https://facebook.github.io/react-native/docs/getting-started.html#quick-start is the canonical source for information about starting new projects.
Install React Native’s handy CLI: `npm install -g react-native-cli`.

##### Why aren’t we doing this today?

Running `react-native init` will download the newest version of React Native and all of its dependencies. That’s around ~500MB in total.

### Running the Project

Remember that running an in-development React Native project has two components: a packager and an iOS runtime.

From within your project directory, you can start your packager with `npm start` (which under the hood is just an alias for `node node_modules/react-native/local-cli/cli.js start`).

The iOS simulator will serve as our iOS runtime (you can also use an actual device if you have a paid Apple Developer account.) There are two ways to run our project in the simulator:

- If you have `react-native-cli` installed (if running `which react-native-cli` doesn’t return “react-native-cli not found”), you can run the simulator without Xcode open via `react-native-cli run-ios`.

- If you don’t have `react-native-cli` installed, or need Xcode open while you’re working, within your project directory open `ios/FirstApp.xcodeproj` with Xcode, and hit the play icon (the build and run button) in the top left.

If you get an error saying “A build only device cannot be used to run this target.”, to the right of the play icon, click “Generic iOS Device” and select “iPhone 6” from the list of options. Build and run your project again by clicking the play icon. This menu allows you to simulate your app on any Apple device you’d like. Nifty.

### Scaling the Simulator

The iPhone you’re simulating probably has more pixels than the laptop you’re working on. Crazy, right? You can scale the simulator via the Window -> Scale item in the menubar.

## <a name='gogogo'>Go go go!</a>

Go get the project running in the iOS simulator.

[XXX](./assets/screen-app.png)

When you see the above screen, congrats. You’re a **hero**.

## <a name='next'>Next</a>

Well, you have just finished this challenge... easy right? :wink:<br />
Post a screenshot of your app in the `#progress` channel, then move on to the [challenge #02](https://github.com/majdi/learn-react-native/tree/master/challenge-02).

## <a name='credits'>Credits</a>

Write & develop with :heart: by [**Majdi Toumi**](http://majditoumi.com) | [**Mhirba**](http://www.mhirba.com).
