# COBI DevKit

A collection of Open Source components to develop [modules](https://cobi.bike/devkit) for [COBI](https://cobi.bike) – the perfect fusion of smartphone and bike.

![COBI DevKit](COBI-DevKit.png)

## Interactive Demo: Learn the fundamentals 💡

Here's the quickest way to learn the COBI DevKit basics without writing any code:

1. Install the [COBI DevKit Chrome Extension](https://chrome.google.com/webstore/detail/cobi-devkit-simulator/hpdhkapigojggienmiejhblkhenjdbno)
2. Navigate to our [interactive demo](https://codepen.io/cobi-bike/pen/VzBOqp?editors=0010) on codepen.io
3. Open the COBI DevKit Extension alongside the example in your Chrome browser window
4. Change location coordinates and hit thumb controller buttons to see COBI.js in action. This simulates data and interaction events that will later be provided by the COBI system when riding a bike.

Bonus points for directly tweaking the code e.g. subscribing to additional data from the COBI.js data stream.

## Let's get started with your first project 🚀

It only takes a few lines of javascript to turn Web Apps into a COBI module:

### Step 1: Add boilerplate code to your web project

To get your Web App ready just add `COBI.js` at the end of the body section of your HTML:
```html
<script src="https://cdn.cobi.bike/cobi.js/0.34.0/cobi.js"></script>
```
... and provide an authentication token back to COBI before subscribing to the data stream. COBI doesn't issue tokens yet, so you can use any token for now:
```javascript

// Authenticate your module
COBI.init('my-token')
```

It's that easy: Any Web App + COBI.js = __COBI Module__!

### Step 2: Hook into the COBI.js data stream

Enough with the boilerplate code, let's make our new COBI module respond to the handlebar remote control:

```javascript
COBI.hub.externalInterfaceAction.subscribe(function(action) {
  alert('Holy moly, I just tapped the handlebar remote and instantly received this ' + action + ' in my Web App');
});
```

... or visualize the Cadence acquired by COBI from an external Bluetooth sensor or eBike motor:

```javascript
COBI.rideService.cadence.subscribe(function(cadence) {
    console.log('Your current cadence is ' + cadence + ' rpm.');
});
```

There is a ton of data available such as current speed, course, heart-rate (if heart-rate monitor is connected), power, calories burned and much more. Our [COBI.js reference](https://cobi-bike.github.io/COBI.js/) will be your friend.

### Step 3: Testing

COBI Modules (as you know: a fancy name for Web Apps with COBI.js) can be viewed by modern web browsers. However, in order to receive data via COBI.js we need an input data source – currently there are two options:
1. Test in the browser: Install our [COBI DevKit Chrome Extension](https://chrome.google.com/webstore/detail/cobi-devkit-simulator/hpdhkapigojggienmiejhblkhenjdbno) and test in the browser with simulated data sources. To simulate riding & fitness data you can play back one of our sample cobitrack or GPX [files](https://github.com/cobi-bike/DevKit-Simulator/tree/master/tracks).
2. Test on the bike/eBike: Enter the URL to your COBI module in our iOS app and take a testride on your bike. Requires registration as a developer on [my.cobi.bike](https://my.cobi.bike) and a [COBI system](https://get.cobi.bike) on your bike (Developer Editions can be ordered from [my.cobi.bike](https://my.cobi.bike)).

## Play ping-pong with the COBI App 🏓

Take advantage of interfaces to the native COBI app to save yourself a lot of work.

#### Start a turn-by-turn navigation to a destination:
```javascript
COBI.navigationService.control.write({'action': 'START', 'destination': {'latitude': 50.110924,'longitude': 8.682127}})
```
#### Open a phone number picker with the list of contacts:
```javascript
COBI.app.contact.read()
```
#### Hook into the voice feedback system:
```javascript
COBI.app.textToSpeech.write({'content' : 'Can you hear my voice?', 'language' : 'en-US'})
```
#### Claim the entire screen space by hiding the clock in the top right corner:
```javascript
COBI.app.clockVisible.write(false);
```
#### Claim all Thumb Controller buttons on eBikes that are reserved for motor control by default:
```javascript
COBI.devkit.overrideThumbControllerMapping.write(true);
```

Check out the [COBI.js reference](https://cobi-bike.github.io/COBI.js/) for more.

## Settings for your Module 🎛

[Explain states]

Hint: Take a look at our [COBI Modules UI Components](https://github.com/cobi-bike/Modules-UI) for an easy way to create a UI for your settings.

## Everything else about the COBI DevKit 🌈

### Inspiration & Examples

* Get inspired by our showcases on the [COBI DevKit site](https://cobi.bike/devkit)
* Take a testride with one of our example modules in the COBI iOS app. Requires registration as a developer on [my.cobi.bike](https://my.cobi.bike)
* Visit our [Showtime Developer Forum](https://forums.cobi.bike/c/showtime) for additional inspiration from the developer community

### Interface Guidelines

Read our [Interface Guidelines](interface-guidelines.md) to understand the unique challenges of developing software for bikes and to learn more about how the COBI system and modules work.

### More DevKit Resources

- [FAQ](FAQ.md)
- [Developer Forums](https://forums.cobi.bike)
- [COBI DevKit Chrome Extension on Chrome Web Store](https://chrome.google.com/webstore/detail/cobi-devkit-simulator/hpdhkapigojggienmiejhblkhenjdbno)
- [COBI DevKit Chrome Extension on Github](https://github.com/cobi-bike/COBI.js-simulator)
- [COBI Modules UI Components](https://github.com/cobi-bike/Modules-UI)
- [COBI.js reference](https://cobi-bike.github.io/COBI.js/)
- [COBI.js architecture](COBI.js-architecture.png)

### Other Tools & Resources

- [Glitch](https://glitch.com/) – friendly community where you'll build the app of your dreams
- [CodePen](https://codepen.io/) – social development environment for front-end designers and developers

## Contributing to this project

Anyone and everyone is welcome to contribute. Please take a moment to review the [guidelines for contributing](CONTRIBUTING.md).

* [Bug reports](CONTRIBUTING.md#bugs)
* [Feature requests](CONTRIBUTING.md#features)
* [Pull requests](CONTRIBUTING.md#pull-requests)

Copyright © 2017 COBI GmbH
