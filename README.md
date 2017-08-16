# COBI DevKit

A collection of Open Source components to develop modules for [COBI](cobi.bike) – the perfect fusion of smartphone and bike.

## Quickstart with just a few clicks

The quickest way to get started:
1. Launch [Chrome](https://chrome.com) and install the [COBI DevKit Chrome Extension](https://chrome.google.com/webstore/detail/cobi-devkit-simulator/hpdhkapigojggienmiejhblkhenjdbno)
2. Open our [example module](https://codepen.io) on [codepen.io](https://codepen.io)
3. Open the [COBI DevKit Chrome Extension](https://chrome.google.com/webstore/detail/cobi-devkit-simulator/hpdhkapigojggienmiejhblkhenjdbno) alongside the [example module](https://codepen.io) in your Chrome browser window
4. Change location or destination coordinates and hit the thumb controller buttons to see COBI.js in action

Bonus points for directly tweaking the code e.g. subscribing to additional data from the COBI.js data stream or adding fancy visualizations.

## Getting started with a new project

It only takes a few lines of javascript to turn webapps into a COBI module:

### Step 1: Add boilerplate code to your web project

To get your COBI module ready just add `COBI.js` at the end of the body section of your HTML:
```html
<script src="https://cdn.cobi.bike/cobi.js/0.34.0/cobi.js"></script>
```
... and provide an authentication token back to COBI before subscribing to the data stream. COBI doesn't issue tokens yet, so you can use any token for now: 
```javascript

// Authenticate your module
COBI.init('my-token')
```

It's that easy: Any Webapp + COBI.js = COBI module!

### Step 2: Hook into the COBI.js data stream

Enough with the boilerplate code, let's make our new COBI module responsive to the handlebar remote control:

```javascript
COBI.hub.externalInterfaceAction.subscribe(function(action) {
  alert("Holy moly, I just tapped the handlebar remote and instantly received this " + action + " in my webapp");
});
```

... or visualize the Cadence acquired by COBI from an external Bluetooth sensor or eBike motor:

```javascript
COBI.rideService.cadence.subscribe(function(cadence) {
    $('#cadence').html(`Your current cadence is ${cadence} rpm.`);
});
```

### Step 3: Testing

COBI modules can be previewed in the brower, but to 

To see your COBI module in action you have two options:
* Install our [COBI DevKit Chrome Extension](https://chrome.google.com/webstore/detail/cobi-devkit-simulator/hpdhkapigojggienmiejhblkhenjdbno) and test in the browser. To simulate riding & fitness data you can play back one of our sample cobitrack files.
* Enter the URL to your COBI module in our iOS app and take a testride on your bike. Requires registration as a developer on [my.cobi.bike](https://my.cobi.bike) and a [COBI system](https://get.cobi.bike) (Developer Editions can be ordered from [my.cobi.bike](https://my.cobi.bike)).

## Everything I need to know about the COBI DevKit

### Inspiration & Examples 

* Get inspired on the [COBI DevKit site](https://cobi.bike/devkit)
* Take a testride with one of our example modules in the iOS app. Requires registration as a developer on [my.cobi.bike](https://my.cobi.bike)
* You can find more code templates in the [examples](examples) directory 
* Make sure to visit our [Showtime Developer Forum](https://forums.cobi.bike/c/showtime) for additional inspiration from other developers

### COBI Interface Guidelines

Read our [Interface Guidelines](interface-guidelines.md) to understand the unique challenges of developing software for bikes and to learn more about how the COBI system and modules work.

### More DevKit Resources

- [FAQ](FAQ.md)
- [Developer Forums](https://forums.cobi.bike)
- [COBI.js docs](https://cobi-bike.github.io/COBI.js/)
- [COBI DevKit Chrome Extension](https://github.com/cobi-bike/COBI.js-simulator)
- [COBI.js architecture](COBI.js-architecture.png)

### Other Tools & Resources

- [glitch](https://glitch.com/) – friendly community where you'll build the app of your dreams
- [codepen](https://codepen.io/) – social development environment for front-end designers and developers

## Contributing to this Project

Anyone and everyone is welcome to contribute. Please take a moment to
review the [guidelines for contributing](CONTRIBUTING.md).

* [Bug reports](CONTRIBUTING.md#bugs)
* [Feature requests](CONTRIBUTING.md#features)
* [Pull requests](CONTRIBUTING.md#pull-requests)

Copyright © 2017 COBI GmbH
