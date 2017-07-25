# Interface Guidelines for COBI Extensions

The COBI DevKit is the world's first platform that offers everything you need to easily design & build interactive experiences for riding on a bike. While the COBI hardware and software takes care of all the hard work (i.e. securely mounting and powering the phone, remote control, acquiring sensor-, eBike- and riding data) developers can focus on bringing new experiences to life with a stream of riding data and a fullscreen canvas embedded in the COBI dashboard:

Introducing _COBI Extensions_.

![COBI](COBI-Extensions-Header.png)

## Understanding the Biking Context

COBI enables developers to design interactive extensions that are loved by users while keeping them safe on the road. This is breaking new territory for developers and UX designers – so it's all the more important to understand this challenging new context:

* Directly interacting with a phone on the road (e.g. by using the touchscreen) is dangerous and often illegal. A handlebar remote (COBI Thumb Controller or Bosch Remote) is therefore a mandatory part of the COBI system to safely interact with the cyclist. It is important to map each button of the handlebar remote intuitively and provide reassuring feedback upon interaction.
* Picture the cyclist with hands on the handlebars & eyes on the road while riding. The extension must not disturb the riders' focus on traffic and the road ahead. However, the extension may provide guidance through voice feedback or glanceable visual hints – any feedback beyond that must be queued for later.
* The cyclist may take short breaks e.g. at traffic lights. Since COBI detects these breaks automatically you can take advantage of them easily to adapt the user interface to accept touch input, allow on-screen keyboards and show more elaborate information that has been queued up during the ride.
* COBI supports both Bikes & E-Bikes, External Sensors (e.g. Cadence & Heart Rate), 4- and 6-Button Thumb Controllers. Make sure to support these configurations to maximize the audience and make the most of the experience of using your extension.
* Keep in mind that the phone is mounted on the handlebars and the viewing distance is larger compared to holding it in your hand.

## Guiding Principles

### Keep it bold: Adaptive & Glanceable Design

* Keep your screendesign glanceable – use bold colors, high contrasts and large typography.
* Resize screen elements dynamically when the bike starts moving and hide descriptive elements (like labels) to increase design clarity.
* Design your extension to be displayed on Android 4.4+ and iOS 9.0+ devices with screen sizes from 4" up to 6"

### Do not disturb: Non-Intrusive User Interface

* Do not require user feedback while riding at anytime. If important events occur, rely on voice feedback to inform and follow-up as soon as the bike stops moving.
* When designing a game consider pausing automatically when the bike starts moving.

### Safe & Powerful Interactions: Remote, Touch & Audio hand in hand

* Make the most relevant interactions accessible via Thumb Controller taps while riding.
* Bring in touch and more sophisticated interactions whenever the bike doesn't move.
* Take advantage of voice feedback to enable users to perform actions in your extension without looking at the screen.
* Depending on the bike different Thumb Controller buttons are available to your extension (indicated by Thumb Controller Type). _Select_, _Up_ and _Down_ are always available unless E-Bike drive control is explicitely allowed. _Left_, _Right_ are available on the 6-Button COBI Thumb Controller.

### Plan, Ride, Advise

COBI Extensions support planning & riding scenarios to keep interaction-heavy planning/configuration tasks separate from the clean, simplistic riding interface. We call the former scenario _Plan_ and the latter _Experience_.

Extensions are expected to support the following view states:

#### State 1: Experience (Landscape orientation, mandatory)

The main user interface for cyclists on the road. Optimized for use with thumb controller and touch – depending on whether the touch interface is enabled.

#### State 2: Plan (Portrait & Landscape orientation, optional if _Manual View_ available)

Touch-only interface available before and during the ride to tweak extension-specific settings. You may automatically forward to _Manual_ if no settings are needed for your extension.

#### State 3: Manual (Portrait & Landscape orientation, optional if _Plan_ available)

Touch-only interface to learn more about how to use your extension. You may automatically forward to _Plan_ if _Experience_ is self-explanatory.

#### Data Stream

Once loaded, COBI will start feeding riding data (location, speed, fitness data, thumb controller events, etc.) via COBI.js to your extension. On closing the extension, the data stream will stop and all scripts will be unloaded.

### Offline first

Recreational cycling often takes place in areas with no or weak cell signal. COBI is designed to gracefully handle offline scenarios at all times – so should your extension. Take advantage of Web Standards like [Application Cache Manifests](https://html.spec.whatwg.org/multipage/offline.html#manifests) to speed up loading times & enable offline use or [Local Storage](https://html.spec.whatwg.org/multipage/webstorage.html#the-localstorage-attribute) to store application state and user preferences.
