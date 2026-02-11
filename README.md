html2canvas-pixelart
====================

[Downloads](https://github.com/Kriegberg/html2canvas-pixelart/releases)

### JavaScript HTML renderer optimised for pixel art ###

**html2canvas-pixelart** is a fork of html2canvas version 1.4.1 which disables image smoothing for crisp pixel art rendering. Please kindly note that this fork uses some any types `(this.ctx as any)` when disabling image smoothing. It works for my use case but your mileage may vary.

The script allows you to take "screenshots" of webpages or parts of it, directly on the users browser. The screenshot is based on the DOM and as such may not be 100% accurate to the real representation as it does not make an actual screenshot, but builds the screenshot based on the information available on the page.

### How does it work? ###
The script renders the current page as a canvas image, by reading the DOM and the different styles applied to the elements.

It does **not require any rendering from the server**, as the whole image is created on the **client's browser**. However, as it is heavily dependent on the browser, this library is *not suitable* to be used in nodejs.
It doesn't magically circumvent any browser content policy restrictions either, so rendering cross-origin content will require a [proxy](https://github.com/niklasvh/html2canvas/wiki/Proxies) to get the content to the [same origin](http://en.wikipedia.org/wiki/Same_origin_policy).

The script is still in a **very experimental state**, so I don't recommend using it in a production environment nor start building applications with it yet, as there will be still major changes made.

### Browser compatibility ###

The library should work fine on the following browsers (with `Promise` polyfill):

* Firefox 3.5+
* Google Chrome
* Opera 12+
* IE9+
* Safari 6+

As each CSS property needs to be manually built to be supported, there are a number of properties that are not yet supported.

### Usage ###

The html2canvas library utilizes `Promise`s and expects them to be available in the global context. If you wish to
support [older browsers](http://caniuse.com/#search=promise) that do not natively support `Promise`s, please include a polyfill such as
[es6-promise](https://github.com/jakearchibald/es6-promise) before including `html2canvas`.

To render an `element` with html2canvas, simply call:
` html2canvas(element[, options]);`

The function returns a [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) containing the `<canvas>` element. Simply add a promise fulfillment handler to the promise using `then`:

    html2canvas(document.body).then(function(canvas) {
        document.body.appendChild(canvas);
    });

### Building ###

You can download ready builds [here](https://github.com/Kriegberg/html2canvas-pixelart/releases).

Clone git repository:

    $ git clone git://github.com/Kriegberg/html2canvas-pixelart.git

Install dependencies:

    $ npm install

Build browser bundle

    $ npm run build

### Examples ###

For more information and examples, please visit the [homepage](https://html2canvas.hertzen.com) or try the [test console](https://html2canvas.hertzen.com/tests/).
