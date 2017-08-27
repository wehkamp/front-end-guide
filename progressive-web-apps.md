# Progressive web apps

> “A Progressive Web App uses modern web capabilities to deliver an app-like user experience.”  - [Progressive web apps](https://developers.google.com/web/progressive-web-apps/?hl=en)


## Overview
In order to create an (native) app-like experience on the web the app needs to be:

- Reliable - Load instantly and never show the downasaur, even in uncertain network conditions.
- Fast - Respond quickly to user interactions with silky smooth animations and no janky scrolling.
- Engaging - Feel like a natural app on the device, with an immersive user experience.

This new level of quality allows Progressive Web Apps to earn a place on the user's home screen.

## Features of a progressive web app
- Progressive - Work for every user, regardless of browser choice because they’re built with progressive enhancement as a core tenet.
- Responsive - Fit any form factor: desktop, mobile, tablet, or forms yet to emerge.
- Connectivity independent - Service workers allow work offline, or on low quality networks.
- App-like - Feel like an app to the user with app-style interactions and navigation.
- Fresh - Always up-to-date thanks to the service worker update process.
- Safe - Served via HTTPS to prevent snooping and ensure content hasn’t been tampered with.
- Discoverable - Are identifiable as “applications” thanks to W3C manifests[6] and service worker registration scope allowing search engines to find them.
- Re-engageable - Make re-engagement easy through features like push notifications.
- Installable - Allow users to “keep” apps they find most useful on their home screen without the hassle of an app store.
- Linkable - Easily shared via a URL and do not require complex installation.

## Enabling technologies

### Manifest
The web app [manifest](https://www.w3.org/TR/appmanifest/) is a W3C specification defining a JSON-based manifest to provide developers a centralized place to put metadata associated with a web application including:

- The name of the web application
- Links to the web app icons or image objects
- The preferred URL to launch or open the web app
- The web app configuration data for a number of characteristics
- Declaration for default orientation of the web app
- Enables to set the display mode e.g. full screen

By setting and manipulating the metadata for the web manifest file, developers enable user agents to create seamless native-like mobile experiences through the Progressive Web App.

### Service Worker
[Service worker](https://w3c.github.io/ServiceWorker/) is the key technology powering Progressive Web Apps. They are the foundation for features as periodic background syncing, offline-caching, push notifications and so on.

Technically, Service Workers provide a scriptable network proxy in the web browser to manage the web/HTTP requests programmatically. The Service Workers lie between the network and device to supplement the content. They are capable of using the cache mechanisms efficiently and allow error-free behavior during offline periods.

### Study links
- [Service Workers: an Introduction](https://developers.google.com/web/fundamentals/getting-started/primers/service-workers)
- [Service workers explained](https://github.com/w3c/ServiceWorker/blob/master/explainer.md)
- [Using Service Workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
