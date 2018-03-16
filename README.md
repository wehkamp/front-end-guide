<img alt="Wehkamp Logo" src="https://www.wehkamp.nl/service/search-navigation-components/img/logo_wehkamp-2scWN3RNjaEl.png" />

# Front-end guide

Wehkamp is one of the largest consumer-oriented e-commerce websites in The Netherlands. To keep growing we try to leverage the latest technology and the talented people in our company. For new hires, this can be a daunting environment to come into. 

This study guide is based on the [Grab study guide](https://github.com/grab/front-end-guide) and is meant to explain the choices that were made with regards to front-end technology and where to find good resources to learn more about each technology.

This study guide is meant for people that don't have (a lot of) experience with these technologies. If you have been keeping up to date with the developments in front-end, this guide won't be of much benefit to you.

## Table of Contents

- [front-end guide](#front-end-guide)
	- [Table of Contents](#table-of-contents)
	- [Progressive Web Apps](#progressive-web-apps)
	- [JavaScript Language](#javascript-language)
	- [User Interface](#user-interface)
	- [Maintainability](#maintainability)
	- [Testing your code](#testing-your-code)
		- [Jest](#jest)
		- [Enzyme](#enzyme)
		- [Cypress](#cypress)
	- [Linting](#linting)
		- [Linting JavaScript](#linting-javascript)
		- [Linting CSS](#linting-css)
	- [Package Management](#package-management)
	- [Formatting Code](#formatting-code)
	- [Build System](#build-system)
	- [Continuous Integration](#continuous-integration)
	- [Continuous Delivery](#continuous-delivery)


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
  
Even though PWAs are still in their infancy, we think that an e-commerce site like ours will benefit greatly from the speed improvements and native feel that it's worth pursuing a PWA solution. For new engineers, it might be a challenge, because there are many things that are a part of building a PWA that are technically advanced (like code splitting, tree shaking, etc.). However, PWAs are currently hot, so many of the front-end leaders are blogging about this and building tools to make creating a PWA easier.

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

 - [Learn ES5 on Codecademy](https://www.codecademy.com/learn/learn-JavaScript)
 - [Learn ES2015 on Babel](https://babeljs.io/learn-es2015/)
 - [Exploring ES6](http://exploringjs.com/es6/)

### Other Study Plans
 - [State of the JavaScript Landscape: A Map for Newcomers](http://www.infoq.com/articles/state-of-javascript-2016)
- [The Hitchhiker's guide to the modern front-end development workflow](http://marcobotto.com/the-hitchhikers-guide-to-the-modern-front-end-development-workflow/)
- [How it feels to learn JavaScript in 2016](https://hackernoon.com/how-it-feels-to-learn-javascript-in-2016-d3a717dd577f#.tmy8gzgvp)
- [Roadmap to becoming a web developer in 2017](https://github.com/kamranahmedse/developer-roadmap#-frontend-roadmap)
- [Modern JavaScript for Ancient Web Developers](https://trackchanges.postlight.com/modern-javascript-for-ancient-web-developers-58e7cae050f9)
- [A Study Plan To Cure JavaScript Fatigue](https://medium.freecodecamp.com/a-study-plan-to-cure-javascript-fatigue-8ad3a54f2eb1#.c0wnrrcwd)
- [JS Stack from Scratch](https://github.com/verekia/js-stack-from-scratch)
- [A Beginner’s JavaScript Study Plan](https://medium.freecodecamp.com/a-beginners-javascript-study-plan-27f1d698ea5e#.bgf49xno2)

## User Interface

ReactJS is one of the more advanced frameworks/libraries that have emerged over the past few years. Since its release in 2013, it has convinced a lot of front-end devs to start using it and building tools on top of it, such as [Next.JS](https://github.com/zeit/next.js/) and [Create-React-App](https://github.com/facebookincubator/create-react-app). ReactJS is not a framework that provides everything out of the box, but it only handles the view layer of your app. The developer can create their own routing and data management solutions or include other modules to handle this.
For years, front-end developers were encouraged to write JavaScript, HTML, and CSS separately. ReactJS challenged this by using JSX, an HTML-like syntax that could be written directly into JavaScript files. Through a transpiler, this would be converted to regular JavaScript syntax. Later, other developers added CSS to the mix, with solutions like [glamorous](https://github.com/paypal/glamorous) or [styled-components](https://www.styled-components.com/).

The features of ReactJS are:
 - **Declarative** - Through JSX, you describe what your component should render, depending on the state and incoming data. In the old days, devs would have to use jQuery to manipulate the DOM to get from one app state to the next. In React, you just change the incoming data or the internal state of the component and the view will be updated automatically, according to how it was specified. JSX also makes it easy to see what the component will render.
  - **Functional** - The view is a pure function of the `props` (external data) and `state` (internal data). Given the same `props` and `state`, the view will always be rendered the same. Pure functions are easy to test, and so that also goes for functional components. Just provide a React component with the same `props` and `state` in a test, and the outcome will always be the same.
  - **Maintainable** - Writing small components encourages reusability. By defining the `propTypes`, components are self-documenting as the reader can clearly see what types of input the component needs. And because your component is a self-contained unit, your view and logic for that component should not be affected by other components, nor affect other components. This makes it easy to shift components around during large-scale refactorings, as long as the same `props` are supplied to the component.
  - **High performance** - Changes in `props` and `state` are not directly translated to the DOM but are first applied to the so-called Virtual DOM. The Virtual DOM is a simple JSON representation of the DOM that is kept in memory. If a component is updated, the change is compared to the Virtual DOM. ReactJS determines the smallest changes needed to render the updated view and applies those changes to the DOM. So, for instance, instead of replacing an entire list when the title of one item is changed, only the item itself is updated.
  - **Ease of learning** - Learning React is pretty simple. You can have a simple React application up and running in a matter of minutes. Especially using something like NextJS or Create-React-App, starting a React app is a matter of writing a few components. The React API is relatively small. The React community is one of the largest, which results in a large ecosystem, open-sourced UI components, and many great resources to learn from online.
  - **Developer experience** - Part of their ecosystem is a set of tools that enhance the developer experience. [React Developer Tools](https://github.com/facebook/react-devtools) plug into your browser's Developer Tools and allow you to inspect the React components that drive your HTML. It's also possible to manipulate the props and state and see how that affects your component. 

Although there are some new contenders on the block (most notably, VueJS), React still offers enough benefits over its competitors. 

### Study links
 - [Comprehensive guide to React](https://tylermcginnis.com/reactjs-tutorial-a-comprehensive-guide-to-building-apps-with-react/)

## Maintainability

Creating a maintainable codebase is **very** important!
At Wehkamp we have multiple engineers working on various projects. We also have a lot of new people onboarding on a regular basis, and it's a good practice to have them contributing code through our standard in a couple of weeks. We highly value readability, maintainability, and stability of our codebases and there are a few ways to achieve that: unit testing, end-to-end testing and forcing a consistent coding style.

Besides writing maintainable code, it's good to have a maintainable development workflow as well. At Wehkamp we do use version control, write documentation, work in different environments, have external and internal dependencies and per team have specific workflow enhancements.

## Testing your code

As mentioned we separate testing by splitting them into unit testing, integration testing & end-to-end testing for that we use a couple of utility tools.

### Jest

<img alt="Jest Logo" src="./images/jest-logo.svg" width="90px" />

[Jest](http://facebook.github.io/jest/) is a testing library by Facebook that aims to make the process of testing pain-free. As with Facebook projects, it provides a great development experience out of the box. Tests can run in parallel resulting in a shorter duration. During watch mode, by default, only the tests for the changed files are run. One particular feature we like is "Snapshot Testing". Jest can save the generated output of your React component and Redux state and save it as serialized files, so you wouldn't have to come up with the expected output yourself. Jest also comes with built-in mocking, assertion and test coverage. One library to rule them all!

 - [Jest getting started guide](https://facebook.github.io/jest/docs/en/getting-started.html)
 - [Jest API reference](https://facebook.github.io/jest/docs/en/api.html)


### Enzyme

<img alt="Airbnb Logo" src="./images/airbnb-logo.svg" width="100" />

[Enzyme](http://airbnb.io/enzyme/) by Airbnb makes it easier to generate, assert, manipulate and traverse your React components' output with a jQuery-like API. It is recommended that Enzyme is used to test React components. Enzyme makes writing Jest tests fun and easy.

 - [Enzyme API reference](http://airbnb.io/enzyme/docs/api/)

### Cypress

<img alt="Cypress Logo" src="./images/cypress-io-logo.png" width="100" />

[Cypress](https://www.cypress.io/) is a test engine that runs unit and integration (so-called end-to-end testing) tests in your browser. It's language agnostic, and no dependencies have to install before using it. It provides real-time command execution, shows your application when testing, it's easy to debug and has a simple API.

 - [Cypress getting started guide](https://docs.cypress.io/guides/getting-started/why-cypress.html#What-You???ll-Learn) 
- [Cypress API reference](https://docs.cypress.io/api/introduction/api.html)

## Linting

A linter is a tool to analyze code statically and find problems with it. Potentially preventing runtime errors and at the same time, enforcing a coding style. It saves time during pull request reviews when reviewers do not have to leave nitpicky comments on coding style. 

### Linting JavaScript

<img alt="ESlint Logo" src="./images/eslint-logo.svg" width="100" />

[ESLint](http://eslint.org/) is a tool for linting JavaScript code that is highly extensible and customizable. Teams can write their own lint rules to enforce their custom styles. At Wehkamp, we use Airbnb's [`eslint-config-airbnb`](https://www.npmjs.com/package/eslint-config-airbnb) pre-set, that has already been configured with the standard coding style in the [Airbnb JavaScript style guide](https://github.com/airbnb/JavaScript).

For the most part, using ESLint is as simple as tweaking a configuration file in your project folder. There's nothing much to learn about ESLint if you're not writing new rules for it. Just be aware of the errors when they surface and Google it to find out the recommended style.


- [ESLint Homepage](http://eslint.org/)
- [Airbnb JavaScript Style Guide](https://github.com/airbnb/JavaScript)

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

ESlint allows you to auto fix code by using the `--fix` flag on execution. You could even create a file watcher for it, so it fix your code on save.

### Linting CSS

<img alt="Stylelint Logo" src="./images/stylelint-logo.svg" width="100" />

For linting SCSS, we use stylelint. Like ESLint, stylelint is designed in a very modular fashion, allowing developers to turn rules on/off and write custom plugins for it. 

Once you have learned ESLint, learning stylelint would be effortless considering their similarities. stylelint is currently being used by large enterprises like [Facebook](https://code.facebook.com/posts/879890885467584/improving-css-quality-at-facebook-and-beyond/), [Github](https://github.com/primer/stylelint-config-primer) and [Wordpress](https://github.com/WordPress-Coding-Standards/stylelint-config-wordpress).

Stylelint even enables you to auto fix code although the feature is not fully matured yet, and is only able to correct a limited number of rules.

- [stylelint Homepage](https://stylelint.io/)
- [Lint your CSS with stylelint](https://css-tricks.com/stylelint/)

Like ESlint, Stylelint also enables you to auto fix code although the feature is not fully matured yet, and is only able to correct a limited number of rules.

## Package Management

<img alt="NPM Logo" src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/db/Npm-logo.svg/640px-Npm-logo.svg.png" width="100"/>

`npm` is a package manager for the JavaScript programming language. It is the default package manager for the JavaScript runtime environment Node.js. It consists of a command line client, also called `npm`, and an online database of public and paid-for private packages, called the `npm` registry. The registry is accessed via the client, and the available packages can be browsed and searched via the `npm` website. The package manager and the registry are managed by npm, Inc.

If you take a peek into your `node_modules` directory, you will be shocked by the number of directories that are contained in it. Each babel plugin, lodash function, is a package on its own. When you have multiple projects, these packages are duplicated across each project and they are largely similar. 

In the old days each time you run `npm install` in a new project, these packages are downloaded over and over again even though they already exist in some other project on your computer. At first, NPM had problems with non-determinism but as of version 5, the installed packages are handled via a `package.lock` file, which ensures that every install results in the exact same file structure in `node_modules` across all machines. 

The most common `npm` commands can be found [here](https://docs.npmjs.com/). `npm` is extensible and one of our extensions is `npm-check` which makes updating dependencies a breeze especially when the modern JavaScript project requires so many dependencies these days. [Do check it out!](https://github.com/dylang/npm-check)

- [npm Homepage](https://docs.npmjs.com/)

## Formatting Code

<img alt="Prettier Logo" src="https://cdn.rawgit.com/grab/front-end-guide/master/images/prettier-logo.png" width="100" />

Another tool for enforcing consistent coding style for JavaScript and CSS is [Prettier](https://github.com/prettier/prettier).

In most cases, it is recommended to setup Prettier on top of ESLint and stylelint and integrate it into the workflow. This allows the code to be formatted into consistent style automatically via commit hooks so that developers do not need to spend time formatting the coding style manually.

Note that Prettier only enforces coding style, but does not check for logic errors in the code. Hence it is not a replacement for linters.

#### Study Links

- [Prettier Homepage](https://prettier.io/)
- [Prettier GitHub repo](https://github.com/prettier/prettier)
- [Comparison between tools that allow you to use ESLint and Prettier together](https://gist.github.com/yangshun/318102f525ec68033bf37ac4a010eb0c)


## Build System - webpack

<img alt="webpack Logo" src="https://cdn.rawgit.com/grab/front-end-guide/master/images/webpack-logo.svg" width="100" />

This part will be kept short as setting up webpack can be a tedious process and might be a turn-off to developers who are already overwhelmed by the barrage of new things they have to learn for front-end development. In a nutshell, [webpack](https://webpack.js.org/) is a module bundler that compiles a front-end project and its dependencies into a final bundle to be served to users. Usually, projects will already have the webpack configuration set up and developers rarely have to change it. Having an understanding of webpack is still a good to have in the long run. It is due to webpack that features like hot reloading and CSS modules are made possible.

We have found the [webpack walkthrough](https://survivejs.com/webpack/foreword/) by SurviveJS to be the best resource on learning webpack. It is a good complement to the official documentation and we recommend following the walkthrough first and referring to the documentation later when the need for further customization arises.

#### Study Links

- [webpack Homepage](https://webpack.js.org/)
- [SurviveJS - Webpack: From apprentice to master](https://survivejs.com/webpack/foreword/)

## Continuous Integration

We use [Jenkins CI](https://jenkins.io/) for our continuous integration (CI) pipeline. Continuous Integration (CI) is a development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early. 

By integrating regularly, you can detect errors quickly, and locate them more easily.

- Run linting for the project.
- Run unit tests for the project.
- If the tests pass:
  - Test coverage generated by Jest is uploaded to [Codecov](https://codecov.io/)

#### Study Links

- [Jenkins Homepage](https://jenkins.io/)
- [Codecov Homepage](https://codecov.io/)
- [ToughtWorks](https://www.thoughtworks.com/continuous-integration)


## Continuous Delivery

We use [Jenkins CD](https://jenkins.io/) for our continuous delivery (CD) pipeline.  

Continuous Delivery can help large organizations become as lean, agile and innovative as startups. Through reliable, low-risk releases, Continuous Delivery makes it possible to continuously adapt software in line with user feedback, shifts in the market and changes to business strategy. Test, support, development, and operations work together as one delivery team to automate and streamline the build-test-release process.

Continuous Delivery is the natural extension of Continuous Integration, an approach in which teams ensure that every change to the system is releasable, and release any version with the push of a button. Continuous Delivery aims to make releases boring, so that we can deliver frequently and get quick feedback on what users care about.

#### Study Links

- [Jenkins Homepage](https://jenkins.io/)
- [Codecov Homepage](https://codecov.io/)
- [ToughtWorks](https://www.thoughtworks.com/continuous-delivery)

## Footnotes

If certain things are still unclear, please do *NOT* hesitate and ask around, we are all willing to help.
