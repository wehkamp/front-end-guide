# Wehkamp Front end guide

Wehkamp is one of the largest consumer-oriented ecommerce websites in The Netherlands. To keep growing we try to leverage the latest technology and the talented people in our company. For new hires this can be a daunting environment to come into. 

This study guide is based on the [Grab study guide](https://github.com/grab/front-end-guide) and is meant to explain the choices that were made with regards to front end technology and where to find good resources to learn more about each technology.

This study guide is meant for people that don't have (a lot of) experience with these technologies. If you have been keeping up to date with the developments in front end, this guide won't be of much benefit to you.

## Table of Contents

* [Progressive Web Apps](#progressive-web-apps)
* [JavaScript language](#javascript-language)
* [User Interface](#user-interface)
  * [Server-side Rendering](#server-side-rendering)
* [State Management](#state-management)
* [Coding with style](#coding-with-style)
* [Maintainability](#maintainability)
  * [Testing](#testing)
  * [Linting JavaScript](#linting-javascript)
  * [Linting CSS](#linting-css)
* [Build System](#build-system)
* [Package Management](#package-management)
* [Continuous Integration/Deployment](#continuous-integration-deployment)
* [Hosting](#hosting)
* [Development](#development)

## Progressive Web Apps

Some time ago, Google coined the term *Progressive Web App* (PWA), to describe a web app that would provide the same user experience as a native app on a mobile device. A PWA is not so much a specific tool, but a compilation of various best practices and technologies that should lead to a "native" feel in a web app.

The benefits:
 * A responsive website, with a low Time To Interactive and fast navigation between pages. The use a of Service Worker allows for intelligent caching of data and assets. 
 * A "native"-like experience with fluent animations and low load times.
 * The option to implement more advanced APIs such as Push Notifications
 * Provides the user with the option to "install" the app on his phone or tablet and use it as if it was a native app.
 
 The downsides:
  * Not all browsers support service workers, which are a key technology in PWAs. Most notably Safari on iOS (and macOS) lacks support. However, work has started to implement service workers for Safari, at least in macOS. Also, Safari does support many other features of PWAs.
  * People are not yet used to installable web apps. They might prefer a native app, because of familiarity. 
  * PWAs are still in the early adopter stage, there are not many tools and support libraries that make the development of a PWA easier.
  
Even though PWAs are still in their infancy, we think that an ecommerce site like ours will benefit greatly from the speed improvements and native feel that it's worth pursuing a PWA solution. For new engineers, it might be a challenge, because there are many things that are a part of building a PWA that are technically advanced (like code splitting, tree shaking, etc.). However, PWAs are currently the hot, so many of the front end leaders are blogging about this and building tools to make creating a PWA easier.

### Study links
 - [Progressive Web Apps](https://developers.google.com/web/progressive-web-apps/)
 - [Build your first PWA](https://codelabs.developers.google.com/codelabs/your-first-pwapp/#0)
 - [Udacity PWA Course](https://classroom.udacity.com/courses/ud811)

## JavaScript Language

Before diving into frameworks to build the UI, it's a good idea to get at least a solid grasp of the current state of JavaScript. The standardized version of JavaScript is called ECMAScript. 

In 2015, JavaScript (the language) got a major update through ECMAScript 2015 (a.k.a. ES6). The standards body that provides these updates, TC39, is now creating smaller improvements that they release every year. So, the latest version is ES2016, but the plans for ES2017 are already open and some browser vendors are experimenting with implementations for that, even though they haven't implemented everything of ES2015. 

Because these newer iterations of the language provide many benefits to us as developers, we use [Babel](https://babeljs.io) to transpile our code from the latest ECMAScript standards to JavaScript that the browsers can understand. We use [babel-preset-env](https://github.com/babel/babel-preset-env) to make sure that Babel produces code that the most-used browsers can understand.

Take a few days to make sure you are up to speed with the features of ES5.1 and ES2015 to make sure you understand code samples you might come across in the study links in later sections of this guide. Make sure you understand arrow functions, classes, template strings, destructuring, default/rest/spread operators, and importing/exporting modules.

### Study links

 - [Learn ES5 on Codecademy](https://www.codecademy.com/learn/learn-javascript)
 - [Learn ES2015 on Babel](https://babeljs.io/learn-es2015/)
 - [Exploring ES6](http://exploringjs.com/es6/)

## User Interface

At Wehkamp, we build our user interfaces with ReactJS. 
