## Getting Started FAQ

### What do I need to get started with the DevKit?

#### 1. To develop & test your module in the browser:

* Baseline skills in modern web development
* [DevKit Simulator](https://github.com/cobi-bike/DevKit-Simulator)

You can turn any of your existing web apps into a module with a few extra lines of javascript.

#### 2. To test your Module on a bike or eBike:

* Online hosting for your module
* iOS Device (minimum iPhone 5 with iOS 10.0)
* [COBI.bike system](https://get.cobi.bike)
* Registration as a developer on [my.cobi.bike](https://my.cobi.bike)

### Do I need to purchase a COBI.Bike system to start building a module?

No, you can get started for free with the [DevKit Simulator](https://github.com/cobi-bike/DevKit-Simulator) and test on a COBI.Bike system when you're ready. If you don't have one yet, you can purchase a developer edition on [cobi.bike/devkit](https://cobi.bike/devkit) or any other COBI.Bike system in our [online store](https://get.cobi.bike).

### How can I turn my website / webapp into a module?

Include `COBI.js` in your html and start subscribing to riding data and remote control events.

### Can you recommend any additional development tools / platforms to build modules?

We like getting inspired on [codepen.io](https://codepen.io) and building prototypes on [glitch.me](https://glitch.me). Both work great with the [DevKit Simulator](https://github.com/cobi-bike/DevKit-Simulator).

## Technical FAQ

### I don't know how to test my module within the COBI.Bike app

Did you already sign up as a developer on [my.cobi.bike](https://my.cobi.bike)? If yes, please follow the instructions on the [DevKit site](https://github.com/cobi-bike/COBI-DevKit).

### Sometimes the settings of my module are reset

If your iOS device is low on storage, the Safari browser cache may get deleted. This is a known issue for now.

### I'm using the `subscribe` method, but I don't receive any data

Make sure to authenticate your module first – to do so call
`COBI.init("YOUR-TOKEN")` before you subscribe to any `COBI.js` data stream.

### I changed the code of the module but the changes are not appearing on the COBI.Bike app

We have noticed that sometimes there are some browser-related caching issues so this is what might be happening to you. The easiest solution would be to go into the module selection screen, remove *My Module* and add it again.

### Any tips for debugging my module within the COBI.Bike app on the phone?

The native app will display javascript errors in a dialog. Just activate this feature in the diagnostics settings of the app.

### How do I get a specific version of the `COBI.js` library?

The following url provides `0.42.0` of `COBI.js`: *https://cdn.cobi.bike/cobi.js/0.42.0/cobi.js*.
This will work for any other published version.

### Are there any other known technical limitations?

There are not many technical constraints to module development; any modern framework can be used (Angular, React, Vue) as well as any mobile-compatible library.

There are however some limitations that need to be taken into account:

* The webapp should not rely on server side rendering.
* Currently, the user needs to be online to render the module: COBI.js does not support an offline mode.

## Distribution / Business Model FAQ

### How can I share my module with others?

For now, you can share your work (screenshots, url) with other developers in the [COBI.bike developer showtime forum](https://forums.cobi.bike/c/showtime).

### When and how can I make my module available to COBI.Bike users later?
Currently it is not possible to publish your modules to other users, though we are working on this. In the meantime, the DevKit enables you to figure out if your idea has legs and what features work best in a biking context. Make sure you comply with the [interface guidelines](interface-guidelines.md) and share your results with the developer community [forums.cobi.bike](https://forums.cobi.bike). We'll announce distribution mechanisms to end-users later.

### Will I be able to charge money for my module?

Currently there are no monetization plans via the COBI.Bike platform. If you’re offering a commercial service we recommend to view modules as a bike-friendly "springboard" to offer limited, specific functionality suitable for the context of biking. For more advanced functionalities, you can link to your own native app or website. Feel free to use a login to authenticate users for paid functionalities, but make sure to follow the requirements of respective mobile ecosystem policies.

### Any plans to support in-house distribution for enterprises?

Yes, please [get in touch](https://cobi.bike/connect).
