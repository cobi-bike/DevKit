
- I am using the `subscribe` method for `X` but I dont get any data?
This usually happens if you forget to authenticate your webapp. To do so call
`COBI.init("YOUR-API-CODE-HERE")`.

- My app works on the Simulator but not on the device :( ?
Instead of trying to brute force your app it would be better to diagnose the
problem first. To do that connect your device to the `Safari Web Inspector Guide`
following the instructions [here](https://developer.apple.com/library/content/documentation/AppleApplications/Conceptual/Safari_Developer_Guide/GettingStarted/GettingStarted.html#//apple_ref/doc/uid/TP40007874-CH2-SW8). This will allow you to
see `console` information and stacktraces directly on your desktop.

- How do I get a specific version of the COBI.js library?
The following url gives you version `0.1.0` of the COBI.js library: *https://cdn.cobi.bike/cobi.js/0.1.0/cobi.js*. This will work for any other published version of the library.
