# MVP-Architecture-for-Firmware
This is my public brainstorming repo for an idea of MVP architecture for Firmware.

I've been struggling over the past couple years trying to find a nice, clean, modular architecture for firmware and so far I haven't found anything I've liked. After playing around with writing a mobile app in Flutter, I discovered the MVP architectural model (Model View Presenter) which is diagrammed in the chart below:

![MVP Architectural Model](https://i.stack.imgur.com/b49Dj.png)

borrowed from: [StackOverflow](https://softwareengineering.stackexchange.com/questions/379002/help-with-understanding-implementing-mvp-architecture-in-android)

I've really enjoyed this pattern for mobile, so I'm going to attempt to map it to firmware in this repo, eventually providing example projects and guides (if it ends up being something I want to use). If this works, I believe it will provide a simple architecture that is highly testable (via unit and integration testing) and very clean.

## The Basic MVP for Firmware

**Model**
Our model will handle things like storing data to flash, settings, GPIO configuration, etc... This code should really be constant even if our hardware changes.

**Presenter**
Our presenter will handle any necessary logic between the Model and View. It will accept events from the view, tell the model when and what data to update, the provide any updates to the view that are necessary. This code should remain constant even if hour hardware changes.

**View**
Our view is closely related to the hardware itself, so it may change if our hardware changes. The view will take actions (from outside the device) such as user input/buttons/sensors/etc...
