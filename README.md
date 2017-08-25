<img alt="Wehkamp Logo" src="https://www.wehkamp.nl/service/search-navigation-components/img/logo_wehkamp-2scWN3RNjaEl.png" />

# Front end guide

Wehkamp is one of the largest consumer-oriented e-commerce websites in The Netherlands. To keep growing we try to leverage the latest technology and the talented people in our company. For new hires, this can be a daunting environment to come into. 

This study guide is based on the [Grab study guide](https://github.com/grab/front-end-guide) and is meant to explain the choices that were made with regards to front end technology and where to find good resources to learn more about each technology.

This study guide is meant for people that don't have (a lot of) experience with these technologies. If you have been keeping up to date with the developments in front end, this guide won't be of much benefit to you.

## Table of Contents

- [Front end guide](#front-end-guide)
	- [Table of Contents](#table-of-contents)
	- [Progressive Web Apps](#progressive-web-apps)
	- [JavaScript Language](#javascript-language)
	- [User Interface](#user-interface)
	- [Maintainability](#maintainability)
		- [Testing](#testing)
			- [Jest](#jest)
			- [Enzyme](#enzyme)
			- [Cypress](#cypress)
		- [Linting Javascript](#linting-javascript)
		- [Linting CSS](#linting-css)

## Progressive Web Apps

Some time ago, Google coined the term *Progressive Web App* (PWA), to describe a web app that would provide the same user experience as a native app on a mobile device. A PWA is not so much a specific tool, but a compilation of various best practices and technologies that should lead to a "native" feel in a web app.

The benefits:
 * A responsive website, with a low Time To Interactive and fast navigation between pages. The use of a Service Worker allows for intelligent caching of data and assets. 
 * A "native"-like experience with fluent animations and low load times.
 * The option to implement more advanced APIs such as Push Notifications
 * Provides the user with the option to "install" the app on his phone or tablet and use it as if it was a native app.
 
 The downsides:
  * Not all browsers support service workers, which are a key technology in PWAs. Most notably Safari on iOS (and macOS) lacks support. However, work has started to implement service workers for Safari, at least in macOS. Also, Safari does support many other features of PWAs.
  * People are not yet used to installable web apps. They might prefer a native app, because of familiarity. 
  * PWAs are still in the early adopter stage, there are not many tools and support libraries that make the development of a PWA easier.
  
Even though PWAs are still in their infancy, we think that an e-commerce site like ours will benefit greatly from the speed improvements and native feel that it's worth pursuing a PWA solution. For new engineers, it might be a challenge, because there are many things that are a part of building a PWA that are technically advanced (like code splitting, tree shaking, etc.). However, PWAs are currently hot, so many of the front end leaders are blogging about this and building tools to make creating a PWA easier.

### Study links
 - [Progressive Web Apps](https://developers.google.com/web/progressive-web-apps/)
 - [Build your first PWA](https://codelabs.developers.google.com/codelabs/your-first-pwapp/#0)
 - [Udacity PWA Course](https://classroom.udacity.com/courses/ud811)
 - [Google PWA Training](https://developers.google.com/web/ilt/pwa/)

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

ReactJS is one of the more advanced frameworks/libraries that have emerged over the past few years. Since its release in 2013, it has convinced a lot of front end devs to start using it and building tools on top of it, such as [Next.JS](https://github.com/zeit/next.js/) and [Create-React-App](https://github.com/facebookincubator/create-react-app). ReactJS is not a framework that provides everything out of the box, but it only handles the view layer of your app. The developer can create their own routing and data management solutions or include other modules to handle this.
For years, front end developers were encouraged to write JavaScript, HTML, and CSS separately. ReactJS challenged this by using JSX, a HTML-like syntax that could be written directly into JavaScript files. Through a transpiler, this would be converted to regular JavaScript syntax. Later, other developers added CSS to the mix, with solutions like [glamorous](https://github.com/paypal/glamorous) or [styled-components](https://www.styled-components.com/).

The features of ReactJS are:
 - **Declarative** - Through JSX, you describe what your component should render, depending on the state and incoming data. In the old days, devs would have to use jQuery to manipulate the DOM to get from one app state to the next. In React, you just change the incoming data or the internal state of the component and the view will be updated automatically, according to how it was specified. JSX also makes it easy to see what the component will render.
  - **Functional** - The view is a pure function of the `props` (external data) and `state` (internal data). Given the same `props` and `state`, the view will always be rendered the same. Pure functions are easy to test, and so that also goes for functional components. Just provide a React component with the same `props` and `state` in a test, and the outcome will always be the same.
  - **Maintainable** - Writing small components encourages reusability. By defining the `propTypes`, components are self-documenting as the reader can clearly see what types of input the component needs. And because your component is a self-contained unit, your view and logic for that component should not be affected by other components, nor affect other components. This makes it easy to shift components around during large-scale refactorings, as long as the same `props` are supplied to the component.
  - **High performance** - Changes in `props` and `state` are not directly translated to the DOM but are first applied to the so-called Virtual DOM. The Virtual DOM is a simple JSON representation of the DOM that is kept in memory. If a component is updated, the change is compared to the Virtual DOM. ReactJS determines the smallest changes needed to render the updated view and applies those changes to the DOM. So, for instance, instead of replacing an entire list when the title of one item is changed, only the item itself is updated.
  - **Ease of learning** - Learning React is pretty simple. You can have a simple React application up and running in a matter of minutes. Especially using something like NextJS or Create-React-App, starting a React app is a matter of writing a few components. The React API is relatively small. The React community is one of the largest, which results in a large ecosystem, open-sourced UI components, and many great resources to learn from online.
  - **Developer experience** - Part of their ecosystem is a set of tools that enhance the developer experience. [React Developer Tools](https://github.com/facebook/react-devtools) plug into your browser's Developer Tools and allow you to inspect the React components that drive your HTML. It's also possible to manipulate the props and state and see how that affects your component. 

Although there are some new contenders on the block (most notably, VueJS), React still offers enough benefits over its competitors. 

## Maintainability

Creating a maintainable code base is **very** important. At Wehkamp we have multiple engineers working on multiple projects. We highly value readability, maintainability, and stability of our code bases and there are a few ways to achieve that: Unit testing, End-to-end testing and forcing a consistent coding style.

### Testing

As mentioned we separate testing by splitting them into Unit testing & End-to-end testing for that we use a couple of utility tools.

#### Jest

<img alt="Jest Logo" src="https://cdn.rawgit.com/grab/front-end-guide/master/images/jest-logo.svg" width="80px" />

[Jest](http://facebook.github.io/jest/) is a testing library by Facebook that aims to make the process of testing pain-free. As with Facebook projects, it provides a great development experience out of the box. Tests can be run in parallel resulting in a shorter duration. During watch mode, by default, only the tests for the changed files are run. One particular feature we like is "Snapshot Testing". Jest can save the generated output of your React component and Redux state and save it as serialized files, so you wouldn't have to manually come up with the expected output yourself. Jest also comes with built-in mocking, assertion and test coverage. One library to rule them all!

##### Study links

 - [Jest getting started guide](https://facebook.github.io/jest/docs/en/getting-started.html)
 - [Jest API reference](https://facebook.github.io/jest/docs/en/api.html)



#### Enzyme

<img alt="Airbnb Logo" src="https://avatars0.githubusercontent.com/u/698437" width="100px" />

[Enzyme](http://airbnb.io/enzyme/) by Airbnb makes it easier to generate, assert, manipulate and traverse your React components' output with a jQuery-like API. It is recommended that Enzyme is used to test React components. Enzyme makes writing Jest tests fun and easy.
##### Study links

 - [Enzyme API reference](http://airbnb.io/enzyme/docs/api/)

#### Cypress

<img alt="Enzyme logo" src="https://pbs.twimg.com/profile_images/715181587596505088/WCV1ZBXh_400x400.jpg" width="100px">

[Cypress](https://www.cypress.io/) is a test engine that runs unit and integration (so called end-to-end testing) tests in your browser. It's language agnostic and no dependencies have to be installed prior to using it. It provides real-time command execution, gives you Clear visibility, it's easy to debug and has a simple API.
##### Study links

 - [Cypress getting started guide](https://docs.cypress.io/guides/getting-started/why-cypress.html#What-You’ll-Learn) 
- [Cypress API reference](https://docs.cypress.io/api/introduction/api.html)

### Linting Javascript

<img alt="ESLint Logo" src="https://cdn.rawgit.com/grab/front-end-guide/master/images/eslint-logo.svg" width="80px" />

A linter is a tool to statically analyze code and finds problems with them, potentially preventing bugs/runtime errors and at the same time, enforcing a coding style. Time is saved during pull request reviews when reviewers do not have to leave nitpicky comments on coding style. [ESLint](http://eslint.org/) is a tool for linting JavaScript code that is highly extensible and customizable. Teams can write their own lint rules to enforce their custom styles. At Wehkamp, we use Airbnb's [`eslint-config-airbnb`](https://www.npmjs.com/package/eslint-config-airbnb) pre-set, that has already been configured with the common good coding style in the [Airbnb JavaScript style guide](https://github.com/airbnb/javascript).

For the most part, using ESLint is as simple as tweaking a configuration file in your project folder. There's nothing much to learn about ESLint if you're not writing new rules for it. Just be aware of the errors when they surface and Google it to find out the recommended style.

Here's an example of `.eslint` file that we use in a couple of repositories.

```
{
  "env": {
    "browser": true,
    "node": true,
    "jest": true,
    "mocha": true
  },
  "extends": "airbnb",
  "parser": "babel-eslint",

  // additions to, or overrides of the airbnb rules
  "rules": {
    "max-len": ["error", 140],
    "no-use-before-define": ["error", "nofunc"],
    "import/no-named-as-default": ["off"],
    "react/jsx-filename-extension": ["error", { "extensions": [".js", ".jsx"] }]
  }
}
```

#### Study Links

- [ESLint Homepage](http://eslint.org/)
- [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)

### Linting CSS