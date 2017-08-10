# COBI DevKit

A Javascript library for developing modules for [COBI](cobi.bike) – the perfect fusion of smartphone and bike.

## Getting Started

To start developing modules you need to add the `COBI.js` library at the end of the body section of your HTML as shown below
```html
<script src="https://cdn.cobi.bike/cobi.js/latest/cobi.js"></script>
```
... and provide an authentication token back to the COBI app before subscribing to the data stream. See [details](https://cobi-bike.github.io/COBI.js/#COBI.init).

To test your COBI module you have two options:
* Install our [COBI.js Simulator](https://github.com/cobi-bike/COBI.js-simulator) Chrome Extension and test in the browser
* Load your module within the COBI app and take a testride on your bike (requires registration as a developer at [my.cobi.bike](https://my.cobi.bike)).

## Usage

```javascript

// authenticate your module
COBI.init('YOUR API KEY')

// Subscribe to 'location' event to receive updates on the current location
COBI.mobile.location.subscribe(function(location) {
    $('#location').html(`<p> New location , lat: ${location.latitude}, lon: ${location.longitude} </p>`);

});

// Subscribe to 'thumb Controller' event to receive pressed keys from the COBI Thumb Controller
COBI.hub.externalInterfaceAction.subscribe(function(action) {
    $('#thumbcontroller').html(`<p> New action: ${action} </p>`);
});

// Alternative you can provide a callback to the read/write functions to receive only the next incoming event, not every update
COBI.intelligenceService.heartRate.read(function(heartrate) {
    $('#heartrate').html(`<p> Current heartrate is ${heartrate} </p>`);
});
```

You can find some example modules in the [examples](examples) directory.

An overview of the COBI.js architecture can be found [here](COBI.js-architecture.png)

## Interface Guidelines

Check out our [Interface Guidelines](interface-guidelines.md) to understand more about the COBI system and how modules work and interact with the COBI app.

## More information

- [FAQ](FAQ.md)
- [forums](https://forums.cobi.bike)
- [COBI.js docs](https://cobi-bike.github.io/COBI.js/)
- [COBI.js Simulator](https://github.com/cobi-bike/COBI.js-simulator)

### useful tools

- [glitch](https://glitch.com/) is the friendly community where you'll build the app of your dreams
- [codepen](https://codepen.io/) is a social development environment for front-end designers and developers


## Contributing to this project

Anyone and everyone is welcome to contribute. Please take a moment to
review the [guidelines for contributing](CONTRIBUTING.md).

* [Bug reports](CONTRIBUTING.md#bugs)
* [Feature requests](CONTRIBUTING.md#features)
* [Pull requests](CONTRIBUTING.md#pull-requests)

Copyright © 2017 COBI GmbH
