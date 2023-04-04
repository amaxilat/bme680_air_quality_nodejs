# bme680_air_quality_nodejs

> A nodejs script to get data from BME680 Sensor on a RapspberryPi

## Hardware requirements

* [Raspberry Pi](https://www.raspberrypi.org/)
* [BME680 Breakout](https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors/bme680/)

## Installation

Note: these installation instructions assume that your Raspberry Pi is running an installation
of [Raspbian Bullseye](https://www.raspberrypi.org/downloads/raspbian/), with both [Node.js v19.x](https://nodejs.org/)
and [npm](https://www.npmjs.com/) installed.

### Preparing for the installation

1. First of all, make sure your Raspberry Pi is up-to-date:

        sudo apt-get update && sudo apt-get dist-upgrade

### Installing bme680-sensor

1. Use `cd` to navigate to your Node.js project directory.

2. Install `bme680-sensor` using npm:

        npm install bme680-sensor --save

## Usage

1. Start by loading the module:

        const {Bme680} = require('bme680-sensor');

2. Initialize the Bme680 object:

        const bme680 = new Bme680(1, 0x77);

3. Make sure the I2C address is the correct for the breakout you use (`0x77` in my case, could also be `0x76`).

4. Running the script:

````javascript
bme680.initialize().then(async () => {
    // Measure the air quality with an interval of one second.
    await measureAirQuality(300000, 1000, receivedEnvironmentalData);
});
````

5. `measureAirQuality` receives 3 arguments, the startupTime, the polling interval, and a callback to receive the data
   calculated.
