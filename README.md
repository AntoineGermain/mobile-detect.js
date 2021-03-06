# mobile-detect.js

A loose port of [Mobile-Detect](https://github.com/serbanghita/Mobile-Detect) to JavaScript.

This script will detect the device by comparing patterns against a given User-Agent string.
You can find out information about the device rendering your web page:

  * mobile or not
  * if mobile, whether phone or tablet
  * operating system
  * Mobile Grade (A, B, C)
  * specific versions (e.g. WebKit)


# Usage

## Browser

    <script src="mobile-detect.js"></script>
    <script>
        var md = new MobileDetect(window.navigator.userAgent);
        // ... see below
    </script>

## Node.js / Express

    var MobileDetect = require('mobile-detect'),
        md = new MobileDetect(req.headers['user-agent']);
    // ... see below

## General

```js
// more typically we would instantiate with `window.navigator.userAgent` as user-agent
var md = new MobileDetect('Mozilla/5.0 (Linux; U; Android 4.0.3; en-in; SonyEricssonMT11i Build/4.1.A.0.562) AppleWebKit/534.30 (KHTML, like Gecko) Version/4.0 Mobile Safari/534.30');
console.log(md.mobile());     // 'Sony'
console.log(md.phone());      // 'Sony'
console.log(md.tablet());     // null
console.log(md.userAgent());  // 'Safari'
console.log(md.os());         // 'AndroidOS'
console.log(md.is('iPhone')); // false
console.log(md.is('bot'));    // false
console.log(md.version('Webkit')); // 534.3
```

## More Info ...

Open generated JSDoc in `doc/index.html`

## Side Effects

Script creates the global property `MobileDetect`.

## Modernizr Extension

When using [Modernizr](http://modernizr.com/), you can include `mobile-detect-modernizr.js`.
It will add the CSS classes `mobile`, `phone`, `tablet` and `mobilegradea` if applicable.

You can easily extend it, e.g. `android`, `iphone`, etc.

## Size (bytes)

 * development: 30025
 * minified: 18045
 * minified + gzipped: 7149


# Installation

## Bower

**TODO** is not working yet, since project is not tagged w/ a version!

    $ bower install hgoebl/mobile-detect.js --save

## Node.js / npm

**TODO** is not working yet, since project is not tagged w/ a version and not published to npmjs.org!

    $ npm install mobile-detect --save

# Alternatives

Often device detection is the first solution in your mind. Please consider looking for other solutions
like media queries and feature detection (e.g. w/ Modernizr). Maybe there are better (simpler, smaller,
faster) device detection libraries, so here you have a list:

  * [Modernizr](http://modernizr.com/)
    In most cases the better solution: don't use knowledge about device and version, but detect features
    (touch, canvas, ...)
  * [Mobile-Detect](https://github.com/serbanghita/Mobile-Detect)
    A lightweight PHP class for detecting mobile devices (including tablets).
    This is the "source" of this JavaScript project and if you use PHP on your server you should use it!
  * [dmolsen/Detector](https://github.com/dmolsen/Detector)
    Detector is a simple, PHP- and JavaScript-based browser- and
    feature-detection library that can adapt to new devices & browsers
    on its own without the need to pull from a central database of browser information.
  * [matthewhudson/device.js](https://github.com/matthewhudson/device.js)
    Conditional CSS and/or JavaScript based on device operating system, orientation and type
  * [brendanlim/mobile-fu](https://github.com/brendanlim/mobile-fu)
    Automatically detect mobile requests from mobile devices in your Rails application.
  * [FormFactor](https://github.com/PaulKinlan/formfactor)
    FormFactor helps you customize your web app for different form factors, e.g. when you make
    "the mobile version", "the TV version", etc.
  * [UAParser.js](http://faisalman.github.com/ua-parser-js/)
    Lightweight JavaScript-based User-Agent String Parser


# License

MIT-License (see LICENSE file).


# Contributing

Your contribution is welcome.
If you want new devices to be supported, please contribute to
[Mobile-Detect](https://github.com/serbanghita/Mobile-Detect) instead.

To run generate-script it is necessary to have [Mobile-Detect](https://github.com/serbanghita/Mobile-Detect)
as a sibling directory to mobile-detect.js/.
(I tried to use `git subtree` but had some problems on Mac OS X - probably my fault...)

  * fork or clone serbanghita/Mobile-Detect
  * fork hgoebl/mobile-detect.js
  * run `npm install`
  * create branch
  * make changes and run `grunt` (needs PHP >= 5.4 in your path)
  * run browser test (tests/SpecRunner.html)
  * commit, push to your branch
  * create pull request

## Testing

### Browser

Open `tests/SpecRunner.html` in different browsers.

### Node.js

    $ npm test
    $ # or
    $ grunt jasmine_node


# Donations

If you want, you can donate to [Mobile-Detect](https://github.com/serbanghita/Mobile-Detect).


# TODO

  * Extend RegEx patterns so that test passes
  * update mobilegrade() function to PHP-version
  * Provide gh_pages w/ JSDoc and a live example
