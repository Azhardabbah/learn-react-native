# Learn React Native :: challenge 07

[![](https://img.shields.io/badge/React%20Native-v0.44-blue.svg)](https://facebook.github.io/react-native/)

> :coffee: This challenge is about **TOTP**.

Now that you’ve got the basics of a React Native app down, it’s time to start work on your first real, useful app.

We’re gonna build a **Time-based One Time Password (TOTP)** generator app (just like [Google Authenticator](https://itunes.apple.com/us/app/google-authenticator/id388497605?mt=8)). These kinds of apps are popular for 2-factor authentication across a wide range of services (Like Google, AWS, etc.).

If you’re unfamiliar with TOTP-based authentication, it goes like this: When I setup 2-factor authentication for my Gmail account, Gmail generates a secret which I record in my TOTP app. Using this shared secret, both my app and Gmail can generate the same time-sensitive passcodes at the same time. When Gmail asks for my 2nd factor, I provide the code my app generates, Gmail checks to see if the code is what it should be given the current time, and Gmail lets me in.

If you’re unfamiliar with TOTP-based 2-factor auth, watch this video to see how it in action with Google’s Authenticator TOTP app.

If you’re interested in learning more about the TOTP algorithm, you can check out [this article](http://jacob.jkrall.net/totp/), but that won’t be necessary to make this app (we’ve handled the TOTP algorithm for you).

## <a name='TOC'>Summary</a>

02. [Objectives](#objectives)
03. [Summary](#TOC)
04. [Objective](#objective)
05. [A - Getting Setup](#sub-challenge-A)
06. [B - Displaying the codes](#sub-challenge-B)
07. [C - Accepting and Storing User Input](#sub-challenge-C)
08. [D - Routing (Optional)](#sub-challenge-D)
09. [E - Adding Copy-to-Clipboard Functionality](#sub-challenge-E)
10. [F - Adding QR-reading Functionality](#sub-challenge-F)
42. [Credits](#credits)

## <a name='objective'>Objective</a>

Build a TOTP app! The features of the TOTP app you’ll build are as follows:

- A user can view TOTP codes
- A user can click a TOTP code to copy it to the phone’s clipboard
- A user can add new TOTP code generators (via manual entry and QR scanning)
- A user can remove TOTP code generators

Feel free to continue the challenge with your own features.

To help keep you on track, we’ve broken this app down into sub-challenges.

## <a name='sub-challenge-A'>A - Getting Setup</a>

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

### Go go go!

After following the setup directions, you’ll have an app in a freshly-initialized state.
Go and complete the rest of the sub-challenges.

When you’re done, post a screenshot of your app in the #progress channel, then move on to the next challenge.

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

### Go go go!

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

It would be nice to validate the user’s input for generator secrets.
It would also be nice to let users delete code generators that they’ve added.

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

##### Go go go!

When you’ve completed the objectives, post a screenshot of your app in the `#progress` channel, then move on to the next sub-challenge.

## <a name='sub-challenge-D'>D - Routing (Optional)</a>

### Objectives

This is an optional challenge. The community has not yet settled on a single
best routing solution (see Options below). The state of routing is in fact in
such flux that React Native currently includes an undocumented [experimental alternative](https://github.com/facebook/react-native/blob/73bdef4089d6290c5146b265b3df5719410788e1/Examples/UIExplorer/NavigationExperimental/NavigationExperimentalExample.js) to <Navigator>.
It’s therefore unclear at the moment how valuable intimate knowledge of `<Navigator>`‘s
API will be in the near future.

The direction you choose to take with this challenge is up to you. Dive right
into `<Navigator>`, or make your way with a 3rd party library. If you’re brave,
work through this challenge until you’re finished. If you’re not feeling it,
move along to Challenge 7e. You can always come back to this one later.

The ultimate goal for this challenge is to split the app into multiple pages.
How you choose to do this is entirely up to you.

### Pointers

##### Routing Options

There is a plethora of routing options currently available to React Native.
The first three are included in the React Native core and the rest are 3rd party
libraries.

- [Navigator](https://facebook.github.io/react-native/docs/navigator.html#content)
- [NavigatorIOS](https://facebook.github.io/react-native/docs/navigatorios.html#content)
- [NavigationExperimental](https://share.viget.com/sxsw/learning-react-native/lessons/7d-routing/[a%20viable%20alternative](https://github.com/ericvicenti/navigation-rfc)
- [ExNavigator (built on top of Navigator)](https://github.com/exponentjs/ex-navigator)
- [React Native Router Flux (built on top of ExNavigator)](https://github.com/aksonov/react-native-router-flux)
- [React Native Simple Router](https://github.com/react-native-simple-router-community/react-native-simple-router) - inspired by React Router](https://github.com/reactjs/react-router)

##### Navigator Gotchas

Note that the component defined in `initialRoute` will not update when its
passed props change. In the following example, `MyView` will not rerender in
response to `this.setState({ bar: 'gold' })` in the containing component.

```js
// ...

render: function() {
  return (
    <NavigatorIOS
      initialRoute={{
        component: MyView,
        title: 'My View Title',
        passProps: { foo: this.state.bar },
      }}
    />
  );
},

// ...
```

There is a helpful little hack that lets you give route components more control over their own nav bar behavior (instead of defining it completely wherever you define the route object itself). The hack is detailed in the example below:

```js
// ...

componentWillMount() {
  this.setRightButtonAction()
},

setRightButtonAction() {
  // Get the current route.
  var route = this.props.navigator.navigationContext.currentRoute;
  // Change the route.
  route.onRightButtonPress = () => {
    this.props.navigator.push({
      title: 'New Widget',
      component: NewWidgetPage,
      passProps:  {
        doSomething: this.doSomething
      },
      leftButtonTitle: 'Back',
      onLeftButtonPress: () => {
        this.props.navigator.pop()
      }
    })
  }

  // Use the modified route. (This won't cause a rerender.)
  this.props.navigator.replace(route)
},

// ...
```

##### Flux

Much of the complication around using Navigator is related to passed properties.
Using a more advanced application architecture like [`Flux`](https://facebook.github.io/flux/)
can reduce your application’s reliance on passed props and make routing much easier. [`Microcosm`](https://github.com/vigetlabs/microcosm) and [`Redux`](https://github.com/reactjs/redux)
are good libraries to look at if you’re interested in moving to Flux.

### Go go go!

When you’ve make your multi-page, routed app, post a screenshot or a video
of your app in action in the #progress channel, then move on to the next challenge.

## <a name='sub-challenge-E'>E - Adding Copy-to-Clipboard Functionality</a>

### Objectives

TOTP codes from our app are commonly needed within other apps on the same phone.
Your goal for this challenge is to copy a code to the phone’s clipboard when
it’s clicked, so that the user can just paste the code wherever they need it
(instead of having to remember it and type it out).

### Pointers

Clipboard interaction is actually part of the React Native core now
(it’s an [undocumented feature](https://github.com/facebook/react-native/blob/46a8f1d8e0f2f779bc09395f02be1d0b71587482/Libraries/Components/Clipboard/Clipboard.js))… but let’s try out adding a 3rd party
dependency for learning’s sake. Try `react-native-clipboard`.

### Installing 3rd Party Libraries

Since many 3rd party libraries for React Native include some amount of
Objective-C or Swift code, they must be linked to your project after they are installed.

Directions for linking libraries manually (not recommended) can be found
[in the docs](https://facebook.github.io/react-native/docs/linking-libraries-ios.html#content).

The easiest way to install and link 3rd party libraries is via [npm](https://www.npmjs.com/)
and [rnpm](https://www.npmjs.com/package/rnpm).

If you haven’t installed rnpm yet, run `npm install rnpm --global`.
Then install `react-native-clipboard` via npm: `npm install react-native-clipboard --save`.
After the npm install is complete, use rnpm to link the library: `rnpm link react-native-clipboard`.

## <a name='gogogo'>Go go go!</a>

When you’ve completed the objectives, post a screenshot of your app in
the #progress channel, then move on to the next challenge.

## <a name='sub-challenge-F'>F - Adding QR-reading Functionality</a>

### Objectives

Most TOTP apps allow the user to add a code generator simply by scanning a QR code.
The goal for this challenge is to add that functionality to our app.

### Pointers

##### TOTP QR Codes

QR codes that are used for configuring new TOTP generators encode simple URLs
that take the form `otpauth://totp/accountName?secret=abcdefghijklmnop`.
They provide all the information needed to save a new code generator.

Below is some sample code that may be helpful in working with these URLs
after they’ve been read from a QR code:

```js
// These libs help w/ parsing the TOTP URL that is encoded in the QR image.
// Be sure to npm install both of these. You won't need to link them with rnpm.
import URL from 'url-parse'
import qs from 'qs'

// `qrData` is the raw URL string read from the QR code.
// For TOTP configs, it _should_ look something like 'otpauth://totp/accountName?secret=abcdefghijklmnop'
const url = new URL(qrData)

// Ensure that the QR data is a TOTP config before we do anything else.
if (url.protocol === 'otpauth:' && url.host === 'totp') {
  const name = decodeURIComponent(url.pathname).replace(/^\//, '')
  const secret = qs.parse(url.query.replace(/^\?/, '')).secret

  // Now that you have a name and a secret, you have all the config needed for new code generator.
  addCodeGenerator({ name, secret })
}
```
For testing, you can use the following sample QR code.
Encoded in this QR code is TOTP config with the name `AWS:majdi.toumi@gmail.com`
and the secret `JBSWY3DPEHPK3PXP`.

![](./assets/qrcode.png)

##### Camera Interaction

You’ll probably want to use a 3rd-party library to handle the camera interaction.
`react-native-camera` is a good one. It happens to include QR-scanning functionality right out of the box. :moneybag:

Install `react-native-camera` via npm:
`npm install react-native-camera@https://github.com/lwansbrough/react-native-camera.git --save`.

After the npm install is complete, use rnpm to link the library: `rnpm link react-native-camera`.

Camera interaction may be difficult to test within the simulator.
If you have an Apple iOS developer account, we recommend running the app on an actual device.
Directions for doing so can be found [here](https://facebook.github.io/react-native/docs/running-on-device-ios.html#content).

### Go go go!

When you’ve completed the objectives, post a screenshot of your app in the #progress
channel. Woo hoo, you’ve made it! Congrats!

## <a name='credits'>Credits</a>

Write & develop with :heart: by [**Majdi Toumi**](http://majditoumi.com) | [**Mhirba**](http://www.mhirba.com).
