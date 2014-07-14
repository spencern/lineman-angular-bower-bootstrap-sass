# Localsage Fat Client - Using Lineman.js build tools

# Instructions
1. `git clone repo localsage`
2. `cd localsage`
3. `sudo npm install -g lineman`
4. `npm install`
5. `gem install sass`
6. `gem install bourbon`
7. `gem install neat`
5. `lineman run`
6. open your web browser to localhost:8000
7. 

# Running Tests

This template was used as the basis of [@davemo](http://www.github.com/davemo)'s [Testing Strategies for Angular JS](http://www.youtube.com/watch?v=UYVcY9EJcRs) screencast, and contains all the tests we wrote in the screencast and a few more!

To run the unit tests:

1. `lineman run` from 1 terminal window
2. `lineman spec` from another terminal window, this will launch Testem and execute specs in Chrome

To run the end-to-end tests:

## End-to-End Tests

1. `npm install protractor`
2. `./node_modules/protractor/bin/webdriver-manager update`
3. Make sure you have chrome installed.
4. `lineman run` from 1 terminal window
5. `lineman grunt spec-e2e` from another terminal window

# Defining your apps angular.module in CoffeeScript

If you are using Coffeescript to define the angular.module for your app, you will need to swap the concat order in `config/application.js` such that coffeescript files are included _before_ javascript. (If you are using JavaScript for defining the angular.module the default concat order is fine).

Add the following `concat_sourcemap` block to `config/application.js` if you want to define your app module in coffeescript:

```javascript
module.exports = function(lineman) {
  return {

    concat_sourcemap: {
      js: {
        src: [
          "<%= files.js.vendor %>",
          "<%= files.coffee.generated %>",
          "<%= files.js.app %>",
          "<%= files.ngtemplates.dest %>"
        ]
      }
    }

  };
};
```

Hopefully this helps you get up and running with AngularJS!
