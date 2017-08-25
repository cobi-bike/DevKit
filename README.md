# COBI DevKit

A collection of Open Source components to develop [modules](https://cobi.bike/devkit) for [COBI](https://cobi.bike) – the perfect fusion of smartphone and bike.

![COBI DevKit](COBI-DevKit.png)

## 💡 Interactive Demo: Learn the fundamentals

Here's the quickest way to learn the COBI DevKit basics without writing any code:

1. Install the [COBI DevKit Chrome Extension](https://chrome.google.com/webstore/detail/cobi-devkit-simulator/hpdhkapigojggienmiejhblkhenjdbno)
2. Navigate to our [interactive demo](https://codepen.io/cobi-bike/pen/VzBOqp?editors=0010) on codepen.io
3. Open the COBI DevKit Extension alongside the example in your Chrome browser window
4. Change location coordinates and hit thumb controller buttons to see COBI.js in action. This simulates data and interaction events that will later be provided by the COBI system when riding a bike.

Bonus points for directly tweaking the code e.g. subscribing to additional data from the COBI.js data stream.

## 🚀 Let's get started with your first project

It only takes a few lines of javascript to turn Web Apps into a COBI module:

### Step 1: Add boilerplate code

To get your Web App ready just add `cobi.js` at the end of the body section of your HTML:
```html
<script src="https://cdn.cobi.bike/cobi.js/0.34.1/cobi.js"></script>
```

and pass an authentication token to COBI before subscribing to the data stream. 
COBI doesn't issue tokens yet, so you can use any string for now: 
```javascript

// Authenticate your module
COBI.init('my-token')
```

It's that easy: Any Web App + COBI.js = __COBI Module__!

### Step 2: Hook into the data stream

Enough with the boilerplate code, let's make our new COBI module respond to the handlebar remote control:

```javascript
COBI.hub.externalInterfaceAction.subscribe(function(action) {
  alert('Holy moly, I just tapped the handlebar remote and instantly received this ' + action + ' in my Web App');
});
```

or visualize the Cadence acquired by COBI from an external Bluetooth sensor or eBike motor:

```javascript
COBI.rideService.cadence.subscribe(function(cadence) {
    console.log('Your current cadence is ' + cadence + ' rpm.');
});
```

There is a ton of data available such as current speed, course, heart-rate (if heart-rate monitor is connected), power, calories burned and much more. Our [COBI.js reference](https://cobi-bike.github.io/COBI.js/) will be your friend.

### Step 3: Testing

Now that you have supercharged your Web App, you can test your module either in the Chrome browser on your machine or directly in the COBI iOS App on your bike.

#### Browser testing

Just install the [COBI DevKit Chrome Extension](https://chrome.google.com/webstore/detail/cobi-devkit-simulator/hpdhkapigojggienmiejhblkhenjdbno), open up the Developer Tools (⌘ + Option + i / Ctrl + Shift + j) and select the »COBI« tab.  
To get the best experience, switch on the phone mode in the upper left corner and rotate the device to landscape.
To simulate riding and fitness data you can play back one of our [sample cobitrack or GPX files](https://github.com/cobi-bike/DevKit-Simulator/tree/master/tracks).

#### On-bike testing 

You need to be a registered COBI developer to test modules on your bike. Go to [my.cobi.bike](https://dev-my.cobi.bike/developer) to get started. If you don't own a COBI yet, get one with a special developer discount at [get.cobi.bike/developer](https://get.cobi.bike/developer/).

Ready? Then open up the COBI App on your iPhone and open the edit modules screen. As COBI developer you can now choose from a number of examples modules or add you own via »My Module«

When you open »My Module« on the home screen or the dashboard, you can enter the URL of your module (it can be hosted wherever you want, but we have some suggestions below). When you press »Open module« your module is loaded and hooked up to the COBI App. Now you can easily test your idea on your 🚲.

<img src="resources/Modules.jpeg" width="280px" alt="COBI iOS App Home"> <img src="resources/EditModules.jpeg" width="280px" alt="COBI iOS App Edit Modules"> <img src="resources/MyModule.jpeg" width="280px" alt="COBI iOS App My Module">

## 🏓 Play ping-pong with the COBI App

Take advantage of interfaces to the native COBI app to save yourself a lot of work.

#### Start a turn-by-turn navigation to a destination:
```javascript
COBI.navigationService.control.write({
  'action': 'START', 
  'destination': {'latitude': 50.110924,'longitude': 8.682127}
})
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

## 🎛 Settings for your Module

A module can be shown in different states. There are three pieces of information that you should adapt to:

1. The device orientation — your module should automatically adapt to the available screen size
1. The value of `COBI.parameters.state()` — can be either `COBI.state.edit` or `COBI.state.experience`
1. The state of `COBI.app.touchInteractionEnabled` — changes when you start/stop riding  

### Flexible layout

Take a look at our [COBI Modules UI Components](https://github.com/cobi-bike/Modules-UI) for an easy way to create a UI for your settings.

### Module state

Right now, there are two states you should support. You can check `COBI.parameters.state()` at any time to decide if some sort of settings should be shown (`COBI.state.edit`) or if the actual module is requested (`COBI.state.experience`). To share information between the two states and in between user sessions use the web standard [Local Storage](https://html.spec.whatwg.org/multipage/webstorage.html#the-localstorage-attribute).

### Touch Interaction Changes

While riding, the user is encouraged to use the thumb controller instead of interacting with the UI via touch. Subscribe to changes of this state to make the best out of both situations. Please note that a bar is shown at the top while `touchInteractionEnabled` is `false` — make sure it is not overlapping with your UI.

```javascript
COBI.app.touchInteractionEnabled.subscribe(function(enabled) {
    // Adapt your UI
});
```

![Module States](resources/ModuleStates.jpg)

## 🌈 Everything else about the COBI DevKit

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

## 👏 Contributing to this project

Anyone and everyone is welcome to contribute. Please take a moment to review the [guidelines for contributing](CONTRIBUTING.md).

* [Bug reports](CONTRIBUTING.md#bugs)
* [Feature requests](CONTRIBUTING.md#features)
* [Pull requests](CONTRIBUTING.md#pull-requests)

Copyright © 2017 COBI GmbH
