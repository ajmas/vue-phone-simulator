Vue Phone Simulator
===================

This project provides a web based phone simulator, allowing
basic simulation of a web page on a phone. While the end
goal is to make this as complete as possible, the humble
beginnings is to provide something that will allow to get a
basic idea of how a web page will present itself.

Note when running you'll need to ensure it is running via
'http', rather than 'https', if you want to be able to test
pages that are not served up via https. This is due to
restrictions imposed by the security model in modern 
browsers.

As the project name suggests, this project is written using
[Vue.js](https://vuejs.org/) and at the base provides a Vue
based component - see `src/components/PhoneSimulator.vue` .

Note, this project is not associated with the Vue Team.

## Building and Running

This project uses NPM, so:


- To install the dependencies: `npm install`
- To run in development mode: `npm run dev`
- To build for production: `npm run build`
  - Build artefacts are placed in the `dist` folder


## Limitations

If certain pages don't load, then you should check the
browser's console, since in certain cases security rules
imposed by the browser and/or website may prevent the
page loading in an iframe.

## Useful References

For the dimensions of the screens:

  - https://material.io/devices/
  - https://mydevice.io/devices/

## Credits

We could create the world from scratch, but it is better to
build on top of the efforts of others, so long as we are
willing to credit them.

### The Simulator

Original author: Andre-John Mas

### Phone Templates

 - [iPhone 6](https://dribbble.com/shots/1719571-iPhone-6-Sketch-Template) by George Otsubo
 - [Google Pixel](https://dribbble.com/shots/3004465-Google-Pixel-Mockup) by Daniel Bolyhos 
