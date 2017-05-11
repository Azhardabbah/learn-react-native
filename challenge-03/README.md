# Learn React Native :: Workshop 03

[![](https://img.shields.io/badge/React%20Native-v0.44-blue.svg)](https://facebook.github.io/react-native/)

> :coffee: This workshop is about **simulator orientation**

## <a name='TOC'>Summary</a>

01. [Objective](#objective)
02. [Setup](#setup)
02. [Pointers](#pointers)
42. [Credits](#credits)

## <a name='objective'>Objective</a>

The goal with this challenge is to gain familiarity with React Native’s style
and layout capabilities. To do this, you’ll try to build the following screen:

[XXX](./assets/screen-app.png)

## <a name='setup'>Setup</a>

Before you begin, replace the contents of your project’s `index.ios.js` file
with the following:

```js
'use strict';
import React, {
  AppRegistry,
  Component,
  Image,
  StyleSheet,
  Text,
  View
} from 'react-native';

class FirstApp extends Component {
  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.welcome}>
          Next challenge!
        </Text>
        <Text style={styles.instructions}>
          Try to build a replica of the screen{'\n'}
          shown in the challenge directions.
        </Text>
        <Text style={styles.instructions}>
          (The one below.)
        </Text>
        <Image
          style={styles.targetImage}
          source={{ uri: 'assets/mind-blown.gif' }}
        />
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#eee',
  },
  welcome: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  },
  instructions: {
    marginTop: 10,
    textAlign: 'center',
  },
  targetImage: {
    width: 150,
    height: 300,
    marginTop: 25,
  }
});

AppRegistry.registerComponent('FirstApp', () => FirstApp);
```

## <a name='pointers'>Pointers</a>

### Intro to Pseudo-CSS

React Native does not implement CSS, however it uses JavaScript-based tooling
this is inspired by and feels very much like CSS in certain ways.

##### Styles are represented as JSON.

```css
.page {
  background-color: orange;
  height: 42px;
  border: 1px solid blue;
}
```

...would be...

```css
{
  page: {
    backgroundColor: 'orange',
    height: 42,
    borderColor: 'blue',
    borderWidth: 1
  }
}
```

Styles don’t cascade.

```html
<View style={{ color: 'orange' }} >
  <Text>I'm not orange.</Text>
</View>
```

But you can build up styles compositionally:

```html
<View>
  <Text style={ [styles.defaultText, styles.orange, styles.centered] }>
		I'm orange and centered.
	</Text>
</View>

// ...

const styles = StyleSheet.create({
  defaultText: {
    fontSize: 12,
  },
  orange: {
    color: 'orange',
  },
  centered: {
    textAlign: 'center',
  },
})
```

##### Layout is flexbox-based.

You won’t find any `float` in React Native styles. Flexbox is a more powerful
and elegant alternative, but can have a bit of a learning curve.

If you’re new to Flexbox layouts, the [CSS-Tricks Flexbox Guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) is a teriffic resource.

## <a name='useful-documentation'>Useful Documentation</a>

- Overall Style Docs
- View Properties
- Image Properties
- Text Properties
- Flex Properties
- Transform Properties

## <a name='gogogo'>Go go go</a>

Learning time is over. It’s time to build. How close can you get to the screen below?

[XXX](./assets/screen-app.png)

You can find the same image included on the above screen in the assets directory.

And remember that `<View>` is analogous to HTML’s `<div>`, `<Text>` is analogous to `<p>`, and `<Image>` is analogous to `<img>`.

Post a screenshot of your app in the `#progress` channel, then move on to the next challenge.

> If this style challenge felt too easy for you, spend some more time going crazy, pushing the limits of React Native styling. Then post a screenshot of your crazy.

## <a name='extras'>Extras</a>

[XXX](./assets/screen-topbar.png)

f you’re annoyed by this black status bar text on the dark grey background, check out the [StatusBarIOS API](https://facebook.github.io/react-native/docs/statusbarios.html#content) docs and change it to a lighter color.

## <a name='next'>Next</a>

Well, you have just finished this challenge... easy right? :wink:<br />
Post a screenshot of your app in the `#progress` channel, then move on to the [challenge #04](https://github.com/majdi/learn-react-native/tree/master/challenge-04).

## <a name='credits'>Credits</a>

Write & develop with :heart: by [**Majdi Toumi**](http://majditoumi.com) | [**Mhirba**](http://www.mhirba.com).
