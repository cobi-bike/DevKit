## Getting Started FAQ

### What do I need to get started with the DevKit?

#### 1. To develop & test your COBI Module in the browser:

* Baseline skills in modern web development
* [COBI DevKit Simulator](https://github.com/cobi-bike/COBI.js-simulator)

You can turn any of your existing Web Apps into a COBI module with a few extra lines of javascript.

#### 2. To test your COBI Module on a bike or eBike:

* Online hosting for your Module
* iOS Device (minimum iPhone 5 with iOS 9.0)
* [COBI System](https://get.cobi.bike)
* Registration as a COBI Developer on [my.cobi.bike](https://my.cobi.bike)

### Do I need to purchase a COBI system to start building a module?

No, you can get started for free with the [COBI DevKit Simulator](https://github.com/cobi-bike/COBI.js-simulator) and test on a COBI system when you're ready. If you don't have a COBI yet, you can purchase a Developer Edition on [cobi.bike/devkit](https://cobi.bike/devkit) or any other COBI System in our [online store](https://get.cobi.bike).

### How can I turn my website / webapp into a COBI module?

Include COBI.js in your html and start subscribing to riding data and remote control events.

### Can you recommend any additional development tools / platforms to build COBI modules?

We like getting inspired on [codepen.io](https://codepen.io) and building prototypes on [glitch.me](https://glitch.me). Both work great with the [COBI DevKit Simulator](https://github.com/cobi-bike/COBI.js-simulator).

## Technical FAQ

### I don't know how to test my module within the COBI app

Did you already sign up as a COBI Developer on [my.cobi.bike](https://my.cobi.bike)? If yes, please follow the instructions on the [DevKit site](https://github.com/cobi-bike/COBI-DevKit).

### I'm using the `subscribe` method, but I don't receive any data

Make sure to authenticate your module first – to do so call
`COBI.init("YOUR-TOKEN")` before you subscribe to any COBI.js data stream.

### Any tips for debugging my module within the COBI app on the phone?

The native app will display javascript errors in a dialog.

### How do I get a specific version of the COBI.js library?

The following url provides `0.34.0` of COBI.js: *https://cdn.cobi.bike/cobi.js/0.34.0/cobi.js*. 
This will work for any other published version.

## Distribution / Business Model FAQ

### How can I share my module with others?

For now, you can share your work (screenshots, url) with other COBI developers in the [COBI Developer Showtime forum](https://forums.cobi.bike/c/showtime).

### When and how can I make my module available to COBI users later?
We are in the process of defining distribution mechanisms which are planned to ship in 2018. In the meantime, COBI DevKit enables you to figure out if your idea has legs and what features work best in a biking context. Make sure you comply with the [COBI Interface Guidelines](interface-guidelines.md) and share your results with the developer community [forums.cobi.bike](https://forums.cobi.bike). We'll announce distribution mechanisms to end-users later.

### Will I be able to charge money for my COBI Module?

Currently there are no monetization plans via the COBI platform. If you’re offering a commercial service we recommend to view COBI Modules as a bike-friendly "springboard" to offer limited, specific functionality suitable for the context of biking. For more advanced functionalities, you can link to your own native app or website. Feel free to use a login to authenticate users for paid functionalities, but make sure to follow the requirements of respective mobile ecosystem policies.

### Any plans to support in-house distribution for enterprises?

Yes, please [get in touch](https://cobi.bike/connect).
