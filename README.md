![BlinkStick Node](http://www.blinkstick.com/images/logos/blinkstick-nodejs.png)

BlinkStick Node provides an interface to control Blinkstick
devices connected to your computer with Node.js.

What is BlinkStick? It's a smart USB-controlled LED device. More info about it here:

[http://www.blinkstick.com](http://www.blinkstick.com)

## Note

This fixes the following errors when running `npm install` on _Mac_:

```
node-pre-gyp ERR! Tried to download(404): https://tessel-builds.s3-us-west-2.amazonaws.com/pre-gyp/usb/v1.1.1/usb_bindings-v1.1.1-node-v59-darwin-x64.tar.gz
node-pre-gyp ERR! Pre-built binaries not found for usb@1.1.1 and node@9.2.0 (node-v59 ABI, unknown) (falling back to source compile with node-gyp)
```

Upgrading `usb` package to its latest version prevents building it. Just run
`npm install`.


## Resources

* [Code repository on GitHub](https://github.com/arvydas/blinkstick-node)
* [API reference documentation](https://arvydas.github.io/blinkstick-node)
* [Code Examples](https://github.com/arvydas/blinkstick-node/wiki)

## Requirements

* Node.js
* Libusb for Mac OSX and Linux

### Requirements for Mac OSX

Install Node with npm and libusb using [homebrew](http://mxcl.github.io/homebrew/):

```
$> brew install node
$> brew install libusb
```

### Requirements for Windows

Install [Node for Windows](http://nodejs.org/download/) and make sure it's added
to your PATH environment variable.

### Requirements for Linux

```
$> sudo apt-get install libusb nodejs npm
```

#### Raspberry Pi

The apt repositories keep a very old version of NodeJS.  Please install the
[Node ARM Binaries](http://nodejs.org/download/) from the official site. Run the
following command to confirm the architecture of your Raspberry Pi.

```
$> uname -m
```

Addionally, you will need to install `libudev-dev` rather than `libusb`.

```
$> sudo apt-get install libudev-dev -y
```


## Install BlinkStick node module

Install using npm:

```
$> npm install blinkstick
```

## Getting started

    var blinkstick = require('blinkstick');

To get the first blinkstick on your system:

    var device = blinkstick.findFirst();

To set the color:

    led.blink('random', function(){
        led.pulse('random', function(){
            led.setColor('red', function(){
            });
        });
    });

More details and examples available in the wiki:

https://github.com/arvydas/blinkstick-node/wiki

## Permission problems

If you get an error message on Linux:

    Error: LIBUSB_ERROR_ACCESS

Please run the following command and restart your computer:

    echo "SUBSYSTEM==\"usb\", ATTR{idVendor}==\"20a0\", ATTR{idProduct}==\"41e5\", MODE:=\"0666\"" | sudo tee /etc/udev/rules.d/85-blinkstick.rules

## Maintainers

* Arvydas Juskevicius - [http://twitter.com/arvydev](http://twitter.com/arvydev)
* Paul Cuthbertson - [http://twitter.com/paulcuth](http://twitter.com/paulcuth)

## Copyright and License

Copyright (c) 2014 Agile Innovative Ltd and contributors

Released under MIT license.
