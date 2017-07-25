# COBI DevKit

A Javascript library for developing WebApps for [COBI](cobi.bike), the first smart connected biking system.

## Getting Started

To start developing webapps you would need to add the `COBI.js` library at the end of the body section of your HTML as shown below
```html
<script src="https://cdn.cobi.bike/cobi.js/latest/cobi.js"></script>
```

To start developing webapps for COBI you need:
1. To register as a developer in [my.cobi.bike](https://my.cobi.bike).

2. To provide an Authentication token back to the native app at the beginning of your app. See [details](https://cobi-bike.github.io/COBI.js/#COBI.init).

## Usage

```javascript

// authenticate your app
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

You can find some examples apps in the [examples](examples) directory.

## Interface Guidelines

Check out our [Interface Guidelines](interface-guidelines.md) to understand more about the COBI system and how WebApps work and interact with the COBI app.

## More information

- [FAQ](FAQ.md)
- [forums](forums.cobi.bike)
- [COBI.js docs](https://cobi-bike.github.io/COBI.js/)

## Contributing to this project

Anyone and everyone is welcome to contribute. Please take a moment to
review the [guidelines for contributing](CONTRIBUTING.md).

* [Bug reports](CONTRIBUTING.md#bugs)
* [Feature requests](CONTRIBUTING.md#features)
* [Pull requests](CONTRIBUTING.md#pull-requests)

Copyright © 2017 COBI GmbH
