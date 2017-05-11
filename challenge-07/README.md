# Learn React Native :: Workshop 07

[![](https://img.shields.io/badge/React%20Native-v0.44-blue.svg)](https://facebook.github.io/react-native/)

> :coffee: This workshop is about **TOTP**.

Now that you’ve got the basics of a React Native app down, it’s time to start work on your first real, useful app.

We’re gonna build a **Time-based One Time Password (TOTP)** generator app (just like [Google Authenticator](https://itunes.apple.com/us/app/google-authenticator/id388497605?mt=8)). These kinds of apps are popular for 2-factor authentication across a wide range of services (Like Google, AWS, etc.).

If you’re unfamiliar with TOTP-based authentication, it goes like this: When I setup 2-factor authentication for my Gmail account, Gmail generates a secret which I record in my TOTP app. Using this shared secret, both my app and Gmail can generate the same time-sensitive passcodes at the same time. When Gmail asks for my 2nd factor, I provide the code my app generates, Gmail checks to see if the code is what it should be given the current time, and Gmail lets me in.

If you’re unfamiliar with TOTP-based 2-factor auth, watch this video to see how it in action with Google’s Authenticator TOTP app.

If you’re interested in learning more about the TOTP algorithm, you can check out [this article](http://jacob.jkrall.net/totp/), but that won’t be necessary to make this app (we’ve handled the TOTP algorithm for you).

## <a name='TOC'>Summary</a>

01. [Objective](#objective)
02. [Setup](#setup)
02. [Pointers](#pointers)
42. [Credits](#credits)


## <a name='objective'>Objective</a>

Build a TOTP app! The features of the TOTP app you’ll build are as follows:

- A user can view TOTP codes
- A user can click a TOTP code to copy it to the phone’s clipboard
- A user can add new TOTP code generators (via manual entry and QR scanning)
- A user can remove TOTP code generators

Feel free to continue the challenge with your own features.

## <a name='challenge-tasks'>Challenge Tasks</a>

To help keep you on track, we’ve broken this app down into sub-challenges.

## <a name='sub-challenge-A'>A - Setup</a>

### Objectives

- Initialize a new app project.
- Add a custom app icon.
- Add a custom launch screen.
- Add your app’s name and some basic styles to the main screen.

You can create your own app icons and launch screens, or you can use one provided in the asset directory.

### Setup

Just run `react-native init` to start the new project from scratch :)

### Pointers

No pointers on this one. You’ve got this.

### Get to it.

After following the setup directions, you’ll have an app in a freshly-initialized state.
Go and complete the rest of the sub-challenges bellows.

## <a name='sub-challenge-B'>B - Displaying the codes</a>

### Objectives

Display a list generated codes and their lifespans. Since the codes are time-sensitive, be sure that the info on the screen updates regularly. (Don’t worry about the adding new code generators functionality just yet. Just hardcode some code generators into component state for this challenge. See below for some example code.)

### Pointers

##### TOTP Algorithm

You don’t need to implement the TOTP algo. We’ve done it for you!
Just drop `sha.js` and `totp.js` from the incs files into your project and import them wherever you need them.
Below is an example of how to use the provided totp library to generate codes and code lifespans:

```js
import generateOTP from '../lib/totp' // or wherever you placed totp.js

const MyComponent = React.createClass({
  getInitialState() {
    return {
      generators: [
        {
          name: 'Gmail <js-ios@gmail.com>',
          secret: 'abcdefghijklmnop'
        }
      ]
    }
  },

  renderGenerator(generator) {
    const { otp, secondsBeforeExpiration } = generateOTP(generator)
    // `otp` is the One Time Password, that is the code to be used as a second factor
    // `secondsBeforeExpiration` is an integer representation of how much longer (in seconds) the otp is valid

    return (
      <View>
        <Text>{ generator.name } | { otp } | { secondsBeforeExpiration }</Text>
      </View>
    )
  },

  render() {
    return (
      <View>
        { this.state.generators.map(this.renderGenerator) }
      </View>
    )
  }
})
```

##### ListView

While it is normally advisable to use `<ListView>` for lists, the time-based
rerendering of TOTP codes complicates its use. Feel free to see how far you can
get with `<ListView>`, but don’t worry if you have to fall back to nested `<View>`s.

### Get to it.

When you’ve completed the objective, post a screenshot of your app in the #progress
channel, then move on to the next sub-challenge bellows

## <a name='sub-challenge-C'>C - Accepting and Storing User Input</a>

### Objectives

Allow your users to add code generators. Be sure to store this generator configuration durably so that they don’t disappear when the app quits!

Code generators require two pieces of information:
- A name (to identify what the code is for), which can be any string
- A secret (to generate the codes), which must be a 16 character string.

Most TOTP apps allow codes to be added simply by scanning a QR code. For this challenge, just let the user define generator config via text fields. (Don’t worry, we’ll get to that cool QR-reading functionality)

### Extra Credit

It would be nice to validate the user’s input for generator secrets. It would also be nice to let users delete code generators that they’ve added.

### Pointers

##### Persistence

For persistence, you might want to take a look at [`AsyncStorage`](https://facebook.github.io/react-native/docs/asyncstorage.html#content).

Here’s a teaser:

```js
AsyncStorage.setItem('key-based-location-of-thing-to-be-stored', 'some value', (error) => {
  if (error) {
    alert(error)
  } else {
    // 'some value' is now stored durably at the key 'key-based-location-of-thing-to-be-stored'.
  }
})
```

##### User Input

There are no `<form>` or `<input>` component types in React Native.
Instead we have a selection of native input UI available such as [`<TextInput>`](https://facebook.github.io/react-native/docs/textinput.html#content),
[`<Switch>`](https://facebook.github.io/react-native/docs/switch.html#content), [`<Picker>`](https://facebook.github.io/react-native/docs/picker.html#content), [`<SliderIOS>`](https://facebook.github.io/react-native/docs/sliderios.html#content),
and [`<DatePickerIOS>`](https://facebook.github.io/react-native/docs/datepickerios.html#content).

##### Get to it.

When you’ve completed the objectives, post a screenshot of your app in the `#progress` channel, then move on to the next sub-challenge.

## <a name='sub-challenge-A'>A - Setup</a>

### Objectives

## <a name='sub-challenge-A'>A - Setup</a>

### Objectives

## <a name='gogogo'>Go go go!</a>

Install an app icon and a launch screen. When you’re done move on to [workshop #07](https://github.com/majdi/learn-react-native/tree/master/workshop-07) :wink:

## <a name='credits'>Credits</a>

Write & develop with :heart: by [**Majdi Toumi**](http://majditoumi.com) | [**Mhirba**](http://www.mhirba.com).
