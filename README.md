# toast.js browser notifier library


Toast.js is a flexible minimalist JavaScript popup notifications
library written in TypeScript.

- [Bootstrap](http://twitter.github.com/bootstrap/index.html) friendly
  but does not depend on Bootstrap (notification types and colors
  match Bootstrap alerts).

- Inspired by [notifier.js](https://github.com/Srirangan/notifer.js)
  and [toastr](https://github.com/CodeSeven/toastr).

Project source on [Github](https://github.com/srackham/toast.js).

[Live demo](http://www.methods.co.nz/misc/toast/toast-examples.html).

## Usage
Include `toast.js` and `toast.css` (along with JQuery) then call the
Toast popup functions from your code e.g.

  Toast.info('Hello World!');

The nice thing about popups for transient message reporting is their
ease of use -- just a single statement per message (no HTML markup or
DOM manipulation required).

Toast.js uses jQuery so you'll also need to include it.  See
the `toast-examples.html` examples.


## API
Popup functions:

    Toast.info    (message [,title [, options]])
    Toast.warning (message [,title [, options]])
    Toast.error   (message [,title [, options]])
    Toast.success (message [,title [, options]])

Function parameters:

    message: String
    title:   String
    options: Object with properties to override Toast.defaults

The read-write `Toast.defaults` object contains the following
configuration properties:

    width:            CSS length, overrides CSS file.
    displayDuration:  In milliseconds, set to 0 to make sticky.
    fadeOutDuration:  In milliseconds.

Behavior:

- Toast popups are inserted into the top of the toast container
  (existing messages are pushed down).
- The toast container is a 'div' element with ID 'toast-container', if
  it doesn't already exist Toast.js creates and inserts it into the
  DOM 'body' element.
- The popups are removed from the toast container when they timeout or
  are clicked by the user.

Examples:

    Toast.info('Simple message');
    Toast.success('Message with title', 'Title');
    Toast.error('Sticky message', '', {displayDuration: 0});
    Toast.defaults.displayDuration = 1000;
    Toast.defaults.fadeOutDuration = 800;
    Toast.defaults.width = '800px';

## Building
To generate `toast.js` JavaScript from the `toast.ts` source file copy
the `jquery.d.ts` type declaration file from the TypeScript
distribution to the build directory then run the Typescript compiler:

    tsc toast.ts

If you have [jake](https://github.com/mde/jake) installed you can run:

    jake build


