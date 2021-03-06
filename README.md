# Google Analytics AB

[![Version](http://img.shields.io/npm/v/google-analytics-ab.svg)](https://www.npmjs.org/package/google-analytics-ab) [![Build Status](https://travis-ci.org/tacnoman/googleAnalyticsAB.svg?branch=master)](https://travis-ci.org/tacnoman/googleAnalyticsAB) [![codecov](https://codecov.io/gh/tacnoman/googleAnalyticsAB/branch/master/graph/badge.svg)](https://codecov.io/gh/tacnoman/googleAnalyticsAB) [![Code Climate](https://codeclimate.com/github/tacnoman/googleAnalyticsAB/badges/gpa.svg)](https://codeclimate.com/github/tacnoman/googleAnalyticsAB) [![HitCount](http://hits.dwyl.io/tacnoman/googleAnalyticsAB.svg)](http://hits.dwyl.io/tacnoman/googleAnalyticsAB)


Lib tool in javascript to create A/B tests using Google Analytics events in easy way. With a simple configuration you can edit your page and get metrics.

## Getting started

### NPM
To install using npm you must run.

```bash
$ npm i --save google-analytics-ab
```

And use require to get the lib.

```js
var googleAnalyticsAB = require('googleAnalyticsAB');

// Or with ecma6

import googleAnalyticsAB from 'googleAnalyticsAB'
```

### Bower
To install using Bower you must run.

```bash
$ bower install google-analytics-ab
```

You can get in folder dist the compressed file (`/dist/google-analytics-ab.min.js`).

## Dependencies

- Google Analytics script (obvious?)

## Create your own first test

You must have GA script in your page.

To make a simple test, you can call:
```html
.....
<script src="https://cdn.jsdelivr.net/npm/google-analytics-ab@latest/dist/google-analytics-ab.min.js"></script>
.....
```

```js

  // Example of AB change button color. Green or Red.
  googleAnalyticsAB.create({
    name: 'MY_TEST', // Name of your first test
    percentage: 80, // Percentage of users to run in this test (Default is 80)

    // Alternatives
    options: [
      {
        name: 'green-button', // Name of your alternative
        weight: 1, // weight of your alternative (optional, default is 1)
      },
      {
        name: 'red-button',
        weight: 1,
      }
    ],

    // Method called when AB is sorted
    run: function(option) { // Current option
      var myButton = document.getElementById('myButton'); // Getting some button
      myButton.style.background = option.name === 'green-button' ? '#0F0' : '#F00'; // Change color using the label

      // Event onClick in button tested
      myButton.addEventListener('click', function(ev) {
        option.convert(); // Option has a method called convert. Use to convert :D
      });
    }
  });

```

## How to see the results

Open your Google Analytics account and go to:

`Behavior > Events > Overview`

In Event category, go to `googleAnalyticsAB`.

Click in `Event Action`.

<img src="https://raw.githubusercontent.com/tacnoman/googleAnalyticsAb/master/images/top-events-analytics-01.jpg" alt="logo" title="Event action">

Now, you will see all A/B tests running.
Click in your current A/B test.

Now, you will see your options, check all and click in `Plot rows`.

<img src="https://raw.githubusercontent.com/tacnoman/googleAnalyticsAb/master/images/top-events-analytics-02.jpg" alt="logo" title="Analytics plot lines">

See your test result :D

<img src="https://raw.githubusercontent.com/tacnoman/googleAnalyticsAb/master/images/top-events-analytics-03.jpg" alt="logo" title="Analytics result">


Ps: If you cannot see the events, you need change the date and add the current day.

Bugs? Tacnoman `<renatocassino@gmail.com>`.
