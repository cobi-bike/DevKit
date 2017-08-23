# COBI DevKit

A collection of Open Source components to develop [modules](https://cobi.bike/devkit) for [COBI](https://cobi.bike) – the perfect fusion of smartphone and bike.

## Interactive Demo: Learn the basics

Here's the quickest way to learn the COBI DevKit principle without writing any code:

1. Launch [Google Chrome](https://chrome.com) and install the [COBI DevKit Chrome Extension](https://chrome.google.com/webstore/detail/cobi-devkit-simulator/hpdhkapigojggienmiejhblkhenjdbno)
2. Navigate to our [example module](https://codepen.io) on [codepen.io](https://codepen.io)
3. Open the [COBI DevKit Chrome Extension](https://chrome.google.com/webstore/detail/cobi-devkit-simulator/hpdhkapigojggienmiejhblkhenjdbno) alongside the example in your Chrome browser window
4. In the DevKit Extension, change location coordinates and hit thumb controller buttons to see COBI.js in action. This simulates data that will later be provided by COBI to your module when riding on a bike.

Bonus points for directly tweaking the code e.g. subscribing to additional data from the COBI.js data stream or adding fancy visualizations!

## Let's get started with your first project

It only takes a few lines of javascript to turn web apps into a COBI module:

### Step 1: Add boilerplate code to your web project

To get your web app ready just add `COBI.js` at the end of the body section of your HTML:
```html
<script src="https://cdn.cobi.bike/cobi.js/0.34.0/cobi.js"></script>
```
... and provide an authentication token back to COBI before subscribing to the data stream. COBI doesn't issue tokens yet, so you can use any token for now: 
```javascript

// Authenticate your module
COBI.init('my-token')
```

It's that easy: Any web app + COBI.js = COBI module!

### Step 2: Hook into the COBI.js data stream

Enough with the boilerplate code, let's make our new COBI module respond to the handlebar remote control:

```javascript
COBI.hub.externalInterfaceAction.subscribe(function(action) {
  alert('Holy moly, I just tapped the handlebar remote and instantly received this ' + action + ' in my web app');
});
```

... or visualize the Cadence acquired by COBI from an external Bluetooth sensor or eBike motor:

```javascript
COBI.rideService.cadence.subscribe(function(cadence) {
    console.log('Your current cadence is ' + cadence + '} rpm.');
});
```

There is a ton of more data available like current speed, course, heart-rate (if heart-rate monitor is connected), power, calories burned and much more. Our [COBI.js reference](https://cobi-bike.github.io/COBI.js/) will be your friend.

### Step 3: Testing

COBI modules (a fancy name for web apps with COBI.js) can be viewed by modern web browsers. However, in order to receive data via COBI.js we need an input data source – currently there are two options:
1. Test in the browser: Install our [COBI DevKit Chrome Extension](https://chrome.google.com/webstore/detail/cobi-devkit-simulator/hpdhkapigojggienmiejhblkhenjdbno) and test in the browser with simulated data sources. To simulate riding & fitness data you can play back one of our sample cobitrack or GPX files.
2. Test on the bike/eBike: Enter the URL to your COBI module in our iOS app and take a testride on your bike. Requires registration as a developer on [my.cobi.bike](https://my.cobi.bike) and a [COBI system](https://get.cobi.bike) on your bike (Developer Editions can be ordered from [my.cobi.bike](https://my.cobi.bike)).

## Play Ping-Pong with the COBI App

Take advantage of interfaces to the native COBI app to safe yourself a lot of work.

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

## Everything else to know about the COBI DevKit

### Inspiration & Examples 

* Get inspired on the [COBI DevKit site](https://cobi.bike/devkit)
* Take a testride with one of our example modules in the iOS app. Requires registration as a developer on [my.cobi.bike](https://my.cobi.bike)
* Find more code templates in the [examples](examples) directory 
* Visit our [Showtime Developer Forum](https://forums.cobi.bike/c/showtime) for additional inspiration from other developers

### COBI Interface Guidelines

Read our [Interface Guidelines](interface-guidelines.md) to understand the unique challenges of developing software for bikes and to learn more about how the COBI system and modules work.

### More DevKit Resources

- [FAQ](FAQ.md)
- [Developer Forums](https://forums.cobi.bike)
- [COBI DevKit Chrome Extension](https://github.com/cobi-bike/COBI.js-simulator)
- [COBI.js reference](https://cobi-bike.github.io/COBI.js/)
- [COBI.js architecture](COBI.js-architecture.png)

### Other Tools & Resources

- [glitch](https://glitch.com/) – friendly community where you'll build the app of your dreams
- [codepen](https://codepen.io/) – social development environment for front-end designers and developers

## Contributing to this Project

Anyone and everyone is welcome to contribute. Please take a moment to review the [guidelines for contributing](CONTRIBUTING.md).

* [Bug reports](CONTRIBUTING.md#bugs)
* [Feature requests](CONTRIBUTING.md#features)
* [Pull requests](CONTRIBUTING.md#pull-requests)

Copyright © 2017 COBI GmbH
